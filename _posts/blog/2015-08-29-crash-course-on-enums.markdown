---
layout: post
title: "Java: Crash Course on Enums"
date: 2015-08-29 21:30:00
author: Ryan Beckett
categories:
  - Java
  - Programming
  - Blog
img: javab.jpg
thumb: java.jpg
---


Firstly, we need to discuss what is an enum? Enums provide a convenient way of dealing with sets of values as a list. It acts similarly to a constant class, but it hasn't got the same restrictions that classes do, but we'll cover that later. Let's first look at how to create an enum

<!--more-->


### Constructing an Enum
As an example, I'll be using the four cardinal points.

~~~~~~
public enum Directions {}
~~~~~~

Secondly, we need to populate the enum with information.

~~~~~~
public enum Directions {
    NORTH,
    EAST,
    SOUTH,
    WEST
}
~~~~~~

Note, Java naming conventions state than an enum should have all caps with underscores separating words.

Just like any other class, you use a constructor to define what information an instance needs. With an enum, however, the constructor must be private. This is because enums contain a fixed set of values, which must all be known at compile-time. It doesn't make sense to create new literals at run-time, which would be possible if the constructor were visible (public).

Now the constructor is defined and the information is given.

~~~~~~
public enum Directions {
    NORTH('N'),
    EAST('E'),
    SOUTH('S'),
    WEST('W');

    private final Char letterCode;

}
~~~~~~

Now, there must be a way to access the information. Just like any other class, we add a field and a getter method.

~~~~~~
public enum Directions {
    NORTH('N'),
    EAST('E'),
    SOUTH('S'),
    WEST('W');

    private final Char letterCode;

    Directions(Char code) {
      this.letterCode = code;
    }

    public Char getDirection() {
      return this.letterCode;
    }
}
~~~~~~


And that's the enum complete.


### Using the enum

~~~~~~
public class EnumExample {
    public static void main(String[] args) {
    	Directions dir = Directions.NORTH;
    	System.out.println(dir.getDirection());

    	dir = Directions.WEST;
    	System.out.println(dir2.getDirection());
    }
}
~~~~~~


#### Output:

~~~~~~
N
W
~~~~~~

### Enum vs Constant Class

Technically enums could be seen as a class with typed constants but by using an enum instead of a  class gives you useful methods that you would otherwise have to implement yourself. You also have the ability to use them in switch statements and Enum classes are also type-safe, whereas static fields aren't. I'm sure there are even more advantages. Feel free to comment them below.


Hopefully this helps with the confusion regarding enums.
