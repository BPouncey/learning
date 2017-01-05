---
layout: lesson
title: Introducing PostgreSQL
lesson_date: 2017-01-30
---

## Pre-Work


Please read over the following links:
- [Postgres Data Types](https://www.tutorialspoint.com/postgresql/postgresql_data_types.htm)
- [PostgreSQL Schema](https://www.tutorialspoint.com/postgresql/postgresql_schema.htm)

To start getting familiar with SQL syntax, complete Part 1, from [these exercises](https://www.pgexercises.com/questions/basic/).

---

## Learning Objectives

- Define what role a database plays in an application.
- Explain how a relational database is structured.
- Install and set up an instance of PostgreSQL.
- Explain the difference between `TABLE` and `DATABASE`.
- Model data, and create tables to store it.
- Distinguish different data types in a SQL database context.
- Describe why a Schema is necessary.
- Create a simple Schema using PostgreSQL basic syntax.
- Write basic SQL queries to perform CRUD operations on a database.
- Write SQL queries in a SQL file and execute commands form the `psql` prompt.
- Add constraints to ensure consistent data.
- Implement an auto-incrementing id field.

---

## Keywords

- Relational database
- SQL
- CRUD
- `CREATE TABLE`
- `ALTER TABLE`
- `FOREIGN KEY`
- `INSERT`
- Data Types
- Schema

---

## Exercise 1

You should have a running instance of PostgreSQL running on your computer. In this lab activity,
we'll go through the process of setting up a few new databases within it, to use throughout the rest of our
time with PostgreSQL.

- Create 2 databases
We'll use on of these databases to try out new things. Once we're comfortable, we'll apply
what works to our `production` database.

- Use the `CREATE USER <name> WITH PASSWORD <pw>` command to create a new user and configure a password for each database.
See [documentation](https://www.postgresql.org/docs/9.6/static/sql-createuser.html).

(This setup is meant to mock a real world database setup, and to give us the opportunity to become familiar with
creating and authorizing a new Database on your local machine. In a real production setting, our setup would be more complicated).


---

## Exercise 2

Create Tables and set Data Types. What types of data do we need to model for our REDit application?

- Use the `CREATE TABLE` command to set up some tables in our test database.
- Set the apropriate data-types for each column in our schema.

**Handling Id's** <br/>
Each entry into the database for each of the schemas should have an id. This will be necessary for building
the relationships between data in out database.

- What data type is provided to implement and auto-incrementing id column?
- What are some important behaviors of an auto-incrementing column?

---

## Exercise 3

Postgres is a 'Relational Database'. So far we have not specified any relationships between our data models.
Let's create relationships between the tables we created in the last lesson.

The relationships we'll create are defined as follows:

 - 1 to 1 (1:1)
 - 1 to many (1:n)
 - Many to many (n:n)

To do this we'll need to add Foreign Key Constraints to some columns.

**Many to many relationships** :<br/>
Creating many to many relationships requires the creation of a "Link table".

- How are Link Tables implemented.
- Why are link tables necessary in order to define n:n relationships between columns in our database?
- WHat are the many to many relationships in our priject application's database?

---

## Exercise 4

Installing and setting up Postgres and a GUI for working with your database is complicated.
Take some time now to capture the steps for installing and setting up postgres on your local machine.

---

## Lab activity

Now that we've created our schema (table) for our project applications, user the `INSERT` command to populate
your data base with some mock data.

Add the following mock data to your database:

- 1 User
- 1 Week
- 1 Lesson
- 4 Posts
- 2 Tags

Ensure that you've set up the apropriate foreign key constraints!

---

## Additional Resources

- [Learn SQL - Codeacademy](https://www.codecademy.com/learn/learn-sql)
- [18+ Best Online Resources for Learning SQL and Database Concepts](http://www.vertabelo.com/blog/notes-from-the-lab/18-best-online-resources-for-learning-sql-and-database)
- [PostgreSQL Docsh](http://www.postgresql.org/docs/9.6)
