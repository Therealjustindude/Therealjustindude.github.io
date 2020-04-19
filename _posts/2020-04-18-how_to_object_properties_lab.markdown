---
layout: post
title:      "How to: Object Properties Lab"
date:       2020-04-19 01:57:21 +0000
permalink:  how_to_object_properties_lab
---


I am going to walk you through how to solve the Meowing cat lab in object Properties. In this lab we are asked to 1) Practice defining a class 2) Use macros to create setter and getter methods. With that, we will need to create a Cat class where every instance of Cat has a name.  We want to make a method called #meow so that an instance of the Cat class can meow. 

```
class Cat
  attr_accessor :name
end
```

With the Cat class created along with the macro attr_accessor for name we can set and get name attributes for instances of the Cat class. For example we can do something like this: 
```
maru = Cat.new
maru.name = "Maru"

maru.name
# => "Maru"
```

You can see there that we have a new instance of the cat class and that instance has a name equal to “Maru.”

But, if we run learn in the terminal we see this failure:

```
Failures:
  1) Cat is able to meow
     Failure/Error: maru.meow
     NoMethodError:
       undefined method `meow' for #<Cat:0x0000000002812b60>
```

This is telling us we haven’t created a #meow method.

We want to be able to do something like: maru.meow and get back “meow!” in the terminal. So we will add that instance method into our Cat class. Like this:

```
class Cat
  attr_accessor :name
  def meow
    puts "meow!"
  end
end
```

If we run learn now all our tests are passing.

```
Cat
  instantiates a new cat
  receives attr_accessor
  has a name
  is able to meow

4 examples, 0 failures
```
