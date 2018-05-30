---
layout: post
title:      "Scope and Variables in Ruby"
date:       2018-05-30 23:05:10 +0000
permalink:  scope_and_variables_in_ruby
---


I am working towards my final projects in Learn. Each project builds upon the other to get me to a point where I can write my own code without the specific guidance of the Rspec tests provided for each lesson. It's exciting and a bit intimidating to think about the next steps of writing code without the guidance of the tests that were previously written for each lesson.

The struggle lately has been to comprehend some of the concepts behind when to use a class or an instance variable. Let's look at some of these concepts. 

#### Variables

Variables are the building blocks or containers for storing data. Variables can store and retrieve data in the code we write. Variables can hold more than one value (i.e., arrays). 

#### Local Variables

Local variables have a *scope* that is limited to the area in which they are declared. So, if the local variable is declared within a method or a loop, the scope of that variable is limited to within that method or loop. These variables can only be used in a finite part of the program, and once you exit that part of the program, these variables are destroyed.

For example, if I declare a variable called `a` and want to print the value of `a` 10 times, the code looks like:

```
    10.times do
    a = "Hello, how are you?"
    puts a
    end
```

#### Scope

What is scope? Scope is an area in your program that has available data. A local variable created outside of a method can not be used within the method (i.e., between the keywords *def* and *end*).

For example, if I try to use the variable `a` outside of the loop I will get an error of undefined local variable or method. 


```
    10.times do
    a = "Hello, how are you?"
    end

    puts a

         NameError: undefined local variable or method a' for main:Object
```


The error above occurs because `a` is a local variable whose data is available only within the loop. Outside of the loop the data is not available. The scope changed when the programmer wrote `puts a` after the keyword `end `. Since `a` is a local variable, it can only exist where it was defined, which was within the loop. 

#### Global Variables

Let's start our discussion of global variables by saying that we should never use them. Global variables are defined with a `$` preceding the variable, however, there is always a better way to code than to use a global variable. These variables are scoped to the entire application and can create confusion with other developers who may not realize that a global variable was set.

#### Constants

The values for these variables are supposed to remain fixed for the life of the program. In Ruby, they are defined by being in all upper case letters. These values can be changed, but Ruby will give a warning if this occurs.

#### Instance Variables

Instance variables are defined with an `@` symbol preceding the variable. An instance variable has a scope associated to an object within an instance of a class. This means that methods within the instance have access to any instance variable. 

For example, 

```
class Square

    def initialize(length)
      @length = length
    end

    def area
      @length * @length
    end

end
```

In the `Square` class, the `@length` instance variable was defined within the `#initialize` method and then was accessible within the `#area `method. The `@length` instance variable is then accessible from within any other method within the object.


#### Class Variables

Class variables are defined with two `@@` symbols preceding the variable. Class variables are available to a particular class that they are defined in. The scope of the class variable is to the class itself, instead of within specific instances of the class. 

Class variables are useful to store information relevant to all instances within a certain class. For example,

```
class Square

 @@length = 10
	
end

```

Because the class variable, `@@length`  is defined within the class `Square`, every square would have a length of 10 by default.

#### Summary
Variables are a building block of programming. There are several types of variables available in Ruby and it is important to know when to use each type. The exception is for a global variable, which we do not use when writing our programs.






