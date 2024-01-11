# **PostgreSQL**<a id="docs-internal-guid-284870f4-7fff-2c24-7615-c3f2db4301e6"></a>

# Table of Contents
1. [Introduction to PostgreSQL](#introduction-to-postgresql)
   - [What is PostgreSQL?](#what-is-postgresql)
   - [History of PostgreSQL](#history-of-postgresql)
   - [Features of PostgreSQL](#features-of-postgresql)
2. [Setup PostgreSQL](#setup-postgresql)
   - [Installation](#installation)
   - [Checking PostgreSQL Version](#checking-postgresql-version)
   - [Accessing PostgreSQL Database](#accessing-postgresql-database)
   - [Creating and Managing Databases](#creating-and-managing-databases)
3. [Tables and Schemas](#tables-and-schemas)
   - [Creating Tables](#creating-tables)
   - [Listing Tables](#listing-tables)
   - [Inserting, Updating, and Deleting Data](#inserting-updating-and-deleting-data)
4. [Views, Joins, and Functions](#views-joins-and-functions)
   - [Views](#views)
   - [Joins](#joins)
   - [Aggregate Functions](#aggregate-functions)
   - [User-Defined Functions and Triggers](#user-defined-functions-and-triggers)
5. [Additional SQL Operations](#additional-sql-operations)
   - [Indexes, Arrays, and Enumerations](#indexes-arrays-and-enumerations)
   - [Logical Operators and String Functions](#logical-operators-and-string-functions)



# What is postgreSQL?

* It is a powerful,open source object-Rational database management System(ORDBMS)
* It is used to store data securely
* It is developed by the PostgresSQL Global development Group(a team of volunteers).It is not controlled by any corporation or other private entity.

# History of postgreSQL

It was started in 1986 by professor Stonebreaker as a follow up project.PostgresSQL is now the most advanced open-source database available anywhere.

                                         

# Features of postgreSQL?

* It runs on all major  as like -Linux,Unix and windows.
* It supports text,image,sound,video and include interface for many language like-c,c++, java etc.
* It supports a lot of features of sql like-complex sql queries,foreign    key,triggers,view,transations and concurrency etc.
  In postgresql tables can be set to inherit their characteristics from a “parent” table.


# Setup PostgreSQL:
```
sudo apt update
```

**Output**-
```
Hit:1 http\://packages.microsoft.com/repos/code stable InRelease                                                                                                                  
Hit:2 http\://in.archive.ubuntu.com/ubuntu jammy InRelease                                                                                               
Get:3 http\://security.ubuntu.com/ubuntu jammy-security InRelease \[110 kB]                                                                        
Hit:4 https\://dl.google.com/linux/chrome/deb stable InRelease                                                                                    
Get:5 http\://in.archive.ubuntu.com/ubuntu jammy-updates InRelease \[119 kB]                                                                                                      
Hit:6 https\://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease                                                                                                             
Hit:8 http\://in.archive.ubuntu.com/ubuntu jammy-backports InRelease         
Get:7 https\://download.opensuse.org/repositories/devel:kubic:libcontainers:unstable/xUbuntu\_22.04  InRelease \[1,262 B]
Ign:9 https\://pkg.jenkins.io/debian-stable binary/ InRelease    
Hit:10 https\://pkg.jenkins.io/debian-stable binary/ Release                                                                                                                     
Err:11 http\://pkg.jenkins.io/debian-stable binary/ Release.gpg
The following signatures couldn't be verified because the public key is not available: NO\_PUBKEY 5BA31D57EF5975CA
Fetched 230 kB in 7s (33.1 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
82 packages can be upgraded. Run 'apt list --upgradable' to see them.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'https\://apt.postgresql.org/pub/repos/apt jammy-pgdg InRelease' doesn't support architecture 'i386'
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https\://pkg.jenkins.io/debian-stable binary/ Release: The following signatures couldn't be verified because the public key is not available: NO\_PUBKEY 5BA31D57EF5975CA
W: Failed to fetch http\://pkg.jenkins.io/debian-stable/binary/Release.gpg  The following signatures couldn't be verified because the public key is not available: NO\_PUBKEY 5BA31D57EF5975CA
W: Some index files failed to download. They have been ignored, or old ones used instead**.**
```
```
sudo apt-get install postgresql
```


**Output**-
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
 postgresql-doc
The following NEW packages will be installed:
postgresql
0 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
Need to get 68.9 kB of archives.
After this operation, 73.7 kB of additional disk space will be used.
Ign:1 https\://apt.postgresql.org/pub/repos/apt jammy-pgdg/main amd64 postgresql all 16+256.pgdg22.04+1
Get:1 https\://apt.postgresql.org/pub/repos/apt jammy-pgdg/main amd64 postgresql all 16+256.pgdg22.04+1 \[68.9 kB]
Fetched 68.9 kB in 47s (1,462 B/s)    
Selecting previously unselected package postgresql.
(Reading database ... 229113 files and directories currently installed.)
Preparing to unpack .../postgresql\_16+256.pgdg22.04+1\_all.deb ...
Unpacking postgresql (16+256.pgdg22.04+1) ...
Setting up postgresql (16+256.pgdg22.04+1) …
```

**How to check the version of postgreSql?**
```
psql --version
```

**Output**-
```
bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$ psql --version
psql (PostgreSQL) 16.1 (Ubuntu 16.1-1.pgdg22.04+1)
bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$
```

**Access the PostgreSQL database management system as the PostgreSQL superuser.**
```
sudo -u postgres psql
```

**Output**
```
[sudo] password for bhavesh:
psql (16.1 (Ubuntu 16.1-1.pgdg22.04+1))
Type "help" for help.
```

**sudo**: This stands for "superuser do." It's like asking for special permission to do something important.

**-u postgres**: This tells the system to pretend to be another user when running the following command.

**psql**: This is the command to enter the PostgreSQL database. It's like opening a door to the database where you can talk to it and ask it to do things.

**To see available list of database -**
```
 \l
```
**Output**
```
                                                List of databases

Name |  Owner   | Encoding | Locale Provider | Collate | Ctype | ICU Locale | ICU Rules |   Access privileges   

-------------+----------+----------+-----------------+---------+-------+------------+-----------+-----------------------
employee | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       |
 google  | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       |
 keenable | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       |
 postgres | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       |
 techonology | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       |
 template0   | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       | =c/postgres      +

          |      |      |             |     |   |        |       | postgres=CTc/postgres

 template1   | postgres | UTF8 | libc        | en\_IN   | en\_IN |        |       | =c/postgres      +

          |      |      |             |     |   |        |       | postgres=CTc/postgres
```

**l**: This is a shorthand for the "list" command in psql.

**Database**:A database is a structured collection of data that is organized and stored in a way that makes it easy to manage, retrieve, and update

**Now we create database**-
```
create database <db name>;
```
**Output-**
```
postgres=# create database company;
CREATE DATABASE
```
**CREATE DATABASE:** This is the SQL command used to instruct the database management system (DBMS) to create a new database.
**company:** This is the database name.

**To Switch other database-**
```
 \c <db name>
```
**Output**-
```
postgres=# \c company;
You are now connected to database "company" as user "postgres".
company=#
```
**\c:** The `\c` command is a way of saying, "I want to connect to a different database." It's like walking into a different room to chat about a specific topic.

**How to delete database**-
```
Drop database <db name>
```
**Output-**
```
postgres=# drop database company;
DROP DATABASE
postgres=#
```
**DROP DATABASE:** This SQL command tells the database management system (DBMS) that you want to get rid of a database.

**Table**-

In PostgreSQL, a table is like a virtual spreadsheet or a grid where you can organize and store information.
Here are some simple terms to understand a table in PostgreSQL:

**Rows**: Each row in the table is like a single entry or record. For example, if you have a table for "Students," each row could represent information about a specific student

**Columns**: Columns are like categories or attributes for your data. In the "Students" table, you might have columns for "Name," "Age," and "Grade," where each column holds specific information about the students.

**Cells**: Each intersection of a row and a column is a cell. It holds a single piece of data. For instance, the cell in the "Name" column and the first row might have the value "John."

**Create Table**-
```
company=# create table employee(id int not null primary key,fname text not null,lname text not null,age int not null);
CREATE TABLE
company=#
```
**create table employee**:This is the new table name.

**Id**: This line defines a column named "id" with the data type "int" (integer). The "not null" constraint means that this column must always have a value.A primary key ensures that each value in the designated column(s) is unique.

**Fname text not null**:This line creates a column named "fname.the `TEXT` data type is used to store character strings of any length.

**lname text not null**:This lines also creates a column “lname.

**age int not null**:Creates a column for the age of the employee using the "int" data type.

**To check list all tables in the current database**:
```
\d
```
**Output**-
```
company=# \d
List of relations
 Schema |   Name   | Type  |  Owner   
--------+----------+-------+----------
 public | employee | table | postgres
(1 row)
```
**\d**:It's like a special instruction to ask PostgreSQL for details about database objects.

**To list tables with additional details (columns, types, constraints):**
```
\d tablename
```
**Output**-
```
company=# \d employee;
           Table "public.employee"
 Column |  Type   | Collation | Nullable | Default
--------+---------+-----------+----------+---------
 id | integer |       | not null |
 fname  | text |       | not null |
 lname  | text |       | not null |
 age | integer |       | not null |
Indexes:
"employee\_pkey" PRIMARY KEY, btree (id)
```
**If you want to exit the database**:
```
\q
```
**Output**-
```
company=# \q
bhavesh@bhavesh-HP-Laptop-15-da1xxx:~$
```
**\q**:it instructs PostgreSQL to exit the interactive session and return to the regular command prompt or shell.

**Schema**-
a schema in a database is like a folder that helps organize and categorize your data. Imagine you have a big cabinet, and inside it, you use different folders to keep things sorted. Each folder might contain related documents or items.

**Create Schema**-
```
Create schema\<schema name>
```
**Output**-
```
company=# create schema newschema;
CREATE SCHEMA
company=#
```
**Insert value into table**-
```
insert into employee values(1,'Rahul','Sharma',28);
```
**Output**-
```
company=# insert into employee values(1,'Rahul','Sharma',28);
INSERT 0 1
company=#
```
**Insert into:** This statement is used in SQL to add new records (rows) into a table.

**employee:** employee is the name of the table.

**Values:** It indicates that you are about to provide the values for the columns.

**Check insert value in the table**-
```
Select * from <table name>
```
**Output**-
```
company=# select * from employee;
 id | fname | lname  | age
----+-------+--------+-----
 1 | Rahul | Sharma |  28
(1 row)
```
**SELECT**: This part instructs the database to retrieve all columns from the specified table.

**FROM employee:** This part tells the database from which table it should retrieve the data. In this case, it's the "employee" table.

**Select Keyword**-This is the SQL keyword that signals the start of a query to retrieve or fetch data use.

**Fetch data from the table**-
```
Select id,fname,lname from employee;
```
**Output**-
```
company=# select id,fname,lname from employee;
id | fname | lname  
----+-------+--------
1 | Rahul | Sharma
(1 row)
```
**Update data in table**-
To update existing data in a table, you use the update statement.
```
update employee set fname='lucky' where age=28;
```
**Output**-
```
company=# update employee set fname='lucky' where age=28;
UPDATE 1
company=#
```
**UPDATE employee**: Specifies that you want to update data in the "employee" table.

**SET fname**:'lucky': Indicates the change you want to make. It says, "Set the value of the 'fname' (first name) column to 'lucky'."

**WHERE age=28**: Acts as a condition. It says, "Apply the update only to the rows where the 'age' column is equal to 28."

**Delete data from table**-
To delete data from a table, you use the DELETE statement.
```
delete from employee where id=1;
```
**Output**-
```
company=# delete from employee where id=1;
DELETE 1
company=#
```
**DELETE FROM employee**: Specifies that you want to delete data from the "employee" table.

**WHERE id=1**: Acts as a condition. It says, "Delete the rows where the value in the 'id' column is equal to 1.

**WHERE Clause**-it is used to provide conditions in SELECT, UPDATE, and DELETE statements to filter rows based on a specified condition.
```
select * from employee where age>=28;
```
**Output-**
```
company=# select * from employee where age>=28;
id | fname | lname  | age
----+-------+--------+-----
1 | lucky | sharma |  28
```
**SELECT * FROM employee:** Specifies that you want to retrieve data from the "employee" table. The `*` means you want to retrieve all columns.

**WHERE age >= 28:** Acts as a condition. It says, "Retrieve only the rows where the value in the 'age' column is greater than or equal to 28.

**ORDER BY Clause**- It is used in SELECT statements to sort the result set based on one or more columns. Like- asc desc.
```
select * from employee order by age asc;
```
**Output**-
```
company=# select * from employee order by age asc;
 id |  fname  |  lname  | age
----+---------+---------+-----
2 | rahul   | kaushik |  22
1 | lucky   | sharma  |  28
3 | neeraj  | garg |  33
4 | brijesh | yadav   |  34
(4 rows)
```
**Group by clause**-It is used to change a particular field or data in group and show the other table form
```
select fname,sum(age) from employee group by fname;
```
**HAVING Clause**-It is used to provide a condition and SELECT statements with GROUP BY to filter grouped rows based on a condition.
```
select fname from employee group by fname having count(fname)=1;
```
**Add a column to a table**-To add a new column to an existing table, you use the ALTER TABLE statement.
```
alter table employees add column salery int;
```
**Output**-
```
company=# select * from employees;
```
 id |  fname  |  lname  | ages | salery

**ALTER TABLE**:- This phrase is used to modify an existing table structure
.
**employee**: This is the name of the table to which you want to make changes.

**ADD COLUMN**: This specifies that you want to add a new column to the table
.
**salary**: This is the name of the new column that you want to add.

**int**:`INT` stands for "integer," and it is a data type in databases used to store whole numbers.

**Rename column**: To rename a column, use the ALTER TABLE statement with the RENAME COLUMN clause.
```
alter table employees rename salery to hours;
```
**Output**-
```
company=# select * from employees;
 id |  fname  |  lname  | ages | hours
----+---------+---------+------+-------
```
**Rename table**-To rename a table, use the ALTER TABLE statement with the RENAME TO clause.
```
alter table employees rename to employee;
```
**Output**-
```
company=# alter table employees rename to employee;
ALTER TABLE
company=# select * from employee;
```
**Rename column**-To rename a column, use the ALTER TABLE statement with the RENAME COLUMN clause.
```
alter table employee rename column hours to age;
```
**Output-**
```
company=# alter table employee rename column hours to age;

ALTER TABLE
```
**Delete a column from a table**-To delete an existing column from a table, you use the ALTER TABLE statement.
```
alter table employee drop column age;
```

**Output-**
```
company=# alter table employee drop column age;
ALTER TABLE
company=#
```
**View**-In PostgreSQL, a user view is a virtual table that presents data from one or more tables in a simplified way for users to query.
```
create view new_employee as select fname,ages from employee;
```
**How to show view table**-
```
select * from new_student;
```
**Inner join\simple join**-A JOIN in PostgreSQL is used to combine rows from two or more tables based on a related column between them.
```
select employee.fname,employee.lname,student.name from employee inner join student on employee.id=student.id;
```

**Left join**-In a left join, all records from the left table are included, and matching records from the right table are added, with non-matching values replaced by NULLs.
```
select employee.fname,employee.lname,student.name from employee left join student on employee.id=student.id;
```
**Right join**-In a right join, all records from the right table are included, and matching records from the left table are added, with non-matching values replaced by NULLs.
```
select employee.fname,employee.lname,student.name from employee right join student on employee.id=student.id;
```
**Cross join**-In a cross join, every row from the first table is combined with every row from the second table, creating all possible combinations.
```
select name,fname from student cross join employee;
```

**Full outer join**- A FULL OUTER JOIN returns all rows when there is a match in either the left or the right table. If there is no match, NULL values are returned for columns from the table without a match.
```
select employee.fname,employee.lname,student.name from employee full outer join student on employee.id=student.id;
```
**Aggregate functions**-In PostgreSQL, aggregate functions perform a calculation on a set of values and return a single result. Examples include SUM, AVG, COUNT, MAX, and MIN.

**Sum**-Adds up all the values in a numeric column.
```
select sum(salery) from new_employee;
```
**Output-**
```
company=# select sum(salery) from new_employee;
sum   
--------
127000
```
**Avg**-Calculates the average (mean) of values in a numeric column
```
select avg(salery) from new_employee;
```
**Output**-
```
company=# select avg(salery) from new_employee;
avg     
--------------------
31750.000000000000
```
**Max**-Finds the highest value in a column.
```
select max(salery) from new_employee;
```
**Output**-
```
company=# select max(salery) from new_employee;
 max  
-------
 59000
(1 row)
```
**Min**-Finds the lowest value in a column
```
select min(salery) from new_employee;
```
**Output**-
```
company=# select min(salery) from new_employee;
min  
------
8000
```
**Count**-Counts the number of rows in a result set.
```
select count(salery) from new\_employee;
```
**Output**-
```
company=# select count(salery) from new_employee;
count
-------
4
(1 row)
```
## User defined function##-
A user-defined function (UDF) is like a custom operation or calculation that you create in a database to perform a specific task.

**Triggers**:Triggers in databases are like automatic actions that get executed (e.g. insert,update,delete) when certain events (e.g.,changes to a table) occur,helping to maintain data integrity or perform additional tasks.

**Alias**: Alias is like a nickname or a short name that you give to a column or a table in a query. It helps make your query results more readable and provides a way to reference columns or tables with a different name.
```
select max(salery) as max_salery from new_employee;
```
**Output**-
```
company=# select max(salery) as max_salery from new_employee;
 max_salery
------------
 59000
(1 row)
```

**Index**: index is a database object that improves the speed of data retrieval operations on a table.
```
create index new_student on new_employee("name");
```
**Array**:An array is a data structure that stores a collection of elements of the same type.It allows you to group related pieces of data together under a single name.
```
create table worker(id int not null,name text,salery integer[],work_hours text[][]);
```
**1d array (value access)**
```
select salery[2] from worker;
```
**2d array(value access)**
```
select work_hours[1][1] from worker;
```
**Enumeration:** Using this function we can create our according data type.
```
create type mood as enum('sad','ok','happy');
```
**Logical Operators**-

AND (logical AND)

OR (logical OR)

NOT (logical NOT)

**And Operator**:And" is a logical operator used in programming and Boolean logic to combine two conditions. It returns true only if both conditions are true.
```
 select * from student where name='rajnish' and age=33;
```
**Output**-
```
company=# select * from student where name='rajnish' and age=33;
 id |  name   | age
----+---------+-----
  1 | rajnish |  33
```
**OR Operator**:The OR operator is used to combine multiple conditions in a SQL statement. It returns true if at least one of the conditions joined by OR is true.
```
select * from student where name='shyam' or age=40;
```
**Output-**
```
company=# select * from student where name='shyam' or age=40;
 id | name  | age
----+-------+-----
2 | shyam |  22
(1 row)
```
**Not**:Not" is a logical operator that reverses the truth value of a condition, turning true into false and false into true.
```
select * from student where name is not null;
```
**Output**-
```
company=# select * from student where name is not null;
id |  name   | age
----+---------+-----
  1 | rajnish |  33
  2 | shyam   |  22
  3 | gaurav  |  22
(3 rows)
```

**Like operator**:Like" is a string comparison operator used in databases and programming that allows for pattern matching, often used in queries to search for a specified pattern within a text column.
```
select * from student where name like 'ra%';
```
**Output-**
```
company=# select * from student where name like 'ra%';
 id |  name   | age
----+---------+-----
1 | rajnish |  33
(1 row)
```
**IN**: The IN operator checks if a specified value matches any value in a list.
```
select * from student where age in(33,22,22);
```
**Output**-
```
company=# select * from student where age in(33,22,22);
 id |  name   | age
----+---------+-----
  1 | rajnish |  33
  2 | shyam   |  22
  3 | gaurav  |  22
(3 rows)
```
**NOT IN**: The NOT IN operator, as the name suggests, negates the condition of the IN operator. It checks if a specified value does not match any value in a list.
```
select * from student where age not in(21,67,45);
```
**Output**-
```
company=# select * from student where age not in(21,67,45);**
 id |  name   | age
----+---------+-----
  1 | rajnish |  33
  2 | shyam   |  22
  3 | gaurav  |  22
(3 rows)
```
**Between Operator**:"Between" is an operator in programming and databases used to filter values within a specified range, inclusive of the endpoints.
```
select * from student where age between 21 and 40;
company=# select * from student where age between 21 and 40;
 id |  name   | age
----+---------+-----
  1 | rajnish |  33
  2 | shyam   |  22
  3 | gaurav  |  22
(3 rows)
```
**String function**-

**concate:**"Concatenate" is an operation that combines two or more strings into a single string in programming and data manipulation.
```
select concat('hello','world','hi');
```
**Output**-
```
company=# select concat('hello','world','hi');
concat    
--------------
 helloworldhi
(1 row)
```
**Length**:Length" is a function in programming and databases that returns the number of characters in a string or the number of elements in a collection, providing the size or length of the data.
```
 select length('hello');
```
**Output**-
```
company=# select length('hello');
 length
--------
   5
(1 row)
```
**Lower**: Converts a string to lowercase.
```
select lower('HELLO');
```
**Output**-
```
company=# select lower('HELLO');
 lower
-------
 helo 
```
**Upper**: Converts a string to uppercase.
```
company=# select upper('hello') as upparcase;
 upparcase
-----------
 HELLO
```
**Position**:Position" is a function in programming and databases that identifies the starting position of a substring within a string, helping to locate specific text or characters.
```
select position('ha' in 'bhavesh')
```
**Output-**
```
company=# select position('ha' in 'bhavesh');
 position
----------
     2
```
**Ascii**: Returns the ASCII value of the first character in a string.
```
 select ascii('a');
company=# select ascii('a');
 ascii
-------
97
```
**Reverse:** Reverses the order of characters in a string.
```
select reverse('hello');

company=# select reverse('hello');

 reverse
--------------------
 olleh 
```
**Repeat:** Repeats a string a specified number of times.
```
select repeat('hell0',4);
```
**Output**-
```
company=# select repeat('hell0',4);
     repeat    
----------------------
 hell0hell0hell0hell0
```
