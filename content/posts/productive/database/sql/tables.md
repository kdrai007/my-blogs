---
title: "tables"
draft: false
---

# Tables in SQl

Tag : #postgres #sql #alter

### Creating A Table

To create a new table in database , use the `Create Table` statement followed by the name of the table and the fields you want in the table.

ex, 

```sql
CREATE TABLE employees (
id Integer,
name TEXT, 
age Integer,
salary INTEGER
);
```

- Each fields is followed by its datatype

### Alter a Table

We often need to alter our table If we need to add any further fields or remove any existing field.

#### 1. Rename a table or column

```sql
Alter Table employees RENAME to contractors;

Alter Table contractors Rename Column salary to invoice;
```

#### 2. Add or Drop a Column

```sql
Alter Table contractors Add Column job_title Text;

Alter Table contractors Drop Column job_title;
```

### Auto Increment

Many dialect of SQL support an `Auto Increment` feature. When inserting docs into database while auto increment enable and database system assign some value automatically.

### Where Clause

SQL accepts a `Where` statement within a query that allows us to be very specific with our instructions.

example,

```sql
Select * From Users Where age >18;
```

- This query will give output of all the users above 18 age group.

#### Finding Null Values

You Can use `Where` clause to filter values whether they are `NULL` or `NOT NULL`

for null,

```mysql
Select * From users Where firstname IS NULL;
```

not null,

```mysql
Select * From users Where firstname IS NOT NULL;
```

#### Delete

A `DELETE` statement remove records from the table that matches `WHERE` clause, example:-

```sql
DELETE FROM employees
Where age >= 60
```

### Update Query

A `UPDATE` statement update existing value in a table, example :-

```sql
UPDATE bank SET balance = 150000 WHERE id = 531;
```

- This query will set balance of bank user with id 531 150k


## Migrations

A database migration is a set of changes to a relational database. In fact, alter table statements which we used previously are examples of migrations.



