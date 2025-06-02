---
title: Step by Step Introduction to Unit Testing in Java
date: 2021-04-10
canonical_url: https://dev.to/gervg/step-by-step-introduction-to-unit-testing-in-java-3ae7
categories: [SoftwareDev]
tags: [unit-testing, java, tutorials]
---

## Introduction

Hey folks! So I kinda promised to someone I forgot who that I'll write a unit testing guide for this [group](https://www.facebook.com/groups/649943542157470?_rdc=1&_rdr). There must be hundreds of similar guides out there in the wild, but I feel like most of those I've seen are too short and doesn't really explain the rationale behind unit testing. I think unit testing is one of the most underrated skill that a programmer should learn and sadly it isn't taught in schools (in our country, at least). So here's my take on a (hopefully) gentle introduction to the world of automated testing.

Anyway, enough with my babbling. Let's get right into it.

## Naive way of testing code

When we first started learning programming, what we'd normally do is write code, run the program. Then conduct tests by entering some inputs hoping that the output is as we desired. If not, we go back writing our code again and fixing bugs.

Well, there's nothing wrong with that. In fact, for your entire life as a programmer you'd be doing all these three things:

1) **write** code

2) **run** the program

3) **test** the behavior of your program

Then repeat again

But you won't always be writing simple console applications. Sooner or later, you'll find yourself doing repetitive tests with slightly varying inputs.

In the real world where you'd be dealing with much much bigger and more complex software, doing those three things every time will be **very time consuming**. There will also be cases where you need to isolate your changes and just **test a specific part** rather than the whole system.

## What is Unit testing?

So instead of running and testing your entire program every time you have to a change in your code, we can automate it by **writing code to test our code**. More specifically, write code that would test a single part of the system isolated from everything else. That's unit testing.

### An analogy

For example, you are building a house and you need some light bulbs. So you go to the store and buy a light bulb. In order to make sure that the light bulb you just bought works, you need to test it.

But the good thing about it is that it's independent of your house. You can test it by itself. No need to actually install it in your house and see if it lights up. Instead, you or the sales assistant can install it to a test bulb socket (found in most hardware or appliance stores) and see if it lights up. You are essentially **testing** a single **unit** of a light bulb which is meant to be part of your house (i.e. the entire system) under construction.

Imagine if it wasn't possible to test the light bulb alone. You have to go back to your house first, finish building it, install the light bulbs and test if it actually switches on. Quite a hassle, isn't it?

## Getting your feet wet

### Prerequisites

Before taking this guide, be sure that you are already familiar with Java language as I will not be going through the detail of compiling and running your Java program. Also be sure to have an internet connection as we will be downloading some tools, and libraries. This guide also assumes that you have an existing project where you want to add unit testing. If not, you can just copy-paste the Java files below and follow along.

It's also worth noting that the guide, for now, is also written to suit MacOS or Linux users. But experienced Windows users may also want to try anyway (and let me know where it gets difficult! I'll make updates on this guide where necessary).

Below is short list of everything you need:

