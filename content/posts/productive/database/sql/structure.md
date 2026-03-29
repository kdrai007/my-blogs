---
title: "structure"
draft: false
---

## Limit

Sometimes we don't want to retrieve every records from a table. For example, It's pretty common to have millions of records in table if we try to fetch all records at once system can crash. That's where `LIMIT` clause comes in

```sql
Select * From users Limit 10;
```

- This query will retrieve only 10 records from the table `users`.


## Order By

SQL also offer us the ability to sort the results of query using `ORDER BY`. Order By keywords sort records by the given field in acending order, OR `ASC` for short, or you can sort in `DEC` order.

example,

```sql
Select * from users
	Order By price DESC
	;
```

> When using both `ORDER BY` and `LIMIT` remember `ORDER BY` always comes first.