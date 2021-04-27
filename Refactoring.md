What is functional programming?
Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data — Wikipedia
Pure functions

“water drop” by Mohan Murugesan on Unsplash
The first fundamental concept we learn when we want to understand functional programming is pure functions. But what does that really mean? What makes a function pure?
So how do we know if a function is pure or not? Here is a very strict definition of purity:
It returns the same result if given the same arguments (it is also referred as deterministic)
It does not cause any observable side effects
It returns the same result if given the same arguments
Imagine we want to implement a function that calculates the area of a circle. An impure function would receive radius as the parameter, and then calculate radius * radius * PI:

Why is this an impure function? Simply because it uses a global object that was not passed as a parameter to the function.
Now imagine some mathematicians argue that the PI value is actually 42and change the value of the global object.
Our impure function will now result in 10 * 10 * 42 = 4200. For the same parameter (radius = 10), we have a different result. Let's fix it!

TA-DA 🎉! Now we’ll always pass thePI value as a parameter to the function. So now we are just accessing parameters passed to the function. No external object.
For the parameters radius = 10 & PI = 3.14, we will always have the same the result: 314.0
For the parameters radius = 10 & PI = 42, we will always have the same the result: 4200
Reading Files
If our function reads external files, it’s not a pure function — the file’s contents can change.

Random number generation
Any function that relies on a random number generator cannot be pure.

It does not cause any observable side effects
Examples of observable side effects include modifying a global object or a parameter passed by reference.
Now we want to implement a function to receive an integer value and return the value increased by 1.

We have the counter value. Our impure function receives that value and re-assigns the counter with the value increased by 1.
Observation: mutability is discouraged in functional programming.
We are modifying the global object. But how would we make it pure? Just return the value increased by 1. Simple as that.

See that our pure function increaseCounter returns 2, but the counter value is still the same. The function returns the incremented value without altering the value of the variable.
If we follow these two simple rules, it gets easier to understand our programs. Now every function is isolated and unable to impact other parts of our system.
Pure functions are stable, consistent, and predictable. Given the same parameters, pure functions will always return the same result. We don’t need to think of situations when the same parameter has different results — because it will never happen.
Pure functions benefits
The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:
Given a parameter A → expect the function to return value B
Given a parameter C → expect the function to return value D
A simple example would be a function to receive a collection of numbers and expect it to increment each element of this collection.

We receive the numbers array, use map incrementing each number, and return a new list of incremented numbers.

For the input [1, 2, 3, 4, 5], the expected output would be [2, 3, 4, 5, 6].
Immutability
Unchanging over time or unable to be changed.

“Change neon light signage” by Ross Findon on Unsplash
When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.
In Javascript we commonly use the for loop. This next for statement has some mutable variables.

For each iteration, we are changing the i and the sumOfValue state. But how do we handle mutability in iteration? Recursion!

So here we have the sum function that receives a vector of numerical values. The function calls itself until we get the list empty (our recursion base case). For each "iteration" we will add the value to the total accumulator.
With recursion, we keep our variables immutable. The list and the accumulator variables are not changed. It keeps the same value.
Observation: Yes! We can use reduce to implement this function. We will cover this in the Higher Order Functions topic.
It is also very common to build up the final state of an object. Imagine we have a string, and we want to transform this string into a url slug.
In OOP in Ruby, we would create a class, let’s say, UrlSlugify. And this class will have a slugify! method to transform the string input into a url slug.

Beautiful! It’s implemented! Here we have imperative programming saying exactly what we want to do in each slugify process — first lower case, then remove useless white spaces and, finally, replace remaining white spaces with hyphens.
But we are mutating the input state in this process.
We can handle this mutation by doing function composition, or function chaining. In other words, the result of a function will be used as an input for the next function, without modifying the original input string.

Here we have:
toLowerCase: converts the string to all lower case
trim: removes whitespace from both ends of a string
split and join: replaces all instances of match with replacement in a given string
We combine all these 4 functions and we can "slugify" our string.
Referential transparency


