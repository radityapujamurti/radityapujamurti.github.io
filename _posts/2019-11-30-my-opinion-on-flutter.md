---
layout: post
title: My Opinion on Flutter
tags: others
cover: 
excerpt: I find Flutter intuitive and easy to learn. It is great for creating mobile app prototype.
---

## Summary
I find Flutter intuitive and easy to learn. It is great for creating mobile app prototype. However, do more research about it before using Flutter for production.

*Before you continue: this article is intended to give general idea about Flutter and help anyone who are deciding whether to learn it or not. It is not a detailed tutorial on how to build app using Flutter.*

## Why I Chose Flutter
> Flutter - Beautiful native apps in record time

Flutter allows us to build mobile application once and deploy it in both Android and iOS. There are other more established alternatives such as React Native. I became interested in Flutter after knowing it uses a programming language that I never learned before: Dart.

Dart feels similar to Java. As to why Flutter uses Dart over other programming languages, here is an [article](https://hackernoon.com/why-flutter-uses-dart-dd635a054ebf) for it.

The most apparent advantage for me is the ability for Dart to hot-reload, thanks to its Just In Time (JIT) compilation nature. You don’t have to wait for a long time just to see the effect of changing size/colour of a small part of a widget in your application.

![](https://media2.giphy.com/media/11ISwbgCxEzMyY/giphy.gif?cid=790b7611b5cb983065238f358a6573bcdde0417877425c86&rid=giphy.gif&ct=g)

Awesome!

## First Impression
In my spare time, I really enjoyed learning Flutter. Documentation is great and I did not face significant obstacle to get my prototype up and running. Development is a breeze, mostly due to hot-reload feature as mentioned above.

The concept of widgets in Flutter is intuitive for me. In a widget, we embed another widget as its child then you can embed another widget in that child widget and so on. Also, we can reuse a widget in other parts of our code. So build once and use everywhere!

However, it can also be cumbersome when there are too many embedded widgets in a single .dart file. A better practice is to separate these widgets into separate files. This will cause another issue. As the number of widgets file increase, finding the right widget files can be a challenge. Therefore, it is crucial to name and organize our widget files properly.

## File Organization
This brings me to my next point.

To make it easier in organizing my Dart files, I like to organize it into the following folders:

- Models — a single truth definition of how our data should look like, similar to a schema in database
- Screens — widgets that are used to display the whole screen that includes app bar (usually with ‘scaffold’ widget)
- Widgets — widgets that are used as part of another widgets or screens
- Providers — for provider related logic (explained in the next section)
The list above can increase depending on our own specific needs such as adding ‘Helpers’ folder to store helper functions. One example is location picker function to enable users to select a location on a Google Map plugin.

Organizing our files will greatly improve our experience with Flutter. So please take some time to think about it to prevent pain and confusion in the end.

## Providers
In the previous section, I mentioned a special folder for Providers.

To put it simply, Provider is used to supply necessary data or methods for certain widgets to use.

But why do we need provider?

Without provider, we usually pass around the data we need between screens/widgets thorough the constructors when we call that widget.

For example, in screen A has a button with ‘onPressed’ method to navigate to screen B. In screen B, we only need e.g. ‘item_id’ and ‘item_name’ data which are obtained from screen A. Then, we create another screen C that needs ‘item_id’, ‘item_name’ and ‘item_description’ from screen B. In this case, we need to change the properties in screen B to require ‘item_description’. It is so that screen A can pass ‘item_description’ to screen B and then screen B pass it to screen C even though screen B does not require ‘item_description’ at all.

![](https://media0.giphy.com/media/eChf44Gyj2VrO/giphy.gif?cid=790b76113888817ebed8f78508ee0241907a6cbb3a24b4b5&rid=giphy.gif&ct=g)

This is redundant and can quickly become a complex situation.

Here Flutter Providers come to the rescue. From the example above, it is possible for screen C to get all the data it needs directly from a method used that is defined in a Dart file inside the ‘Providers’ folder.

We can learn more about Provider [here](https://pub.dev/packages/provider).

## Final Thoughts
I really enjoy my learning journey with Flutter. It has a great potential to become the next established framework for mobile app development (or it already is). However, always remember to do more thorough research if you want to use it for production as there might still be rough edges that need further fixes.

Good luck, have fun!