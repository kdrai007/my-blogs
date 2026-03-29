---
title: "constraints"
draft: false
---

# Constraint

A constraint is a rule we create on a database that enforces some specific behaviour. For example, Setting a `Not Null` on a column ensures that the column can not be left empty. 

example,

```sql
Create Table employees (
	id Integer Primary Key,
	name Text UNIQUE,
	title Text Not Null
);
```
## Null Types

In Sql, a cell with `NULL` value indicates that the cell is empty. A `NULL` is different than zero value.

### Constraints

When creating a table we can decide whether or not field can or cannot be `NULL`, and that's kind of constraint. 


## Primary Keys

A Key defines and protects relationship between tables. A `primary key` is a special column that uniquely indentifies column

- Each column can only have one `Primary Key`.

## Foregin Keys

Foregin Key are is what makes relational database relational! Foregin keys defines that relationship between tables.

- Foregin keys points to Primary key of another table.

Foregin keys -> Primary Key

example,

```sql

Create Table departments(
id Integer Primary Key,
department_name Text Not Null
);

Create Table employees(
id Integer Primary Key,
name Text Not Null,
department_id Integer,
Constraint fk_departments
Foregin Key (department_id),
References department(id)
)
```


