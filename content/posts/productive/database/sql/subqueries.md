---
title: "subqueries"
draft: false
---

# SubQueries

tag: #sql #subquery #query 

Sometimes a single query is not enough to fetch all records we need.

here, an example for subquery

```sql
Select id,song_name,artist_id 
	From songs
	Where artist_id IN(
		Select id 
		From artists
		Where artist_name LIKE '%Arj%'
	);	
```

### Subqueries in `SELECT` clause

- Used to calculate a value for each row.

```sql
Select id,name, 
	(
	 Select Max(amount)
	 From transaction t1 
	 Where t1.user_id = u1.id
	 ) As max_amount
  From users u1
  ;
```

- Here in this query, we are fetching some fields in `users` table in which we are trying to fetch max amount according to each user from `transactions` table

### Subqueries in `FROM` clause

Used as a derived table ( or Common table experssion or CTE)

```sql
Select sender_id,total_amount
 From (
	Select sender_id, SUM(amount) as total_amount 
		From transactions
		Group By sender_id
 ) subquery
 Where total_amount > 100
 ;
```

- The subqueries calculate total amounts for each `sender_id` and check if `total_amount` is more than `100`.

### Subqueries in `WHERE` clause

```sql
Select id,song_name,artist_id From songs
	Where artist_id IN(
		Select id From artists
		Where name LIKE '%Arj%'	
	)
```

- This query returns song from `songs` table  matched by subquery with artist name `Arj` something from `artists` table.

<details>
<summary style="font-weight:bold;">subquery syntax</summary>
<p>
The only syntax unique  to a subquery is the parenthesis surrounding the nested query. 
</p>
<details>