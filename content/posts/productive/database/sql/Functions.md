---
title: "Functions"
draft: false
---

SQL is a programming language and like nearly all programming language it's supports functions.We can use functions and alias to calculate new columns in a query.

### Between

We can check if values are `Between` two numbes using the `Where` clause in an intuitive way!

```sql
SELECT user,salary FROM employees WHERE salary BETWEEN 2000 And 80000;
```

- This query will return user and salary column from employees table whose salary is between 2k and 80k.

### Distinct

Sometimes we want to retrieve records from a table without any duplicates.

```sql
SELECT DISTINCT previous_company FROM employees;
```

### Logical Operators - AND

We often need to use multiple condtions to retrieve exact information we want.We can begin to structure much more complex queries by using multiple conditions to narrow down the search result. 
#### And operator

```sql
Select name,address,contact from members
Where city = "New York"
And age Between 20 and 40;
```

- This query only retrive a member who are from "New York" and their age is between 20 to 40.



#### Equality operators

All of the following operators are supported in SQL. The = is the main one to watch out for, it's not == like in many other languages! SQLite does allow for == but it's not a good habit to get into, as other dialects of SQL will not recognize == as valid syntax.

- =
- <
- >
- <=
- >=

```sql
Select * from users
	Where country_code = "CA"
	And age <=18;
```

#### OR

```sql
Select * 
	From products
	Where shipment_status = 'out of stock'
	Or Quantity Between 10 and 80;
```

- This query retrieve every column where shipment status is 'out of stock' or quantity is between 10 and 80.
#### IN

Another variation to the `WHERE` clause we can utilize is the `IN` operator. `IN` operator return `True` or `False` if the first operand matches any of the values in second operand.

exmaple,

```sql
Select *
	From products
	WHERE shipment_status IN ('out of stock', 'shipped','preparing');
```

- This query fetch all products whose `shipment_status` is either 'out of stock','shipped' or 'preparing'.
- Compare to `AND` operator `IN` operator is easy to compare different fields together.

#### LIKE

Sometimes we don't have the luxery of knowing exactly what we need to query. That's where `LIKE` comes in

for example,

```sql
Select * from users WHERE name LIKE 'As%' 
```

- This query will fetch every `user` whose name starts with 'As' like 'Ashoka' or 'Ashwin'.


```sql
Select * from users WHERE name LIKE '%as' 
```

- This query will fetch every `user` whose name ends with 'as'


```sql
Select * from users WHERE name LIKE '%as%' 
```

- This query will fetch every user whose name contain 'as' between their words.

#### Underscore Operator

The `%` wildcard operator matches zero or more characters. Meanwhile `_` operator only matches a single character.

```sql
SELECT * From users 
	Where name Like '__un';
```

- This query will fetch user whose name are exactly 4 char long and their name ends with `un`.





