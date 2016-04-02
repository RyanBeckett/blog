---
title: "Swift: Constants And Variables"
layout: post
date: 2015-05-04 11:44:00
tag:
  - Swift
  - Programming
  - Blog
blog: true
comments: true
---

Constants and variables in Swift are simply ways in which we can store data. In Swift a 'constant' is a variable whose values cannot be changed after its been declared. On the other hand, a variable's value can be changed. Note for neither of these can you assign a new type after it's been declared. Now let's look at how we declare these.

We use the word "let" to declare a constant in Swift:

~~~~~~
  let placeOfBirth = "Belfast, Northern Ireland"
~~~~~~

For a variable we use "var":

~~~~~~
  var livingIn = "Banbridge, Northern Ireland"
  var age = 19
~~~~~~

When we declared each of these, Swift automatically defined their types based on what values we passed in when declaring them. Now, lets say we want to explicitly tell Swift what types of values we what to store. This is called 'Type Annotations'. Let's use the same examples as before to explain.

~~~~~~
  let placeOfBirth: String = "Belfast, Northern Ireland"
  var livingIn: String = "Banbridge, Northern Ireland"
  var age: Int = 19
~~~~~~

Now copy and paste the above code into a playground or [click here][SS1] to use Swift Stub. Below it try and change the value of livingIn and placeOfBirth to your age, mobile number or anything that has a number. Eg:

~~~~~~
  livingIn = 09883657496
  placeOfBirth = 14
~~~~~~

You will get an error for both. If you've been switched on, you should have known already that the constant "placeOfBirth" would not have changed as I have already told you that it's "a variable whose values cannot be changed after its been declared". So if you noticed that, then [well done][joke]!

Now you might be asking yourself, Ryan then why did we get an error for "placeOfBirth". It's not a constant, it's a variable and we know this because it begins with "var" not "let".
You are correct this is not a constant, even though we are trying to changes it's value; which we are allowed todo with a variable but we are also trying to change it's type from a 'String', to an 'Int' and this is why we are getting the error.

Hopefully this helps with constants and variables in Swift.

[SS1]:http://swiftstub.com/758337396/?v=gm
[joke]:http://treasure.diylol.com/uploads/post/image/394172/resized_jesus-says-meme-generator-10-points-for-gryffindor-caef09.jpg