- **Java 8** or higher (I'm using Java 8. But to follow this guide, it doesn't matter if you're using a newer version)
- Favorite **Code editor or IDE** (I use IntelliJ IDEA myself, but you're free to use whatever you want)
- **Gradle** build tool (download and follow the guide [here](https://gradle.org/install/))
    - in case you are already using Gradle, you may want to skip to [this step and just add JUnit to your dependencies](#setting-up-the-testing-framework)
- Command Line (Shell or Command Prompt)
    - we'll be doing things from scratch, so having familiarity working in terminal is a great plus
    - this also makes this guide IDE-agnostic, meaning you don't have to be very dependent on a specific IDE just to make this work
    - if you're on Windows, you may opt to use WSL or the bash prompt that comes with Git (if you are already using one).

### A sample existing code

Say we have an existing console application which accepts input of any length from the user and then our program outputs the reverse of the input. Classic problem.

So we can implement this by writing the following:

```java
package com.gerv.guev;

import java.util.Scanner;

public class ConsoleApplication {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String input = scanner.nextLine();

        MyStringUtilities stringUtilities = new MyStringUtilities();
        String reversedString = stringUtilities.reverse(input);

        System.out.println("The reverse is: " + reversedString);
    }
}
```
{: file="ConsoleApplication.java" }

```java
package com.gerv.guev;

public class MyStringUtilities {
    public String reverse(String input) {

        char[] reversedCharSequence = new char[input.length()];
        int index = input.length() - 1;

        for(char letter : input.toCharArray()) {
            reversedCharSequence[index] = letter;
        }

        return String.valueOf(reversedCharSequence);
    }
}
```
{: file="MyStringUtilities.java" }

You might notice a "bug" here. That's intentional. We'll delve into that later

![File structure 1](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/if9sag99945nq0la5pi3.png)

At this point, your project structure should look similar to this. It's alright if you don't have the  *.idea* folder or the **.iml* file. Those are just IntelliJ IDEA generated files.

### Setting up the testing framework

The testing framework that we're gonna use is **[JUnit](https://junit.org/junit4/).** To add it in our project, we need a *dependency manager* such as Gradle.

> **Dependency Manager**
> 
> The great thing about OOP is that it allows us to reuse somebody else's code. Those reusable pieces of code often mature enough that they can be standalone libraries or frameworks. They then get redistributed by various means, either by downloading the JAR files, as in the case of Java, or getting the source code and building it by yourself. These libraries or frameworks become the *dependencies* of your project. Some of these libraries/frameworks have dependencies of their own, so you also have to take care of them and add them to your project.
>
> But doing so multiple times over the duration of your project can be time-consuming, entails difficulties, and is a very repetitive processes. This is where dependency manager comes in.
>
> A **dependency manager** is a tool that helps you download libraries and/or frameworks, as well as their dependencies, to add to your project; while also keeping track of the version you are using for each. Some examples of popular dependency managers for Java projects are **Gradle** and **Maven** (which also functions as build tools).
>
> For further reading about dependency managers and what they can do, check out [this article](https://medium.com/prodsters/what-are-dependency-managers-26d7d907deb8) by Seun Matt in Medium
{: .prompt-tip }

If you have prepared the [prerequisites](#prerequisites) listed earlier, you should have Gradle already installed in your system. To check, enter the following in your terminal and it should output a directory where you installed Gradle.

```terminal
$ which gradle
```

Next, we need to turn our existing console application project into a Gradle project. Expand each step by clicking the drop-down then follow the instructions

- Go to your project directory

    In my case, my project is saved in `Users/gerv/Source/HelloUnitTesting`.  I can use `~` as short hand for my User home directory.

    ```terminal
    $ cd ~/Source/HelloUnitTesting
    ```

- Initialize a Gradle project

    Simple enter the following command and follow the on-screen instructions to setup gradle for your project

    ```terminal
    $ gradle init
    ```

    If you're confused, you can just follow the screenshot below.
    ![Gradle init output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tmc5th1thg62gq2qx3cj.png)

    You might notice that my shell prompt is different. That's because I'm using zsh with oh-my-zsh, but that's a topic for another day. For now, think of that fancy arrow as the `$` sign you normally see.

- Run your first Gradle build

    ```terminal
    $ gradle build
    ```

    Then you should see an output similar to this:
    ![Gradle build output](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/56g7yqfcq02u295fwdfj.png)

You might notice that there are a bunch of files added to your project folder. These are files that are generated by `gradle init` and will be used by Gradle when building your project. You may happily ignore them for now, but I want to quickly introduce you to one of them, the `build.gradle` file. This is the file that contains the list of your dependencies and repositories (from which your dependencies will be downloaded). Take a quick look at it and notice that JUnit is already added; this because we picked JUnit earlier when we ran `gradle init` .

```java
//Snippet of build.gradle

dependencies {
    // Use JUnit test framework
    testImplementation 'junit:junit:4.12'
}
```
{: file="build.gradle" }


You may also notice that `main` and `test` folders are added to the project. We will use them to reorganize our code.

### Separating source code and test code

Gradle isn't smart enough to know that you already have existing code in your project, and assumes that you are starting a Gradle project from scratch. So it creates its own folders, package, the class named `App.java` with the `main()` method.

After running `gradle init` , your project directory should look like this.
![File structure after gradle init](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mi16gb61bwdwg0txi115.png)

But we already have [ConsoleApplication.java](#a-sample-existing-code) and that serves as the main entry point of our application so we can just get rid of `App.java`. We also don't need the package `HelloUnitTesting` since we already have an existing one from before. Delete them as you normally would, or if you're like me and you like doing everything in terminal

```terminal
$ rm -r src/main/java/HelloUnitTesting
```

```terminal
$ rm -r src/test/java/HelloUnitTesting
```

<figure>
  <img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/cs66g1h560qctdwjtvkn.png">
  <figcaption>Project directory after deleting some files</figcaption>
</figure>

Then we need to reorganize our code and put them inside the `main/java/` folder. To do this, you can either drag the `com.gerv.guev` (or whatever your existing package name is) to `main/java/` or do it via terminal again

```terminal
$ mv src/com src/main/java/com
```

If you're also using IntelliJ IDEA, you might notice that `main/java` is marked like a package even though it isn't. To make them appear like normal folders, simply right click on the `src` then point to *Mark Directory As* and pick *Unmark as Sources Root*. Then right click on `java` folder under `main` then *Mark Directory As* and pick *Sources Root.* Do the same thing with the `java` folder under `test`, but pick *Test Sources Root*. For the `resources` folder, mark them as *Resources Root* and *Test Resources Root* for `main` and `test` respectively.

If you've carefully followed the instructions, your project directory should now look something like this:

![File structure after setting up Gradle](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6ouc7hj2jat8l5bh4fr0.png)

To quickly check if everything still works, run this and it should tell you "Build Successful". You may also want to try and run your program if it still works as before.

```terminal
$ gradle build
```

If your gradle build is successful but your IDE is complaining (i.e. squiggly red lines, you can just reimport/reopen your project and hopefully your IDE recognizes that it's now a Gradle project.

**Quick Recap!**
That's a lot of things we've already covered. Here's what we've done so far:
- turn our project into a Gradle project
- add JUnit to our dependencies
- Reorganize our project folders

### Writing your first unit test

Now that we have finished setting up our project and its dependencies, we are now ready to write our unit test!

Under the `test/java` folder, create a package `com.gerv.guev` or whatever package name you already used in your project. Then create a file named `MyStringUtilitiesTest.java`. You may copy the contents of the class for now, I'll explain what it does along the way.

```java
package com.gerv.guev;

public class MyStringUtilitiesTest {
    //Empty class
}
```
{: file="MyStringUtilitiesTest.java" }

Then we are going to add a test method that actually does nothing. We're taking very small steps to make sure we're not making mistakes and everything is still working as it is.

```java
package com.gerv.guev;

import org.junit.Test;

public class MyStringUtilitiesTest {
    @Test
    public void someUselessTest() {
        assert true;
    }
}
```
{: file="MyStringUtilitiesTest.java" }

In the code above, `@Test` is an annotation that tells our compiler that the method that we just wrote is a **test method**. `@Test` annotation is located under the `org.junit` package (notice the `import` statement above).

A method marked as a **test method** will be checked by the test runner if it satisfies some conditions we are expecting. In this case, the test should always pass because we told it to `assert true` which will always be true no matter what. The point of writing this the first time is to check if our unit testing framework was really set up correctly. After you've written one or if you're already familiar with the testing framework your are using, there's no need to write this one every time.

To run the test, type in this command

```terminal
$ gradle test --tests="com.gerv.guev.MyStringUtilitiesTest.someUselessTest"
```

In the command above, we are telling Gradle to run the test found in a fully qualified name. In this case we're telling it to specifically run `someUselessTest()` test method.

A **fully qualified name** consists of the package name, class name, and method name. It represents the hierarchical location of your file or folder and should always be unique.

But if you have multiple tests inside a class or package, you can just replace it with an asterisk (*) and it should still run
```terminal
$ gradle test --tests="com.gerv.guev.MyStringUtilitiesTest.*"
```

### Running the test and using the results to debug

Now, let's replace that useless test with a real one to test our earlier [code](#a-sample-existing-code) for reversing a string.


```java
package com.gerv.guev;

import org.junit.Assert;
import org.junit.Test;

public class MyStringUtilitiesTest {
    @Test
    public void shouldReturn_ReverseString() {
        MyStringUtilities stringUtilities = new MyStringUtilities();

        String actualResult = stringUtilities.reverse("hello");
        String expectedResult = "olleh";

        Assert.assertEquals(expectedResult, actualResult);
    }
}
```
{: file="MyStringUtilitiesTest.java" }

Go ahead and run the test using the command mentioned earlier, and you should see an error similar to this

```terminal
> Task :test FAILED

com.gerv.guev.MyStringUtilitiesTest > shouldReturn_ReverseString FAILED
    org.junit.ComparisonFailure at MyStringUtilitiesTest.java:14

1 test completed, 1 failed

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':test'.
> There were failing tests. See the report at: file:///Users/gerv/Source/HelloUnitTesting/build/reports/tests/test/index.html

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 1s
3 actionable tasks: 1 executed, 2 up-to-date
```

This tells us that our test failed. Gradle has a pretty neat way of telling this to us and generates an HTML report. Copy that file path and open it using your browser.

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/070wb3e4wcjqcw6bn0b6.png)

From here it says: `org.junit.ComparisonFailure: expected:<[olleh]> but was:<[????o]>` on the first line of the stack trace. It tells us many things:

1. our input string was not reversed hence it is not equal to our expected output *"olleh"*
2. the actual result does not contain the correct characters or is probably empty. Instead, it's displaying multiple question marks.
3. The actual output has the same length as our expected output. It has 5 characters.
4. The last character "o" is still the last character in the actual output

**Don't fear the stack trace!**
Most beginners find the error messages in the stack trace intimidating, but it's actually quite easy to decipher. All you have to do is to read the first line to have a general idea of what caused the failure. If you still don't know at first glance what the error was, skim through the lines and look for your package and class ****then check the line number.

In our example, it says:
`org.junit.ComparisonFailure: expected:<[olleh]> but was:<[????o]>`

then I skip lines until I see a familiar package name:
`at com.gerv.guev.MyStringUtilitiesTest.shouldReturn_ReverseString(MyStringUtilitiesTest.java:14)`

That tells us that there was a `ComparisonFailure` at line 14 of our `MyStringUtilitiesTest` class.

Given those findings, we can check back our code to see what was wrong. Here's the current code now with comments. Can you spot what's wrong?

```java
package com.gerv.guev;

public class MyStringUtilities {
    public String reverse(String input) {

        char[] reversedCharSequence = new char[input.length()];
        int index = input.length() - 1; //take the last index of the string

        //transfer each letter to new char array
        for(char letter : input.toCharArray()) {
            reversedCharSequence[index] = letter; 
        }

        return String.valueOf(reversedCharSequence);
    }
}
```
{: file="MyStringUtilities.java" }

From our original code, what we did is we took each letter of the input from left to right then transferring it to the new character array from right to left **but we did not move the index.** To fix this, we have to decrement the index for it to move from right to left.

```java
package com.gerv.guev;

public class MyStringUtilities {
    public String reverse(String input) {

        char[] reversedCharSequence = new char[input.length()];
        int index = input.length() - 1; //take the last index of the string

        //transfer each letter to new char array
        for(char letter : input.toCharArray()) {
            reversedCharSequence[index] = letter; 
            index--;
        }

        return String.valueOf(reversedCharSequence);
    }
}
```
{: file="MyStringUtilities.java" }

Now run your test again and it should give that sweet success

```terminal
gradle test --tests="com.gerv.guev.MyStringUtilitiesTest.*"

BUILD SUCCESSFUL in 1s
3 actionable tasks: 2 executed, 1 up-to-date
```

Suppose we are going to add features in our string utilities class, like detection of palindrome

```java
package com.gerv.guev;

public class MyStringUtilities {
    
    public boolean isPalindrome(String input) {
        return input.equals(reverse(input));
    }
    
    public String reverse(String input) {

        char[] reversedCharSequence = new char[input.length()];
        int index = input.length() - 1;

        for(char letter : input.toCharArray()) {
            reversedCharSequence[index] = letter;
            index--;
        }

        return String.valueOf(reversedCharSequence);
    }
}
```
{: file="MyStringUtilitiesTest.java" }

Then all we have to do is to write another unit test and run all of them. The beauty of unit tests is that you'll always have a proof that your older features are still working even after adding new ones. And there's no need to run your console application every time just to do a manual test.


```java
package com.gerv.guev;

import org.junit.Assert;
import org.junit.Test;

public class MyStringUtilitiesTest {

    @Test
    public void shouldReturn_ReverseString() {
        MyStringUtilities stringUtilities = new MyStringUtilities();

        String actualResult = stringUtilities.reverse("hello");
        String expectedResult = "olleh";

        Assert.assertEquals(expectedResult, actualResult);
    }

    @Test
    public void shouldReturnTrue_ForPalindromes() {
        MyStringUtilities stringUtilities = new MyStringUtilities();

        boolean actualResult = stringUtilities.isPalindrome("racecar");
        Assert.assertTrue(actualResult);
    }

    @Test
    public void shouldReturnFalse_ForNotPalindromes() {
        MyStringUtilities stringUtilities = new MyStringUtilities();

        boolean actualResult = stringUtilities.isPalindrome("hello");
        Assert.assertFalse(actualResult);
    }
}
```
{: file="MyStringUtilitiesTest.java" }

You may continue adding other tests, say a different input word or maybe an entirely different test, then run it as usual. I am leaving that as an exercise for you.

## Final notes

We've barely scratched the surface of unit testing and there's a lot more to it than just testing inputs and outputs. We haven't even discussed yet its best practices but that's enough for now. I hope that you get the rough idea of how to use unit testing to your advantage.

## Relevant Articles

- Parasoft has a quick guide on setting up JUnit and it even teaches how to use it without build tools like Gradle or Maven. Go check it out [here](https://www.parasoft.com/junit-tutorial-setting-up-writing-and-running-java-unit-tests/)
- There are other excellent testing frameworks available for Java such as [TestNG](https://testng.org/doc/) and [Spock](http://spockframework.org/spock/docs/1.3/index.html). I personally prefer Spock over JUnit because of some features and syntactic sugars. The caveat is it's written using [Groovy](https://groovy-lang.org/) which is a dynamically-typed language. It might be hard for beginners to quickly grasp it on top of understanding unit-testing.
- For .NET users, there's [XUnit](https://xunit.net/) as the de facto testing framework for .NET applications. It's (arguably) the successor of the older [NUnit](https://nunit.org/). For other languages, just try appending the first few letters of what ever language you're using then "-Unit". For example, JSUnit, PhpUnit, PyUnit, etc.
- Some software development techniques such as [Test-Driven Development (TDD)](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530) and Behavior-Driven Development (BDD) are anchored in the mastery of unit testing. These techniques will help you consciously develop features while also maintaining robustness of your system over time.
- If you're an intermediate or advanced programmer, I strongly recommend that you read Martin Fowler's articles on [Unit Testing](https://martinfowler.com/bliki/UnitTest.html#:~:text=I%20think%20that%20the%20term,that%20unit%20is%20working%20correctly), other [levels of testing](https://martinfowler.com/articles/practical-test-pyramid.html#UnitTests) and the concept of [self-testing code](https://martinfowler.com/bliki/SelfTestingCode.html)
- Unit testing can also help you abstract away the layers of your application by using Test Doubles. You can read another Fowler's article [here](https://martinfowler.com/bliki/TestDouble.html) or the equally comprehensive [blog](https://docs.microsoft.com/en-us/archive/msdn-magazine/2007/september/unit-testing-exploring-the-continuum-of-test-doubles) of Mark Seeman at Microsoft.
