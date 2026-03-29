---
title: "Performance"
draft: false
---

Tags: #sql #queries #indexs #sql_injection

# Performace

## Index

Indexes in Postgres is powerful mechanism  that helps find data much faster on a large datasets compare to normal query.They allow the database to retrieve specific rows much faster than scanning the entire table. 

**Index :-** An index is a data structure that sql uses to quickly locate specific rows in table based on a value in one or more columns.

#### How to Create an Index

To create an Index in postgres, use `Create Index` statement.

syntax:

```sql
Create Index index_name on table_name(column_name);

-- Example

Create Index name_index on users(username)
```

- In example, this create an index named `name_index` on the `username` column of the `users` table.

#### Using index in query

Here's a catch, We don't need to specify index on queries because if there's any index in table postgres automatically uses it.

```sql
Select * from users Where username='allan1';
```

- If an index available on column, Postgres will use it to find raw quickly.

### Multi-Column Index

As the name suggest, We can index multiple column at once

example,

```sql
Create Index first_name_last_name_age_idx on users(first_name,last_name,age);
```

facts about multi-column :-

- A multi-column index is sorted by first column first, the second column next, and so on.
- We get all the performance on the first column only after than the performance start degrading. 

## SQL Injection

`Sql Injection` is very common way for hackers to breach our database and cause problems.

for example,

if someone is using this query 

```sql
Insert Into students(name) Values(?);`
```

hackers can inject malicious query like this:-

```sql
Insert Into students(name) Values('example');drop table students;--)
```

### How to prevent Sql-Injection

First of all we need to be aware of sql-injection, but nowdays risk is pretty low that someone directly run queries on database developers use library for inserting and updating records in database. Libraries are pre-configured to santize the input data so, it's secure to insert into database.

