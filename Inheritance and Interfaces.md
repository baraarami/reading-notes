# Inheritance and Interfaces


# Inheritance :

It's Provides powerlful and natural mechanism for organizing and structuring your software 
this section explains how classes inherent state and behavior from thier superclasses ,
and explaines how classes state and behavior from their superclasses , and explains how to derive 
one class from another using the simple syntax provided by the java .


# what is Inheritance ?
Different kinds of objects often have a certain amount in common with each other.


coted paragraphe """"""""""""""'


The syntax for creating a subclass is simple. At the beginning of your class declaration, use the extends keyword, followed by the name of the class to inherit from:

class MountainBike extends Bicycle {

    // new fields and methods defining 
    // a mountain bike would go here

}
This gives MountainBike all the same fields and methods as Bicycle, yet allows its code to focus exclusively on the features that make it unique. This makes code for your subclasses easy to read. However, you must take care to properly document the state and behavior that each superclass defines, since that code will not appear in the source file of each subclass.
""""""""""""""""""""""""""





# Interface

It's contract between a class and the outside world . when a class implement an interface
it promises to provide the behavior published by the interface . this section defines a 
simple interface and explain the necessary changes for any class that implements it .


# what is an Interface ?
Objects define their interaction with the outside world through the methods that they expose.
methode from the object's interface with the outside world , the buttons on the front of your
television set , for example , are the interface between you and the electrical wiring on 
the other side of its plastic casing .


coted paragraphe """"""""""""""'


Implementing an interface allows a class to become more formal about the behavior it promises to provide. Interfaces
form a contract between the class and the outside world, and this contract is enforced at build time by the compiler. 
If your class claims to implement an interface, all methods defined by that interface must appear in its source code before the class will successfully compile.

""""""""""""""""""""""""""""""