Let’s implement a square function:

This pure function will always have the same output, given the same input.

Passing 2 as a parameter of the square function will always returns 4. So now we can replace the square(2) with 4. That's it! Our function is referentially transparent.
Basically, if a function consistently yields the same result for the same input, it is referentially transparent.
pure functions + immutable data = referential transparency
With this concept, a cool thing we can do is to memoize the function. Imagine we have this function:

And we call it with these parameters:

The sum(5, 8) equals 13. This function will always result in 13. So we can do this:

And this expression will always result in 16. We can replace the entire expression with a numerical constant and memoize it.
Functions as first-class entities

“first-class” by Andrew Neel on Unsplash
The idea of functions as first-class entities is that functions are also treated as values and used as data.
Functions as first-class entities can:
refer to it from constants and variables
pass it as a parameter to other functions
return it as result from other functions
The idea is to treat functions as values and pass functions like data. This way we can combine different functions to create new functions with new behavior.
Imagine we have a function that sums two values and then doubles the value. Something like this:

Now a function that subtracts values and the returns the double:

These functions have similar logic, but the difference is the operators functions. If we can treat functions as values and pass these as arguments, we can build a function that receives the operator function and use it inside our function. Let’s build it!

Done! Now we have an f argument, and use it to process a and b. We passed the sum and subtraction functions to compose with the doubleOperator function and create a new behavior.
Higher-order functions
When we talk about higher-order functions, we mean a function that either:
takes one or more functions as arguments, or
returns a function as its result
The doubleOperator function we implemented above is a higher-order function because it takes an operator function as an argument and uses it.
You’ve probably already heard about filter, map, and reduce. Let's take a look at these.
Filter
Given a collection, we want to filter by an attribute. The filter function expects a true or false value to determine if the element should or should not be included in the result collection. Basically, if the callback expression is true, the filter function will include the element in the result collection. Otherwise, it will not.
A simple example is when we have a collection of integers and we want only the even numbers.
Imperative approach
An imperative way to do it with Javascript is to:
create an empty array evenNumbers
iterate over the numbers array
push the even numbers to the evenNumbers array

We can also use the filter higher order function to receive the even function, and return a list of even numbers:

One interesting problem I solved on Hacker Rank FP Path was the Filter Array problem. The problem idea is to filter a given array of integers and output only those values that are less than a specified value X.
An imperative Javascript solution to this problem is something like:

We say exactly what our function needs to do — iterate over the collection, compare the collection current item with x, and push this element to the resultArray if it pass the condition.
Declarative approach
But we want a more declarative way to solve this problem, and using the filter higher order function as well.
A declarative Javascript solution would be something like this:

Using this in the smaller function seems a bit strange in the first place, but is easy to understand.
this will be the second parameter in the filter function. In this case, 3 (the x) is represented by this. That's it.
We can also do this with maps. Imagine we have a map of people with their name and age.

And we want to filter only people over a specified value of age, in this example people who are more than 21 years old.

Summary of code:
we have a list of people (with name and age).
we have a function olderThan21. In this case, for each person in people array, we want to access the age and see if it is older than 21.
we filter all people based on this function.
Map
The idea of map is to transform a collection.
The map method transforms a collection by applying a function to all of its elements and building a new collection from the returned values.
Let’s get the same people collection above. We don't want to filter by “over age” now. We just want a list of strings, something like TK is 26 years old. So the final string might be :name is :age years old where :name and :age are attributes from each element in the people collection.
In a imperative Javascript way, it would be:

In a declarative Javascript way, it would be:

The whole idea is to transform a given array into a new array.
Another interesting Hacker Rank problem was the update list problem. We just want to update the values of a given array with their absolute values.
For example, the input [1, 2, 3, -4, 5]needs the output to be [1, 2, 3, 4, 5]. The absolute value of -4 is 4.
A simple solution would be an in-place update for each collection value.

