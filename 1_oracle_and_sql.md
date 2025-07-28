## 1. Oracle and SQL

**SQL** - Structured Query Language.  
**ERD** - Entity Relationship Diagram. It is a visual tool primarily used for database design and data modeling, illustrating how different entities relate to each other within a system. ERDs are helping to plan, design, and document complex database systems. Here we can see several types of relationship between entities:

| Name          | Crow's foot notation | Definition                         |
| ------------- |:--------------------:| ---------------------------------- |
| zero          | [A] --o- [B]         | A can "have" zero B's              |
| one           | [A] --\|- [B]        | A can "have" one B's               |
| many          | [A] ---< [B]         | A can "have" many B's              |
| zero-to-many  | [A] --o< [B]         | A can "have" from zero to many B's |
| one-to-many   | [A] --\|< [B]        | A can "have" from one to many B's  |
| zero-to-one   | [A] --o\|- [B]       | A can "have" from zero to one B's  |

But in the real world, we can see many-to-many relationships, like `[A] >--< [B]`. Therefore we cannot build this relationship in a table representation. Instead, in the database system, we do `[A] >--[A_B]--< [B]`. We can complete it by using foreign keys. So, `A_B` will have records for each relationship between `A` and `B`.

**PRIMARY KEY** is a unique identifier for a row in a particular table.  
**FOREIGN KEY** is a copy of some (or all) of one table’s PRIMARY KEY data in a second table so that the second table can relate to the first.

### Levels of Normalization
* **1NF** - no repeated groups, all tables are two-dimentional
* **2NF** - 1NF ∪ each data item have unique primary key, which is not a composite one and cannot be divided into smaller bits of data
* **3NF** - 2NF ∪ the data stored in the table relates only to table's subject; other data is stored in separate tables  

(Levels BCNF and 4-5NF are not a subject of the exam)  

### Database and SQL
A Database is a "physical" representation of a business system. SQL - a declarative programming language used to retrieve and manipulate data stored in a database and create and manipulate database structure (like table creation).  

The following are several types of SQL statements. (Session Control Statements, System Control Statements, Embedded SQL Statements are not a part of the exam.)

### DDL (Data Definition Language)
DDL is used to build database objects. It can create, edit, or drop tables, add comments, issue privileges to users, and initiate performance analysis on objects by built-in tools.
* `CREATE` - creates db objects (like tables)
* `ALTER`  - used on an existing object to change its structure, name, or other attributes.
* `DROP` - removes a db object, which was created by a `CREATE` statement
* `RENAME` - changes the name of an existing  db object 
* `TRUNCATE` - removes all records in an existing table and itn't have a recovery option like `DELETE` has
* `GRANT` - provides priviliges to users
* `REVOKE` - removes priviliges
* `FLASHBACK` - restores an earlier version of a table or database
* `PURGE` - removes database objects from the recycle bin for good.
* `COMMENT` - adds a comment for the data dictionary


### DML (Data Manipulation Language)
DML is used to work with data inside db objects. It used to add, modify, view, and delete data from the table(s).
* `SELECT` - displays data from a table or view
* `INSERT` - adds data to a table
* `UPDATE` - modifies existing data in the table
* `DELETE` - removes the data from a table
* `MERGE` - performs a combination of INSERT, UPDATE, and DELETE statements in a single statement


### TCL (Transaction Control Language)
TCL is used to manage transactions within a database.
* `COMMIT` - saves a set of DML modifications performed in the current database session
* `ROLLBACK` - undoes a set of DML modifications performed during the current database session
* `SAVEPOINT` - marks a position in a session to prepare for a future ROLLBACK


### Building a `SELECT` Statement

```
SELECT <columns names>
FROM <table name>;
```
For example, the next statement displays only column `name` from the `employee` table. Quotes here are crucial due to calling a column that has a name as a reserved word:
```
SELECT `name`
FROM employee;
```
Another example shows how to display all columns from a table `employee`:
```
SELECT *
FROM employee;
```
