---
title: How to Think in Object-Oriented Way 
date: 2021-08-07
image:
  path: https://media2.dev.to/dynamic/image/width=1000,height=420,fit=cover,gravity=auto,format=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Frdrj6joom8v4dltf18zw.jpg
canonical_url: https://dev.to/gervg/how-to-think-in-object-oriented-way-29a2
categories: [SoftwareDev]
tags: [object-oriented-programming, java, tutorials]
---

## Who is this for?

If you are any of the following:

- Someone who already has a decent understanding of any structured programming language. The examples are written in Java but it should be easy to follow as long as you already have a programming background
- Someone who is struggling to understand OOP
- Someone who didn’t study their entire semester and now wants to do a crash course (kidding)
- Or just curious about what this 3 letter acronym is

…then this guide is for you.

Otherwise, you might still get a thing or two here. Maybe this serves a good refresher. Perhaps, you’d notice some mistakes as well, in which case please let me know and I’ll be more than happy to make the correction and credit you :)

## Things I won’t cover

This is not meant to be a comprehensive guide on OOP. There are already hundreds of books and videos for that. Instead, this is a primer for those who are just starting to get their feet wet with OOP. I will try my best to limit the jargon and terminologies to avoid bogging you down, or else I’ll be defeating the very purpose of this guide.

As such, I won’t be discussing things here like the **4 pillars of OOP, GoF design patterns, SOLID**, or other software development principles rooted in OOP. Some of these topics will be (sneakily) touched upon as it is impossible not to do so, but I won’t go into detail to avoid information overload.

With that out of the way, let’s jump right into it.

---

## What the heck is OOP?

**OOP** stands for **O**bject-**O**riented **P**rogramming, sometimes referred to as **OO** when used as an adjective. As the name suggests, it is an approach wherein you model parts of your code as if they are individual objects with specific characteristics, states, or behaviors.

> *✅ OOP is all about thinking and modeling your code like it’s an actual real-world object*
>

You can think of your program as an actual piece of hardware with individual components that when combined together works as a single unit. Each component would have their own characteristics, their own behavior, and their own state at a given time.

A good analogy is a desktop computer. Within the system unit, it contains many parts each with their own responsibility (i.e. memory/disk for storage, CPU for all the processing needs, etc.). Then you’ll also have peripherals like keyboard, mouse, or display devices, which serve as your bridge to the external world - accepting inputs or giving outputs.

Your program, in a way, can also be modeled like that. It can be divided into multiple logical parts then combine them together. If you’ve modeled it properly, you can should also be able to easily swap out same type of parts but with probably different characteristics like how you can switch out a graphics card for another that has better specs and performs differently.

## Concepts and Uses

### 1. Categorization

One of the first things that you’ll learn in programming is the data type or simply *type*. You’ve probably already encountered this when declaring or assigning variables like so

```java
int age = 20;
```

What this basically does is that it tells your computer that the data you are storing is of type *integer*, denoted by `int` keyword, and should be treated as such. Its *category* is an integer and not a floating-point number, boolean, nor a string, etc.

In OOP, you have the power to create your own *type.* In most OO languages, this comes in the form of a `class`. To demonstrate, let’s have a simple `Box`

```java
class Box {
    //fields here
}
```

There can be many types of box:

- shoe box
- jewelry box
- music box
- mail box

to name a few.

These are all wildly different but they all fit our basic idea of what a box should be: some sort of an enclosure to store something.