We use the Math.abs function to transform the value into its absolute value, and do the in-place update.
This is not a functional way to implement this solution.
First, we learned about immutability. We know how immutability is important to make our functions more consistent and predictable. The idea is to build a new collection with all absolute values.
Second, why not use map here to "transform" all data?
My first idea was to test the Math.abs function to handle only one value.

We want to transform each value into a positive value (the absolute value).
Now that we know how to do absolute for one value, we can use this function to pass as an argument to the map function. Do you remember that a higher order function can receive a function as an argument and use it? Yes, map can do it!

Wow. So beautiful! 😍
Reduce
The idea of reduce is to receive a function and a collection, and return a value created by combining the items.
A common example people talk about is to get the total amount of an order. Imagine you were at a shopping website. You’ve added Product 1, Product 2, Product 3, and Product 4 to your shopping cart (order). Now we want to calculate the total amount of the shopping cart.
In imperative way, we would iterate the order list and sum each product amount to the total amount.

Using reduce, we can build a function to handle the amount sum and pass it as an argument to the reduce function.

Here we have shoppingCart, the function sumAmount that receives the current currentTotalAmount , and the order object to sum them.
The getTotalAmount function is used to reduce the shoppingCart by using the sumAmount and starting from 0.
Another way to get the total amount is to compose map and reduce. What do I mean by that? We can use map to transform the shoppingCart into a collection of amount values, and then just use the reduce function with sumAmount function.

The getAmount receives the product object and returns only the amount value. So what we have here is [10, 30, 20, 60]. And then the reduce combines all items by adding up. Beautiful!
We took a look at how each higher order function works. I want to show you an example of how we can compose all three functions in a simple example.
Talking about shopping cart, imagine we have this list of products in our order:

We want the total amount of all books in our shopping cart. Simple as that. The algorithm?
filter by book type
transform the shopping cart into a collection of amount using map
combine all items by adding them up with reduce

Done! 🎉



# Refactoring JavaScript for Performance and Readability (with Examples!)





We're going to refactor some pieces of code based off real examples that I've come across. Sometimes I'll need to perform this kind of refactoring on my own code before submitting a PR. Other times I'll do a small refactor of existing code at the start of a story or bug to make my changes easier to implement.

Scenario 1
We're an URL-shortening website, like TinyURL. We accept a long URL and return a short URL that forwards visitors to the long URL. We have two functions.
// Unrefactored code

const URLstore = [];

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  URLstore.push({[rndName]: URL});
  return rndName;
}

function getLong(shortURL) {
  for (let i = 0; i < URLstore.length; i++) {
    if (URLstore[i].hasOwnProperty(shortURL) !== false) {
      return URLstore[i][shortURL];
    }
  }
}
Problem: what happens if getLong is called with a short URL that isn't in the store? Nothing is explicitly returned so undefined will be returned. Since we're not sure how we're going to handle that, let's be explicit and throw an error so that problems can be spotted during development.

Performance-wise, be careful if you're iterating through a flat array very often, especially if it's a core piece of your program. The refactor here is to change the data-structure of URLstore.

Currently, each URL object is stored in an array. We'll visualize this as a row of buckets. When we want to convert short to long, on average we need to check half of those buckets before we find the correct short URL. What if we have thousands of buckets, and we perform this hundreds of times a second?

The answer is to use some form of hash function, which Maps and Sets use under the surface. A hash function is used to map a given key to a location in the hash table. Below, this happens when we place our short URL into the store in makeShort and when we get it back out in getLong. Depending on how you're measuring run time, the result is that on average we only need to check one bucket — no matter how many total buckets there are!
// Refactored code

const URLstore = new Map(); // Change this to a Map

function makeShort(URL) {
  const rndName = Math.random().toString(36).substring(2);
  // Place the short URL into the Map as the key with the long URL as the value
  URLstore.set(rndName, URL);
  return rndName;
}

