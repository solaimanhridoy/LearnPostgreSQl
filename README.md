<img src="./img/postgresql-card.png" alt="PostgreSQL Icon" style="zoom:110%;" />

# Learn PostgreSQL 

>  A lightweight documentation of PostgreSQL for beginners.

## Table of Contents

- + - * [Learn PostgreSQL](#learn-postgresql)
        * [Table of Contents](#table-of-contents)
          + [Preface](#preface)
            - [What is a Database?](#what-is-a-database-)
            - [What is SQL and Relational Database?](#what-is-sql-and-relational-database-)
            - [What is PostgreSQL?](#what-is-postgresql-)
          + [Getting Started](#getting-started)
            - [Setup & Install PostgreSQL](#setup---install-postgresql)
            - [PostgreSQL Roles and User Login](#postgresql-roles-and-user-login)
              * [Accessing with Switching Accounts](#accessing-with-switching-accounts)
              * [Accessing without Switching Accounts](#accessing-without-switching-accounts)
              * [How to check Roles in PostgreSQL](#how-to-check-roles-in-postgresql)
              * [Create roles in PostgreSQL](#create-roles-in-postgresql)
              * [Update and Delete a Roll in PostgreSQL](#update-and-delete-a-roll-in-postgresql)
              * [Create and Delete Roles from using shell commands (Without connecting `psql`)](#create-and-delete-roles-from-using-shell-commands--without-connecting--psql--)
            - [How to create database](#how-to-create-database)
            - [How to connect a database](#how-to-connect-a-database)
          + [The SQL Language](#the-sql-language)
            - [Creating a new table to a database](#creating-a-new-table-to-a-database)
            - [Deleting a table from a database](#deleting-a-table-from-a-database)
            - [Adding data to the table](#adding-data-to-the-table)
            - [Querying data from the table](#querying-data-from-the-table)
      
      

### Preface

Here we will be introduced with PostgreSQL an open-source, robust, high-performance database with a lot of great features where we will do some hands-on practice to learn the basics of PostgreSQL. All the implementations were tested on Ubuntu 18.04. Before diving into PostgreSQL, we will have a look at some basic theory of **database**, **SQL**, and **PostgreSQL**.

#### What is a Database? 

The **database** is an organized collection of structured data that is used to store, manipulate, and retrieve data.

#### What is SQL and Relational Database? 

A **relational database** is a type of database that stores access to data points that are related to one another.

**SQL** (Structured Query Language) is a domain-specific language in programming that can manipulate a relational database.

#### What is PostgreSQL?

**PostgreSQL** also known as '**Postgres**' is an open-source, robust, high-performance object-relational database system that extends the SQL language with a lot of great features that safely store and scale the most complicated data workloads.



### Getting Started

#### Setup & Install PostgreSQL 

Just follow this link [Linux downloads (Ubuntu)](https://www.postgresql.org/download/linux/ubuntu/) and copy the script then paste on your terminal to install on Ubuntu using the apt repository. 

For other systems follow this official link [Downloads](https://www.postgresql.org/download/) to download and for installation instructions.

#### PostgreSQL Roles and User Login

PostgreSQL role is a feature by PostgreSQL for handling authentication and authorization. It's a concept of managing permissions where more than one roles can be created and roles can be members of other roles, allowing them to take on the permission to manipulate changes.

##### Accessing with Switching Accounts

After installation by default PostgreSQL created an account called  *postgres*  that is the default PostgreSQL Role. To log in this account, switch over to the *postgres* type this command:

`$ sudo -i -u postgres`

To access a Postgres prompt type:

`$ psql`

Now you will be logged in and able to start the interaction with the database.

To quit from Postgres prompt just type this command:

`postgres=#  \q`

##### Accessing without Switching Accounts

Following is the command that will log into Postgres without the intermediary *bash* shell in between.:

`$ sudo -u postgres psql`

##### How to check Roles in PostgreSQL 

To check the list of roles first type the following command:

`psql`

then type this:

`\du` 

We will see the list of roles with their name,  list of attributes, and member of which role.

##### Create roles in PostgreSQL

We noticed that by default there is a role named `postgres`. We can also create a new roll 

from the Postgres prompt.

First, enter into the prompt by typing `psql` if you are not already in. 

Then we can create a role simply typing this:

`CREATE ROLE new_roll_name;`

And we can add a password for the login session and add attributes that will define which types of access the role has been authorized to manipulate into the database. Then we can also add to the column 'member of' if the role is under any member.

Let's add a role where the user name is `lib10`with  authorized as `SUPERUSER`,  `CREATEDB`attributes and `PASSWORD`is 'abcd':

`CREATE ROLE lib10 WITH SUPERUSER CREATEDB PASSWORD 'abcd'; `

Type `\du` to see the newly created role.

##### Update and Delete a Roll in PostgreSQL

Suppose we need to add more attributes to our new role `lib10` and that means we need to update the role attributes change the password. 

To update attributes to the new role and change it's password type the command:

`ALTER USER WITH SUPERUSER CREATEDB CREATEROLE LOGIN ENCRYPTED PASSWORD 'Newabcd';`

If we need to delete a role than simply type:

`DROP ROLE lib10;`

##### Create and Delete Roles from using shell commands (Without connecting `psql`)

To create a database role with non-superuser access from the shell just type and enter:

`createuser -PE RoleName`

Where our `-P` flag prompts to set a password for the new role and the `-E`flag indicates to store the password as an MD5-encrypted string.

We can check the role created by connecting to `psql`and running `\du` command.

To Delete a database role from the shell just type:

`dropuser -i RoleName`

To create a superuser from the shell type:

`createuser -sPE SuperuserName`

#### How to create database

There are two ways to create a database. 

To create a database from shell type:

`$ createdb databaseName1`

To create a database from `psql`type:

`CREATE DATABASE databaseName2;`

To see the list of databases and  their details type from `psql`:

`\l`

To delete a database from the shell type:

`$ dropdb databaseName1`

And to delete the database from the `psql`type this:

`DROP DATABASE databaseName2;`

#### How to connect a database

To connect a database type from the shell:

`psql databaseName;`

To switch from another database type:

`\c databaseName2`

To get help for various SQL commands type:

`\h`

To quit from the database type:

`\q`

### The SQL Language 

To store, retrieve, and manipulate database PostgreSQL uses the basic SQL language. Let's see some examples.

#### Creating a new table to a database

In SQL to create a table we need to define the table name, column name and their data types.

To create a table type:

```
CREATE TABLE weather (
    city            varchar(80),
    temp_lo         int,           -- low temperature
    temp_hi         int,           -- high temperature
    prcp            real,          -- precipitation
    date            date
);
```

Here we can see a table named weather where 5 columns and their data types added. Here in the first column `city` is a column and `varchar` is its types with a range of 80 characters.  We can add a comment to start with`--` and we can see three comments here.

 Another example:

```
CREATE TABLE cities (
    name            varchar(80),
    location        point
);
```

The `point` type is an example of a PostgreSQL specific data type.

#### Deleting a table from a database

To delete a database type this:

```
DROP TABLE tablename;
```

#### Adding data to the table

To add or insert data into a table type this example:

```
INSERT INTO weather VALUES ('San Francisco', 46, 50, 0.25, '1994-11-27');
```

Here we can see the table name should be specified with its columns value.

Another example:

```
INSERT INTO cities VALUES ('San Francisco', '(-194.0, 53.0)');
```

We saw a type PostgreSQL specific data type `point` above example shows that we the of `point` type should be defined as coordinate pairs.

An alternative way to insert data to avoid remembering the column name:

```
INSERT INTO weather (city, temp_lo, temp_hi, prcp, date)
    VALUES ('San Francisco', 43, 57, 0.0, '1994-11-29');
```

Column name can be listed in a different order.

```
INSERT INTO weather (date, city, temp_hi, temp_lo)
    VALUES ('1994-11-29', 'Hayward', 54, 37);
```

An additional feature and optimized way to insert a large number of data just type `COPY`command with the table name and its location.

```
COPY weather FROM '/home/user/weather.txt';
```

#### Querying data from the table

To retrieve data from a table type this:

```
SELECT * FROM weather;
```

We can write expressions, not just simple column references, in the select list. For example, we can do:

```
SELECT city, (temp_hi+temp_lo)/2 AS temp_avg, date FROM weather;
```





To be continued ...