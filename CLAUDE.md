# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Personal blog of Gervin Guevarra — a Jekyll site built on the **jekyll-theme-chirpy** gem (via [Chirpy Starter](https://github.com/cotes2020/chirpy-starter)), deployed to GitHub Pages. The theme is consumed as a **RubyGem**, not vendored, so there are no theme source files (`_layouts`, `_includes`, `_sass`, core JS) in this repo — only content, config, and a few overrides. To inspect theme internals, look inside the installed `jekyll-theme-chirpy` gem.

## Commands

Ruby/Bundler are **not** installed on the host — everything runs in a container (see "Running locally"). All commands below assume you're inside that container (or the dev container), at the repo root.

```sh
./tools/run.sh                 # serve with livereload at http://127.0.0.1:4000 (dev)
./tools/run.sh -H 0.0.0.0      # bind all interfaces (needed when serving from a container)
./tools/run.sh -p              # production env
./tools/test.sh                # production build + html-proofer (same checks as CI)
bundle exec jekyll b -d _site  # one-off build only
```

There is **no unit-test suite**. "Testing" == `./tools/test.sh`: a production build followed by `html-proofer` (internal links/images/scripts; external links disabled). This mirrors `.github/workflows/pages-deploy.yml`, which builds, html-proofs, and deploys on every push to `master`.

## Authoring posts

- File: `_posts/YYYY-MM-DD-slug.md`. The date prefix sets the publish date; the slug becomes the URL via the configured permalink `/posts/:title/` (e.g. `2026-01-11-the-present.md` → `/posts/the-present/`).
- Front matter follows existing posts: `title`, `date` (`YYYY-MM-DD`), `categories: [X]`, `tags: [lowercase, ...]`. Optional: `image: { path: <url> }` for the banner, `canonical_url` for cross-posts.
- Categories currently in use: `SoftwareDev`, `Life`, `Literature`. New categories need **no registration** — `jekyll-archives` generates `/categories/:name/` and `/tags/:name/` pages automatically.
- Cross-post link to another post with `{% post_url YYYY-MM-DD-slug %}` rather than a hardcoded URL.

## Architecture notes that aren't obvious from a single file

- **`_plugins/posts-lastmod-hook.rb`** shells out to `git log`/`git rev-list` at build time to set each post's `last_modified_at`. If git isn't usable in the build environment (e.g. building from a **git worktree** whose `.git` dir isn't mounted into the container), it prints `fatal: not a git repository` per post and silently skips the field. Harmless — build output is unaffected.
- **`_config.yml` `defaults`** apply `layout: post` + TOC to everything in `_posts/`, and `layout: page` to the `tabs` collection. Don't set these per-file.
- **`_tabs/`** is the `tabs` collection (sidebar nav: About, Archives, Categories, Tags), sorted by an `order` front-matter field.
- Sitemap/robots/feed are generated (`jekyll-sitemap`, `jekyll-feed`). Note both root and `assets/` define `robots.txt` and `feed.xml`, so a build prints two "destination shared by multiple files" conflict warnings — pre-existing and benign.
- `tools/` and `README.md` are in `_config.yml`'s `exclude`, so they're not published.

## Running locally

**Docker must be in Linux-container mode** (this is a Linux toolchain).

**Intended path — VS Code Dev Container** (`.devcontainer/`, image `mcr.microsoft.com/devcontainers/jekyll`): "Reopen in Container", then `./tools/run.sh`.

**If the dev container image won't pull** (corporate TLS proxy such as Netskope can block `mcr.microsoft.com` at the Docker-daemon layer with `x509: certificate signed by unknown authority` — Docker Hub images still pull fine), run against a Docker Hub Ruby image instead. `ruby:3.3-bookworm` (not `-slim`) is required — it ships the compilers that native gems like `eventmachine` (livereload) need. A named volume caches the installed gems between runs.

```sh
# One-time / on Gemfile change: install gems into a reusable volume
docker run --rm -v "$PWD:/workspace" -w /workspace \
  -v chirpy-bundle:/bundle -e BUNDLE_PATH=/bundle \
  ruby:3.3-bookworm bash -lc "bundle install"

# Serve at http://localhost:4000
docker run -d --name chirpy-serve -v "$PWD:/workspace" -w /workspace \
  -v chirpy-bundle:/bundle -e BUNDLE_PATH=/bundle \
  -p 4000:4000 -p 35729:35729 \
  ruby:3.3-bookworm bash -lc "bundle exec jekyll s -H 0.0.0.0 -P 4000 -l --force_polling"
docker rm -f chirpy-serve   # stop it

# Build + html-proofer (test)
docker run --rm -v "$PWD:/workspace" -w /workspace \
  -v chirpy-bundle:/bundle -e BUNDLE_PATH=/bundle \
  ruby:3.3-bookworm bash -lc "bundle exec jekyll b -d _site && \
    bundle exec htmlproofer _site --disable-external \
    --ignore-urls '/^http:\/\/127.0.0.1/,/^http:\/\/0.0.0.0/,/^http:\/\/localhost/'"
```

Notes:
- `--force_polling` is required for livereload to see edits on a Windows bind mount (inotify doesn't fire across the mount).
- On Windows, run these via PowerShell with a native path (`-v "C:\path\to\repo:/workspace"`); Git Bash mangles the mount path.
- `--disable-external` on html-proofer means external links (e.g. the Unsplash/source-material URLs) aren't fetched — matching CI.
