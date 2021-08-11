# Read: Hash Tables

## [Intro to Hash Tables](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)

# Hashtables
![](https://www.tutorialandexample.com/wp-content/uploads/2019/09/Hashtable-in-Java.png)
## What is a Hashtable?
- Hashtables are a data structure that utilize key value pairs.
- every Node or Bucket has both a key, and a value
- hash: is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.
- O(1) time complexity.
  * Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. 
    - In the case of a hashtable, it is used to determine the index of the array.


  * Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
  * Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.
  * Use hashtables to hold unique values, dictionary, and library.
  * Hashtables - are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value. Ability to store the key into this data structure, and quickly retrieve the value through a hash.
  * A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value. Idealy its Big O(1), and worst case O(n).
  * A hash code turns a key into an integer, and their output is determined only by their input. 
  * Hashtable traditionally is created from an array. Each index of the array can hold many types of values. Each Index of the array contain “buckets”, and each of these “buckets” holds one key/value pair combination. 
  * Collision - occurs when more than one key hashes to the same index in an array. 
  * Hash Maps can have any number of buckets. If a hash map has only a few buckets it will be densely full and have many collisions. If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.
  * Load factor - tells us something about how full the hash table is. 
  * Add() - when adding a new key/value pair to a hashtable
  * Find() - takes in a key, gets the Hash, and goes to the index location specified.
  * Contains() - will accept a key, and return a bool on if that key exists inside the hashtable.
  * GetHash() - will accept a key as a string, conduct the hash, and then return the index of the array where the key/value should be placed.

## [what is a hash table?](https://www.youtube.com/watch?v=MfhjkfocRR0)
**Introduction to hash tables**
  * Hash tables are used to store information.
  * Has two main components: a key and a value.
  * A way to implement an assiociative array.
  * Hash function will take in a key value, and as a result will give an index number.
  * The key will always match that index number, but if another key with the same index comes up, you have to make a chain off of the unit it is in.
  * Hash tables can be very large, and store many key values.

## Why do we use hashtables
- Hold unique values
- Dictionary
- Library


## [basics of hash tables](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)
**Basics of Hash Tables**
  * Hashing - is a technique that is used to uniquely identify a specific object from a group of similar objects. 
  * Large keys are converted into small keys by using hash functions. 
  * Hash function - is any function that can be used to map a data set of an arbitrary size to a data set of a fixed size, which falls into the hash table. The values returned by a hash function are called hash values, hash codes, hash sums, or simply hashes.
  * The values are then stored in a data structure called hash table. Hash table is a data structure that is used to store keys/value pairs. 
  * Hashing basic requirements:
    - Easy to compute - It should be easy to compute and must not become an algorithm in itself.
    - Uniform distribution - It should provide a uniform distribution across the hash table and should not result in clustering.
    - Less collisions - Collisions occur when pairs of elements are mapped to the same hash value. These should be avoided.
  * Separate chaining - is one of the most commonly used collision resolution techniques, and implemented using linked lists. 
  * Open addressing - all entry records are stored in the array itself. When a new entry has to be inserted, the hash index of the hashed value is computed and then the array is examined.
  * Probe sequence - is the sequence that is followed while traversing through entries. 
  * Linear probing - is when the interval between successive probes is fixed (usually to 1). 
  * Quadratic probing - is similar to linear probing and the only difference is the interval between successive probes or entry slots.
  * Associative arrays - arrays whose indices are arbitrary strings or other complicated objects.
  * Database indexing - hash tables may also be used as disk-based data structures and database indices.
  * Caches - hash tables can be used to implement caches.
  * Object representation - several dynamic languages, such as Perl, Python, JavaScript, and Ruby use hash tables to implement objects.
  * Hash Functions are used in various algorithms to make their computing faster.


## Terminology
### `Hash` 
- A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.
### `Buckets`
- A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
### `Collisions`
- A collision is what happens when more than one key gets hashed to the same location of the hashtable.
 ## `Structure`
### Hashing
- hash code turns a key into an integer.
- hash codes are deterministic.
- output is determined only by their input.
- Hash codes should never have randomness.
- The same key should always produce the same hash code.
### `Creating a Hash`
hashtable traditionally is created from an array
size 1024. this is important for index placement.
#### `suggestion for key`
- Add or multiply all the ASCII values together.
- Multiply it by a prime number such as 599.
- Use modulo to get the remainder of the result, when divided by the total size of the array.
- Insert into the array at that index.


## [hash table wiki](https://en.wikipedia.org/wiki/Hash_table)
**Hash table**
  * Hash table (hash map) is a data structure that implements an associative array abstract data type, a structure that can map keys to values. A hash table uses a hash function to compute an index, also called a hash code, into an array of buckets or slots, from which the desired value can be found. 
  * The idea of hashing is to distribute the entries (key/value pairs) across an array of buckets. Given a key, the algorithm computes an index that suggests where the entry can be found: index = f(key, array_size).
  * Done in two steps: hash = hashfunc(key)
                      index = hash % array_size
  * The function should provide a uniform distribution of hash values. 
  * Cryptographic hash functions are believed to provide good hash functions for any table size, either by modulo reduction or by bit masking.
  * Perfect hash function can be used to create a perfect hash table that has no collisions.
  * A critical statistic for a hash table is the load factor, defined as load factor = n/k. n is the number of entries occupied in the hash table, and k is the number of buckets.
  * Hash collisions are practically unavoidable when hashing a random subset of a large set of possible keys. Solutions for collisions are seperate chaining and open addressing.
  * Rehashing - includes increasing the size of the underlying data structure and mapping existing items to new bucket locations. 
  * Speed analysis - the hash function is completely unspecified and the table does not resize in the simplest model. 
  * Memory utilization - the memory requirement for a table needs to be minimized. Quotienting works readily with chaining hash tables, or with simple cuckoo hash tables. 
  * Associative arrays - arrays whose indices are arbitrary strings or other complicated objects
  * Hash tables may also be used as disk-based data structures and database indices.
  * Hash tables can be used to implement caches, auxiliary data tables that are used to speed up the access to data that is primarily stored in slower media.
  * Set data structure records whether a given key belongs to a specified set of keys.
  * A transposition table to a complex Hash Table which stores information about each section that has been searched.


### `Collisions`
- collision occurs when more than one key hashes to the same index in an array.
## Internal Methods
- `Add()`
- `Find()`
- `Contains()`
- `GetHash()`
























