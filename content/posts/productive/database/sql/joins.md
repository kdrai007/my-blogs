---
title: "joins"
draft: false
---

Tags: #sql #queries #joins

# Joins

Joins are one of the most important feature that SQL offers. Joins allow us to make use of relations between tables, In short joins allows use to query multiple tables at same time.


## Inner Join

The simplest and most common joins in sql is `Inner Join`. By default a `join` command is an Inner Join. 

![[Pasted image 20241219003303.png]]

- Here is simple diagram of `Inner Join` 

#### On

To perform a table join, we need to tell database how to "match up" the rows from each table. The `ON` clause specifies the each colums to compare.

```sql
Select * from employees e
	Inner Join departments d
		On e.department_id = d.id;
```

This is basic example of join.

### Namespacing  On Tables.

When working with multiple tables, you can specify which table a field exists on using `.`.

example,

```sql
Select student.name , classes.class From student
Inner Join classes ON classes.id = students.class_id;
```

- The above query returns `name` from `student` table and `class` from the `classes` table.


## Left Join

A `Left Join` will return every record from `table_a` regardless if there's any record matches from `table_b`. A left join will also return any matching records from `table_b`

![[Pasted image 20241219142936.png]]

- Here's a diagram of how `left join` positioned between two tables. 	

example,

```sql
Select e.name,d.name From employees e
Left Join departments d
On e.department_id=d.id;
```

### Right Join

A `Right Join` returns all records from `table_b` regardless of matches, and all matching records between two tables.

- A `Right Join` is same as `Left Join` with the order of tables switched.
- In most cases `Left Join` is preferred for readability.

### Full Join

A `Full Join` combines the result set of the `Left Join` and `Right Join` commands. It returns all the records from both from `table_a` and `table_b` regarless of there's any matches.

![[Pasted image 20241220095947.png]]

### Multiple Join

To incorporate data from more than one table, you can utilize multiple jons to execute more complex queries.