---
title: "basics"
draft: false
---

# SQL

Structured Query language or sql is database which is used to collect data and store it.

### Select Statment

A `Select` statment is most common operation in Sql -often called  a "query". Select retrives data from one or more table.

- Standard `Select` statement does not alter the state of the database.

#### Select a single field

A Select statement starts with <code>Select</code> followed by the fields you want to retrive

```sql
Select name from users;
```

#### Select a Multiple field

If you want to select multiple fileds specify those fields using commas

```sql
Select id,name from users;
```

#### Select All field

To select all fields in table use the shorthand `*` syntax.

```sql
Select * from users;
```

## SQL vs NoSQL

A NoSql database is a database which does not use SQL(Structured Query Language). Each NoSql database has its own way to write it's queries.

- NoSql database are generally non-relational 
- Sql database are relational databases.

ex sql database:- Postgres, Sql , SQlite, Oracle etc
ex NoSql database:- Mongodb , Cassandra , CouchDB , redis etc



