# Read: 29 - Room

## [Overview: Saving data with Room](https://developer.android.com/training/data-storage/room)

![](https://gorillalogic.com/wp-content/uploads/2019/12/RoomDB_Transparent.png)
## Save data in a local database using Room 
- WHAT is Room?
  - Room is an `ORM` (object relational mapper) for `SQLite` database in Android. It is part of the Architecture Components released by Google.
- WHY we use Room ?
  - Room allows you to:
    - create and manipulate database in Android more quickly.
    -  See it as an abstraction layer on top of inbuilt SQLite database.
- JUSTIFY: " its highly recommend that you use `Room` instead of using the `SQLite APIs` directly." 
  - because Room provides the following benefits:
    - Compile-time verification of SQL queries.
    - Convenience annotations that minimize repetitive and error-prone boilerplate code.
    - Streamlined database migration paths.

**Save data in a local database using Room**
  * Room persistence library provides an abstraction layer over SQLite to allow fluent database access while harnessing the full power of SQLite. 
  * Room provides the following benefits - compile-time verification of SQL queries, convenience annotations that minimize repetitive and error-prone boilerplate code, and streamlined database migration paths.
  * Setup - add these depencies: 
  dependencies {
  def room_version = "2.2.6"

  implementation "androidx.room:room-runtime:$room_version"
  annotationProcessor "androidx.room:room-compiler:$room_version"

  // optional - RxJava2 support for Room
  implementation "androidx.room:room-rxjava2:$room_version"

  // optional - RxJava3 support for Room
  implementation "androidx.room:room-rxjava3:$room_version"

  // optional - Guava support for Room, including Optional and ListenableFuture
  implementation "androidx.room:room-guava:$room_version"

  // optional - Test helpers
  testImplementation "androidx.room:room-testing:$room_version"
}

* Primary components:
  - The database class that holds the database and serves as the main access point for the underlying connection to your app's persisted data.
  - Data entities that represent tables in your app's database.
  - Data access objects (DAOs) that provide methods that your app can use to query, update, insert, and delete data in the database.
* AppDatabase defines the database configuration and serves as the app's main access point to the persisted data. The database class must satisfy the following conditions:
  - The class must be annotated with a @Database annotation that includes an entities array that lists all of the data entities associated with the database.
  - The class must be an abstract class that extends RoomDatabase.
  - For each DAO class that is associated with the database, the database class must define an abstract method that has zero arguments and returns an instance of the DAO class.

## [Defining entities in Room](https://developer.android.com/training/data-storage/room/defining-data)
**Defining data using Room entities**
  * When you use the Room persistence library to store your app's data, you define entities to represent the objects that you want to store. Each entity corresponds to a table in the associated Room database, and each instance of an entity represents a row of data in the corresponding table.
  * Anatomy of an entity
    - Each Room entity can be defined as a class that is annotated with @Entity. A Room entity includes fields for each column in the corresponding table in the database, including one or more columns that comprise the primary key.
    - Room uses the class name as the database table name.
  * Define a primary key
    - Each Room entity must define a primary key that uniquely identifies each row in the corresponding database table. The most straightforward way of doing this is to annotate a single column with @PrimaryKey.
    - If you need instances of an entity to be uniquely identified by a combination of multiple columns, you can define a composite primary key by listing those columns in the primaryKeys property of @Entity.
  * Ignore fields
    - If an entity has fields that you don't want to persist, you can annotate them using @Ignore, and can use ignoredColumns for an entity inherits fields from a parent entity.
  * Provide table search support
    - Room supports several types of annotations that make it easier for you to search for details in your database's tables.
    - Support full-text search - add the @Fts3 or @Fts4 annotation to a given entity
    - Index specific columns - to add indices to an entity, include the indices property within the @Entity annotation, listing the names of the columns that you want to include in the index or composite index.
  * Include AutoValue-based objects 
    -  In Room 2.1.0 and higher, use Java-based immutable value classes, which you annotate using @AutoValue, as entities in your app's database. This support is particularly helpful when two instances of an entity are considered to be equal if their columns contain identical values. 
    - With @AutoValue as entities, you can annotate the class's abstract methods using @PrimaryKey, @ColumnInfo, @Embedded, and @Relation. When using these annotations, however,include the @CopyAnnotations annotation each time so that Room can interpret the methods' auto-generated implementations properly.

 ### HOW To use Room in your app ?
   1. Setup :
      - add the dependencies to your app's `build.gradle file` as written in this sample code>> [check the code](https://developer.android.com/training/data-storage/room#setup)
   2. Implement a Room database :
      - Follow [this example implementation](https://developer.android.com/training/data-storage/room#sample-implementation) of a Room database with a single data entity and a single DAO.
        - Define Data entity :  Each instance of class represents a row in the creatted table in the app's database.
        - Define Data access object (DAO) : which provides the methods that the rest of the app uses to interact with data in the creatted table.
        - Define Database : defines an AppDatabase class to hold the database.
        - Usage : write a code to create an instance of the database.
  #
  ## Defining data using Room entities
- ***EXPLAIN :*** that we CAN use Room entities to define a database schema without writing any SQL code ?
  - >> by useing the Room persistence library to store your app's data
  - >> you define entities to represent the objects that you want to store. 
  - >> and each entity corresponds to a table in the associated Room database, and each instance of an entity represents a row of data in the corresponding table.
  ## Anatomy of an entity
  #### Here is some example code of it :
  - Example of a simple entity :
 ```
 @Entity
public class User {
    @PrimaryKey
    public int id;

    public String firstName;
    public String lastName;
}
 ```
 - Example demonstrates custom names for tables and columns :
 ```
 @Entity(tableName = "users")
public class User {
    @PrimaryKey
    public int id;

    @ColumnInfo(name = "first_name")
    public String firstName;

    @ColumnInfo(name = "last_name")
    public String lastName;
}
 ```
 #### Define a primary key
  - The most straightforward way of doing this is to annotate a single column with `@PrimaryKey`:
```
 @PrimaryKey
 public int id;
```
#### Define a composite primary key :
 - you can define a composite primary key by listing those columns in the `primaryKeys` property of `@Entity` AS:
 `@Entity(primaryKeys = {"firstName", "lastName"})`
 #### Ignore fields
 - If an entity has fields that you don't want to persist, you can annotate them using `@Ignore`
 #### Provide table search support : check this [code](https://developer.android.com/training/data-storage/room/defining-data#search)
 #### Index specific columns : check this [code](https://developer.android.com/training/data-storage/room/defining-data#column-indexing)
 ### Include AutoValue-based objects: check this [code](https://developer.android.com/training/data-storage/room/defining-data#autovalue)
 #
 ## Accessing data using Room DAOs
 ### Insert 
 - allows you to define methods that insert their parameters into the appropriate table in the database
 ```
  @Insert(onConflict = OnConflictStrategy.REPLACE)
    public void insertUsers(User... users);

    @Insert
    public void insertBothUsers(User user1, User user2);
 ```
 ### Update
 - allows you to define methods that update specific rows in a database table
 ```
    @Update
    public void updateUsers(User... users);
 ```
 ### Delete
 - allows you to define methods that delete specific rows from a database table.
```
 @Delete
    public void deleteUsers(User... users);
```

## [Accessing data with Room](https://developer.android.com/training/data-storage/room/accessing-data#java)
**Accessing data using Room DAOs**
  * Data access objects(DOA) - Each DAO includes methods that offer abstract access to your app's database. At compile time, Room automatically generates implementations of the DAOs that you define.
  * Can define each DAO as either an interface or an abstract class.
  * Annotate your DAOs with @Dao
  * Convenience methods - that let you insert, update, and delete rows in your database without writing any SQL code.
  * Query methods - that let you write your own SQL query to interact with the database.
  * @Insert annotation - allows you to define methods that insert their parameters into the appropriate table in the database. 
  * @Update annotation - allows you to define methods that update specific rows in a database table.
  * @Delete annotation - allows you to define methods that delete specific rows from a database table.
  * @Query annotation - allows you to write SQL statements and expose them as DAO methods. 
  * DAOs can return PagingSource objects for use with Paging 3.
  * Can write your DAO methods to return a Cursor object. 
