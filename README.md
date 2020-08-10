![PostgreSQL Icon](https://blog.xojo.com/wp-content/uploads/2017/06/postgresql-card.png)

# Learn PostgreSQL 

[TOC]

### Preface

Here we will be introduced with PostgreSQL an open-source, robust, high-performance database with a lot of great features where we will do some hands-on practice to learn the basics of PostgreSQL. All the implementations were tested on Ubuntu 18.04. Before diving into PostgreSQL we will have a look at some basic theory of **database**, **SQL**, and **PostgreSQL**.

#### What is a Database? 

The **database** is an organized collection of structured data which is used to store, manipulate and retrieve data.

#### What is SQL and Relational Database? 

A **relational database** is a type of database that stores access to data points that  are related to one another.

**SQL** (Structured Query Language) is a domain specific language in programming that can manipulate a relational database.

#### What is PostgreSQL?

**PostgreSQL** also known as '**Postgres**' is an open source, robust, high performance object-relational database system that extends the SQL language with a lot of great features that safely store and scale the most complicated data workloads.



### Getting Started

#### Setup & Install PostgreSQL 

Just follow this link [Linux downloads (Ubuntu)](https://www.postgresql.org/download/linux/ubuntu/) and copy the script then paste on your terminal to install on Ubuntu using the apt repository. 

For other system follow this official link [Downloads](https://www.postgresql.org/download/) to download and for installation instructions.

#### PostgreSQL Roles and User Login

PostgreSQL roles is a feature by PostgreSQL for handling authentication and authorization. It's a concept of managing permissions where more than one roles can be created and roles can be members of other roles, allowing them to take on the permission to manipulate changes.

##### Accessing with Switching Accounts

After installation by default PostgreSQL created account called  *postgres*  that is the default PostgreSQL Role. To log in this account, switch over to the *postgres* type this command:

`$ sudo -i -u postgres`

To access a Postgres prompt type:

`$ psql`

Now you will be logged in and able to start interaction with the database.

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

We will see the list of roles with their name,  list of attributes and member of which role.

####  



####  



