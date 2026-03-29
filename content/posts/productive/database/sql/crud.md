---
title: "crud"
draft: false
---

# CRUD

CRUD is a acronym that stands for `Create`,`Read`,`Update`  and `Delete`. These four funtionalites are basic in every database language.

## Create

- To create a table you can use this statement in sql.

```sql
Create Table users(
	id SERIAL Primary Key, -- Serial data type increment id by one
	name TEXT Not Null,
	email Text Unique Not Null
)
```

### Object Relational Mapping (ORMs)

ORM is a tool that allows us perform CRUD operations on database using a trandional programming language. These generally comes in the form of `library` or `Framework` that you would use in backend code. 


