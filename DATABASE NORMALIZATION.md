# Introduction to Database Normalization


Database normalization is a process used to organize a database into tables and columns.  The main idea with this is that a table should be about a specific topic and only supporting topics included. Take a spreadsheet containing the information as an example, where the data contains salespeople and customers serving several purposes:

Identify salespeople in your organization
List all customers your company calls upon to sell a product
Identify which salespeople call on specific customers.
By limiting a table to one purpose you reduce the number of duplicate data contained within your database. This eliminates some issues stemming from database modifications.

To achieve these objectives, we’ll use some established rules. As you apply these rules, new tables are formed. The progression from unruly to optimized passes through several normal forms.

There are three normal forms most databases adhere to using.  As tables satisfy each successive database normalization form, they become less prone to database modification anomalies and more focused toward a sole purpose or topic. Before we move on be sure you understand the definition of a database table.


Get your Free Coupon Today

It's my best deal possible to enroll in

Database Normalization Simplified.

Name
Enter Email
GET ACCESS
Reasons for Database Normalization
There are three main reasons to normalize a database.  The first is to minimize duplicate data, the second is to minimize or avoid data modification issues, and the third is to simplify queries. 

As we go through the various states of normalization we’ll discuss how each form addresses these issues, but to start, let’s look at some data which hasn’t been normalized and discuss some potential pitfalls. 

I think once you understand the issues, you better appreciate normalization. Consider the following table:


Note: The primary key columns are underlined
The first thing to notice is this table serves many purposes including:

Identifying the organization’s salespeople
Listing the sales offices and phone numbers
Associating a salesperson with an sales office
Showing each salesperson’s customers
As a DBA this raises a red flag.  In general I like to see tables that have one purpose.  Having the table serve many purposes introduces many of the challenges; namely, data duplication, data update issues, and increased effort to query data.

Data Duplication and Modification Anomalies
Notice that for each SalesPerson we have listed both the SalesOffice and OfficeNumber. There are duplicate salesperson data. Duplicated information presents two problems:

It increases storage and decrease performance.
It becomes more difficult to maintain data changes.
For example:

Consider if we move the Chicago office to Evanston, IL. To properly reflect this in our table, we need to update the entries for all the SalesPersons currently in Chicago.  Our table is a small example, but you can see if it were larger, that potentially this could involve hundreds of updates.


These situations are modification anomalies. Database normalization fixes them. There are three modification anomalies that can occur:

Insert Anomaly
Database Normalization
There are facts we cannot record until we know information for the entire row.  In our example we cannot record a new sales office until we also know the sales person.  Why?  Because in order to create the record, we need provide a primary key.  In our case this is the EmployeeID.

Update Anomaly
Database Normalization
In this case we have the same information in several rows. For instance if the office number changes, then there are multiple updates that need to be made.  If we don’t update all rows, then inconsistencies appear.

Deletion Anomaly
Table Row Deletion Anomaly
Deletion of a row causes removal of more than one set of facts.  For instance, if John Hunt retires, then deleting that row cause us to lose information about the New York office.

Search and Sort Issues
The last reason we’ll consider is making it easier to search and sort your data.  In the SalesStaff table if you want to search for a specific customer such as Ford, you would have to write a query like

SELECT SalesOffice
FROM SalesStaff
WHERE Customer1 = ‘Ford’ OR
      Customer2 = ‘Ford’ OR
      Customer3 = ‘Ford’
Clearly if the customer were somehow in one column our query would be simpler.  Also, consider if you want to run a query and sort by customer. 

Our current table makes this tough. You would have to use three separate UNION queries! You can eliminate or reduce these anomalies by separating the data into different tables. This puts the data into tables serving a single purpose.

The process to redesign the table is database normalization.


Get your Free Coupon Today

It's my best deal possible to enroll in

Database Normalization Simplified.

Name
Enter Email
GET ACCESS
Definition of Database Normalization
There are three common forms of database normalization: 1st, 2nd, and 3rd normal form. They are also abbreviated as 1NF, 2NF, and 3NF respectively. 


There are several additional forms, such as BCNF, but I consider those advanced, and not too necessary to learn in the beginning.

The forms are progressive, meaning that to qualify for 3rd normal form a table must first satisfy the rules for 2nd normal form, and 2nd normal form must adhere to those for 1st normal form. Before we discuss the various forms and rules in detail, let’s summarize the various forms:

First Normal Form – The information is stored in a relational table with each column containing atomic values. There are no repeating groups of columns.
Second Normal Form – The table is in first normal form and all the columns depend on the table’s primary key.
Third Normal Form – the table is in second normal form and all of its columns are not transitively dependent on the primary key
If the rules don’t make too much sense, don’t worry. I’ve linked to article to help you understand them.

For now it’s important to understand there are three rules for database normalization that upon each other.  Some people make database normalization seem complicated.


but it doesn’t have to be, and once you understand it, it becomes intuitive.

More tutorials are to follow! Remember!  I want to remind you all that if you have other questions you want answered, then post a comment or tweet me.  I’m here to help you. What other topics would you like to know more about?