function getLong(shortURL) {
  // Leave the function early to avoid an unnecessary else statement
  if (URLstore.has(shortURL) === false) {
    throw 'Not in URLstore!';
  }
  return URLstore.get(shortURL); // Get the long URL out of the Map
}
For those examples, we assumed that the random function wouldn't clash. 'Cloning TinyURL' is a common system design question and a very interesting one at that. What if the random function does clash? It's easy to tack on addendums about scaling and redundancy.

Scenario 2
We're a social media website where user URLs are generated randomly. Instead of random gibberish, we're going to use the friendly-words package that the Glitch team works on. They use this to generate the random names for your recently created projects!
// Unrefactored code

const friendlyWords = require('friendly-words');

function randomPredicate() {
  const choice = Math.floor(Math.random() * friendlyWords.predicates.length);
  return friendlyWords.predicates[choice];
}

function randomObject() {
  const choice = Math.floor(Math.random() * friendlyWords.objects.length);
  return friendlyWords.objects[choice];
}

async function createUser(email) {
  const user = { email: email };
  user.url = randomPredicate() + randomObject() + randomObject();
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
It's often said that a function should do one thing. Here, createUser does one thing .. kinda. It creates a user. However, if we're thinking ahead to the future, there's a good chance (if our business is successful) that this function is going to grow very large indeed. So let's start early by breaking it up.

You may have also noticed that there is some duplicated logic in our random functions. The friendly-worlds package also offers lists for 'teams' and 'collections'. We can't go around writing functions for every option. Let's write one function that accepts a list of friendly things.
// Refactored code

const friendlyWords = require('friendly-words');

const generateURL = user => {
  const pick = arr => arr[Math.floor(Math.random() * arr.length)];
  user.url = `${pick(friendlyWords.predicates)}-${pick(friendlyWords.objects)}` +
    `-${pick(friendlyWords.objects)}`; // This line would've been too long for linters!
};

async function createUser(email) {
  const user = { email: email };
  // The URL-creation algorithm isn't important to this function so let's abstract it away
  generateURL(user);
  await db.insert(user, 'Users')
  sendWelcomeEmail(user);
}
We separated some logic and reduced the number of lines of code. We inlined a function called pick that accepts an array of length 1 and up and returns a random choice, then we used a template literal to build an URL.

Strategies
Here are some straightforward to implement methods that can lead to easier to read code. There are no absolutes when it comes to clean code — there's always an edge case!

Return early from functions:
function showProfile(user) {
  if (user.authenticated === true) {
    // ..
  }
}

// Refactor into ->

function showProfile(user) {
  // People often inline such checks
  if (user.authenticated === false) { return; }
  // Stay at the function indentation level, plus less brackets
}
Cache variables so functions can be read like sentences:
function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    for (let j = 0; j < continents[i].length; j++) {
      for (let k = 0; k < continents[i][j].tags.length; k++) {
        if (continents[i][j].tags[k] === name) {
          return continents[i][j].id;
        }
      }
    }
  }
}

// Refactor into ->

function searchGroups(name) {
  for (let i = 0; i < continents.length; i++) {
    const group = continents[i]; // This code becomes self-documenting
    for (let j = 0; j < group.length; j++) {
      const tags = group[j].tags;
      for (let k = 0; k < tags.length; k++) {
        if (tags[k] === name) {
          return group[j].id; // The core of this nasty loop is clearer to read
        }
      }
    }
  }
}
Check for Web APIs before implementing your own functionality:
function cacheBust(url) {
  return url.includes('?') === true ?
    `${url}&time=${Date.now()}` :
    `${url}?time=${Date.now()}`
}

// Refactor into ->

function cacheBust(url) {
  // This throws an error on invalid URL which stops undefined behaviour
  const urlObj = new URL(url);
  urlObj.searchParams.append('time', Date.now); // Easier to skim read
  return url.toString();
}
It's important to get your code right the first time because in many businesses there isn't much value in refactoring. Or at least, it's hard to convince stakeholders that eventually uncared for codebases will grind productivity to a halt.
