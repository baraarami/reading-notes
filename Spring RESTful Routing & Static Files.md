# In this quick article
we'll focus on different kinds of Spring Data repository interfaces and their functionality. We'll touch on:

### CrudRepository
### PagingAndSortingRepository
### JpaRepository

Simply put, every repository in Spring Data extends the generic Repository interface, but beyond that, they do each have different functionality.

## Let's start with the *JpaRepository* – which extends PagingAndSortingRepository and, in turn, the CrudRepository.

Each of these defines its own functionality:

1. CrudRepository provides CRUD functions

2. PagingAndSortingRepository provides methods to do pagination and sort records

3. JpaRepository provides JPA related methods such as flushing the persistence context and delete records in a batch

And so, because of this inheritance relationship, the JpaRepository contains the full API of CrudRepository and PagingAndSortingRepository.

When we don't need the full functionality provided by JpaRepository and PagingAndSortingRepository, we can simply use the CrudRepository.



 # The CrudRepository interface:

### The typical CRUD functionality:

1. save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch

2. findOne(…) – get a single entity based on passed primary key value

3. findAll() – get an Iterable of all available entities in database

4. count() – return the count of total entities in a table

5. delete(…) – delete an entity based on the passed object

6. exists(…) – verify if an entity exists based on the passed primary key value

This interface looks quite generic and simple, but actually, it provides all basic query abstractions needed in an application.




#### Now let's talk about one of the main annotations in Spring MVC: @RequestMapping.

Simply put, the annotation is used to map web requests to Spring Controller methods.

1. @RequestMapping Basics

Let's start with a simple example: mapping an HTTP request to a method using some basic criteria.


1.1 @RequestMapping — by Path

1.2 @RequestMapping — the HTTP Method


2. RequestMapping and HTTP Headers

2.1 @RequestMapping With the headers Attribute

2.2 @RequestMapping Consumes and Produces

3. RequestMapping With Path Variables

3.1 Single @PathVariable

3.2  Multiple @PathVariable

3.3  @PathVariable With Regex

4. RequestMapping With Request Parameters

5. RequestMapping Corner Cases

5.1 @RequestMapping — Multiple Paths Mapped to the Same Controller Method

5.2 @RequestMapping — Multiple HTTP Request Methods to the Same Controller Method

5.3  @RequestMapping — a Fallback for All Requests
To implement a simple fallback for all requests using a particular HTTP meth

5.4 Ambiguous Mapping Error


6. New Request Mapping Shortcuts
Spring Framework 4.3 introduced a few new HTTP mapping annotations, all based on @RequestMapping:

### @GetMapping
### @PostMapping
### @PutMapping
### @DeleteMapping
### @PatchMapping
These new annotations can improve the readability and reduce the verbosity of the code.


7. Spring Configuration




