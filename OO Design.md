# OO Design
## SOLID principles 

![](https://devopedia.org/images/article/177/8101.1558682601.png)

# OO SOLID principles in real life

## s is for single responsibility principle

by way of counter-example, consider a class that opens a connection to the database, pulls out some table data, and writes the data to a file. this class has multiple reasons to change: adoption of a new database, modified file output format, deciding to use an orm, etc.  in terms of the srp, we'd say that this class is doing too much.

## o is for open/closed principle

- a great example of this in real life is  a smartphone. all such phones have app stores and these app stores let you extend the base functionality of the phone. the mechanism that allows you to do this is purely one of extension, however. 

## l is for liskov substitution principle


in other words, if you have a class, animal, with a makenoise() method, then any subclass of animal should reasonably implement makenoise(). cats should meow, dogs should bark, etc. what you wouldn't do is define a mutemouse class that throws idontactuallymakenoiseexception. this violates the lsp, and the argument would be that this class has no business inheriting from animal.


## i is for interface segregation principle

to picture this in the real world, think of going down to your local corner restaurant and checking out the menu. you'll see all of the normal menu mainstays, and then something that's just called "soup of the day." why do they do this? because the soup changes a lot and there's no sense reprinting the menus every day. clients that don't care about the soup needn't even be concerned, and clients that do use a different interface -- asking the server.

## d is for dependency inversion

to visualize this in your day to day, go down to your local store and pay for something with a credit card. the clerk doesn't examine your card and get out the "visa machine" after seeing that your card is a visa. he just takes your card, whatever it is, and swipes it. both you and the clerk depend on the credit card abstraction without worrying about specifics.

## [OO SOLID principles in real life](https://dzone.com/articles/the-solid-principles-in-real-life)

**SOLID principles in real life**
* S - single responsibility principle - class or module should have only one reason to change
  - Real life example - the "duck" vehicle are street legal and water-capable, and they only change from driving on land to going out on the water, and from being driven in the water to land.
* O - open/closed principle -  a class that does what it needs to flawlessly and does not need to be changed later, but can be extended.
  - Real life example - a smart phone that doesn't need to be changed itself, but you can add apps on the phone.
* L - liskov substitution principle - any child type of a parent type should be able to stand in for that parent 
  - Real life example - Cooking stew with various ingredients in the stew, while asking if the ingredients are edible or not.
* I - interface segregation principle - don't want to force clients to depend on things they don't actually need
  - Real life example - The soup of the day on a menu at a restuarant. The reason why it only says soup of the day is because it changes everyday.
* D - dependency inversion - depends upon abstractions rather than upon concrete details
  - Real life example - Using a credit card to pay groceries with, and the clerk swiping your credit card with a visa machine.



