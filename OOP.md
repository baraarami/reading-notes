# Object-Oriented Programming Concepts


### What Is an Object?

are key to understanding object-oriented technology , Real-world objects share two characteristics: They all have state and behavior.


Software objects are conceptually similar to real-world objects: they too consist of state and related behavior. An object stores its state in fields (variables in some programming languages) and exposes its behavior through methods (functions in some programming languages).


# Bundling code into individual software objects provides a number of benefits, including:

** Modularity: The source code for an object can be written and maintained independently of the source code for other objects. Once created, an object can be easily passed around inside the system.
** Information-hiding: By interacting only with an object's methods, the details of its internal implementation remain hidden from the outside world.
** Code re-use: If an object already exists (perhaps written by another software developer), you can use that object in your program. This allows specialists to implement/test/debug complex, task-specific objects, which you can then trust to run in your own code.
** Pluggability and debugging ease: If a particular object turns out to be problematic, you can simply remove it from your application and plug in a different object as its replacement. This is analogous to fixing mechanical problems in the real world. If a bolt breaks, you replace it, not the entire machine.


A class declaration names the class and encloses the class body between braces. The class name can be preceded by modifiers. The class body contains fields, methods, and constructors for the class. A class uses fields to contain state information and uses methods to implement behavior. Constructors that initialize a new instance of a class use the name of the class and look like methods without a return type.

You control access to classes and members in the same way: by using an access modifier such as public in their declaration.



# Decimals 
How do Decimal Numbers work? 
Every digit in a decimal number has a "position", and the decimal point helps us to know which position is which:

![sdf](https://user-images.githubusercontent.com/79080942/123831848-69eeec00-d90d-11eb-8516-335b20ff3566.PNG)

The Decimal Number System is also called "Base 10", because it is based on the number 10, with these 10 symbols:

0, 1, 2, 3, 4, 5, 6, 7, 8 and 9


# Binary Numbers
Binary Numbers are just "Base 2" instead of "Base 10". So you start counting at 0, then 1, then you run out of digits ... so you start back at 0 again, but increase the number on the left by 1. 


# Hexadecimal Numbers
Hexadecimal numbers are interesting. There are 16 of them!

They look the same as the decimal numbers up to 9, but then there are the letters ("A',"B","C","D","E","F") in place of the decimal numbers 10 to 15.

So a single Hexadecimal digit can show 16 different values instead of the normal 10 like this:

| Decimal: |	0 |	1 |	2 |	3 |	4 |	5 |	6 |	7 |	8 |	9 |	10 |	11 |	12 |	13 |	14 |	15 |
| Hexadecimal: |	0 |	1 |	2 |	3 |	4 |	5 |	6 |	7 |	8 |	9 |	A |	B |	C |	D |	E |	F |