![Assorted Boxes](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1na2kruf45avng4qqse1.jpg)
_Assorted Boxes. Image by [Chuttersnap](https://unsplash.com/@chuttersnap) on [Unsplash](https://unsplash.com/photos/7eQlPra81zQ)_


If we were to play a [Bring Me game](http://rosietheclown.ca/parties/?p=116) and I say “bring me a box”, I can accept any of those boxes we’ve mentioned.

```java
void accept(Box box) {    //any box will be accepted
	//do some action here
}
```

But if I said “bring me a lunch box”, then I won’t accept a shoe box or any other kind of box.

```java
class LunchBox extends Box {
	//fields here
}
```

```java
void accept(LunchBox lunchBox) {    //will only accept a LunchBox
	//do some action here
}
```

This gives us the option to be either very specific or more generic depending on our expectations or use-cases.

### 2. Blueprints and Construction

When houses or buildings are made, they don’t just magically appear out of thin air (duh). It starts with a careful plan detailing its structure and contents - the blueprint. The blueprint then becomes the basis when the construction begins.

![Blueprint being drawn](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7m9kdax60ea65rjknrfq.jpg)
_Blueprint. Image by [Damon McCullough](https://unsplash.com/@d_mccullough) on [Unsplash](https://unsplash.com/photos/HtBlQdxfG9k)_

In OOP, it’s the same. You start with a `class` that defines how your object is going to behave and look like.

```java
class House {
    int floors;
    int doors;
    String color;
    //other characteristics here
}
```

This is your object’s blueprint but it doesn’t necessarily mean that your object already exists. That’s why you need to instantiate or create it using the *constructor.* Think of your constructors as the actual workers and heavy machinery that helps build your brand new house.

```java
House aBrandNewHouse = new House();
```

> 💡 **What is a constructor?**
> In class-based OOP languages, a constructor is the a special method of a class whose sole purpose is to create an *object instance* for that class.
>
> By default, every class has a `public` (accessible by anyone) no-args constructor. You can change that by having an explicit `private` constructor but that’s already beyond the scope of this guide.
>

This is neat because you have the ability to create multiple independent instances. If you need to, you may change one `House` without affecting the other. But even then, they are still considered to houses because that is their type.

```java
House aBrandNewHouse = new House();
aBrandNewHouse.color = "red"; //A red house

House anotherBrandNewHouse = new House();
anotherBrandNewHouse.color = "blue"; //A blue house
```

### 3. Grouping of Data

![Pizza in a box](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n7x3bejhg4o3aoevzd8u.jpg)
_Pizza in a box. Image by [Lukas Bee](https://unsplash.com/@lukasbee)_

Suppose we want to create an app for a pizza shop. One may write `Pizza` as follows:

```java
class Pizza {
    String[] toppings;
    String size;
    int slices;
    BigDecimal price;
}
```

This is not necessarily wrong. But going back to our earlier definition, OOP is about modelling our code like it’s a real-world object. If you think about it, `price` isn’t part of an actual pizza. Otherwise, we’ll being eating pizzas with price tag.

Instead, we can have a separate class that can contain that information. And in doing so, we can even add more details that’s not part of the pizza itself!

```java
class PizzaOrder {
    Pizza pizza;
    BigDecimal price;
    ServingType servingType;    //enum - DineIn, Delivery, or TakeOut
}
```

In the future, if we needed to change `Pizza` , say we wanted to offer different kinds of `Crust`, we can do so without affecting `PizzaOrder`.

```java
class Pizza {
    String[] toppings;
    Crust crust;
    String size;
    int slices;
}
```

Whenever you write classes, ask which goes with which. Remember that the members (e.g. fields, methods, etc.) in a class should have *high cohesion* - meaning they should be closely related and should be part of the enclosing class. In this example, we created a new `PizzaOrder` which can group the information in a more sensible way.

### 4. Segregation of Responsibility

A physical system like a machine would usually be composed of different parts each with their own purpose. Let’s take for example a car.

For the purposes of this discussion, we’re going to oversimplify the parts of a car, namely:

- Engine - provides power
- Wheels - translates that engine power to a rolling motion
- Brakes - slows down the car
- Steering - points the car to a certain direction

With just this basic parts, maybe our car would look something like this:

![First automobile](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/z7atjfsu41skhm8a46qi.png)
_he first automobile. I don’t even know if this thing has brakes. Source: [Mercedez-Benz Group](https://group.mercedes-benz.com/company/tradition/company-history/1885-1886.html)_

Notice how each of the parts have their distinct purpose? So instead of just dumping every behavior in a single class called `Car` , we can opt to a separate each part into their own classes and assemble together later.

```jsx
class Engine {
    void generatePower() {
        // some implementation here
    }
}
```

```jsx
class Wheels {
    void roll() {
        //some implementation here
    }
}
```

```jsx
class Brakes {
    void reduceSpeed() {
        //some implementation
    }
}
```

```jsx
class Steering {
    void steer(Direction direction) {
        //some implementation
    }
}
```

```jsx
class Car {
    Engine engine;
    Wheels wheels;
    Brakes brakes;
    Steering steering;

    //constructor here
}
```

This seems to be a lot of code. But why do we have to do this?
Much like in the real world, software components can be swapped out for something else that has a more desired characteristic or behavior.

Suppose we wanted to have a faster car and we’d want to swap the engine. We can easily do so by giving the car a different engine.

```jsx
class SuperPowerfulEngine extends Engine {
    // some fields here
}
```

```jsx
// in some other class, we instantiate a Car

SuperPowerfulEngine engine = new SuperPowerfulEngine();
Wheels wheels = new Wheels();
Brakes brakes = new Brakes();
Steering steering = new Steering();

//then we give our super powerful engine to our car
Car car = new Car(engine, wheels, brakes, steering);
```

Imagine our modern day cars if the parts are not distinct from the car itself and could not be replaced, shall we buy an entire car every time something breaks?

### 5. Boundaries or Layers

Now we know how we can categorize things, group relevant information together, and separate responsibilities, we can take it up a notch and create divisions **between two distinct parts so they become independent of each other.

Take a look at your phone. See that hole below? That’s your charging port, right? That’s also where you plug the cable in case you want to make file transfers to and from your computer.

If you’re using an Android phone, then that’s a USB-C port you’re looking at. If you have an iPhone, then that’s a Lightning port.

USB-C and Lightning are types of interfaces. They allow you to connect different things to your phone as long as they follow the form factor. You can think of that form factor as the *contract* between your phone and whatever cable or device you’re connecting to it.

In OOP, we do this with… guess what? An *interface*.

```jsx
interface UsbCPort {
    void charge();
    void transferFile();
}
```

```jsx
interface LightningPort {
    void charge();
    void transferFile();
}
```

```jsx
class AndroidPhone {
    UsbCPort port;

    //some methods here
}
```

```jsx
class IPhone {
    LightningPort port;

    //some methods here
}
```

Remember the *Bring Me Example* earlier? This is exactly the same except that the we’re looking at interfaces instead of classes. What this tells us is that an Android phone wouldn’t care whatever you connect to its port, may it be a charger or a computer, as long as it fits the contract - a USB-C. The same is true for iPhone but with Lightning.

The port creates a physical boundary between the phone and the external device. And this allows us to easily swap out the device we’re connecting to it.

> **Agnostic and loose coupling**
> 
> The phone port is a good demonstration of how components should be *agnostic* and *loosely coupled* to one another.
Agnostic refers to a component being ignorant of the thing being plugged to it as long as it fits certain characteristics. In this case, the phone can handle either charging or file transfer as long as you use the designated connector for its port.
Loosely coupled means you can attach or detach something from a component and the component can still act independently without the other. When you disconnect your charger from your phone, your phone still functions normally (as long as you have battery of course!)
In significantly large projects, software components are designed to be loosely coupled so they can be easier to modify, fix, or test in isolation. One example is the database access. With interfaces, we can connect our application to a different database i.e. an in-memory database which only stores data temporarily. This can serve as a fake database where we can conduct our tests safely instead of connecting directly to a real persistent one.
{: .prompt-tip}

---

## Notes and Further Reading

- Alan Kay, who coined the term object-oriented, said that the real big idea in OOP is messaging rather than objects. I dare not question his authority on the proper definition of OOP. But I also think that there is value to what it has become and how it is being used today even though it may have deviated from the original intent. If you want to read more about Alan Kay’s clarifications on OOP, check these out:
    - [Alan Kay On Messaging (c2.com)](http://wiki.c2.com/?AlanKayOnMessaging)
    - [Dr. Alan Kay on the Meaning of "Object-Oriented Programming" (fu-berlin.de)](http://userpage.fu-berlin.de/~ram/pub/pub_jf47ht81Ht/doc_kay_oop_en)
- While writing about using types to categorize things, I couldn’t help but remember the existence of *category theory*. While OOP may have its roots in mathematics, I did not mean *category* in that sense. I won’t dare use that in my explanation since I don’t have sufficient knowledge for it. I simply felt that *category* may be an easier word than *type* but I failed to consider that it might imply another thing. But in case you want to read more, you may check out *Category Theory for Programmers* by Bartosz Mileweski. It’s on my reading list as well. Here’s a free copy:
    - https://github.com/hmemcpy/milewski-ctfp-pdf
- Earlier I mentioned “GoF Design Patterns”. This refers to the the book *Design Patterns: Elements of Reusable Object-Oriented Software* written by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides aka the Gang of Four (GoF). It’s considered a classic among OO programmers. Here’s a summary I frequent to whenever I need a refresher:
    - https://github.com/kamranahmedse/design-patterns-for-humans
- SOLID is a set of design principles which helps you write elegant and maintainable code. It is formally introduced by Robert Martin aka Uncle Bob, the author of *Clean Code* book - also a classic. Personally, I only appreciated OOP after I learned SOLID. That may or may not be the case for you but SOLID is still an indispensable knowledge. There are a lot of great resources about this topic but here’s one that I found straight from the man himself:
    - [Getting a SOLID start. - Clean Coder](https://sites.google.com/site/unclebobconsultingllc/getting-a-solid-start)
- The examples written here are in Java, a class-based OOP language. But there is another kind which is the prototype-based OOP e.g. used by Javascript.
    - [Prototype-based programming - MDN Web Docs Glossary](https://developer.mozilla.org/en-US/docs/Glossary/Prototype-based_programming)

---

## Credits

- Cover photo by [Robin Glauser](https://unsplash.com/@nahakiole) on [Unsplash](https://unsplash.com/photos/zP7X_B86xOg?utm_source=63921&utm_medium=referral)
