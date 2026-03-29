---
title: "aggregations"
draft: false
---

# Aggregations

aggregations is 'single value' that's derived by combining several other value. Like when we use `COUNT` to count the total rows of particular column or whole table we basically perform aggregation.

#### Why aggregations?

Data stored in database generally stored in raw form. When we need to calculate additional data from that raw data we use an aggregation.

for ex,

```sql
Select COUNT(*) from users;
```

- This query will fetch count of total rows in table `users`.


### SUM

The `SUM` aggregation function returns the sum of set of values.

```sql
Select SUM(salary) from employees;
```

- This query fetch total `SUM` of `salary` column from the table `employees`.

### MAX

The `MAX` as the name suggest, this aggregate function returns max number in set of values.

```sql
Select MAX(amount) from transactions;
```

- This query fetch `MAX` amount from the column `amount`.

#### MIN

The `MIN` function return the minimum number in set of values.

```sql
Select min(amount) Where transactions;
```

- 
#### GROUP BY

- There are times when we need to group data based on specific values.

SQL offers `GROUP BY` clause that can group rows that have similar values to "summary" rows.

```sql
Select  user_id,sum(amount) as Balance from transactions Group By use_id;
```

- 

#### AVG - Average

By using `AVG` clause of SQL we can fin Average of set of values. 

```sql
Select AVG(amount) From Transactions;
```

- This query will return average on all rows of `amount`.

#### Having 

When we need to filter the result of `Group By` even further, we can use the `HAVING` clause. The `Having` Clause specifies a search condition for a group.

The `Having` clause is similar to `Where` cluase, but the difference is that `Having` clause works on colums that are created using `Group By`.

example,

```sql
Select album_id,Count(id) AS count
	From songs
	Group By album_id
	Having count > 5 ;
```

- This query returns the count of all distinct ids where count is more than 5.

<details open>
<summary>Having vs Where in SQL</summary>
<p>Developers can get confused between <code>Having</code> & <code>Where</code> clause - they're pretty similiar after all.</p>

<p>The difference is fairly simple:-</p>

<ul>
<li>A <code>WHERE</code> condition is applied to all the data in a query before it's grouped by <code>GROUP BY</code> clause.</li>
<li>A <code>HAVING</code> condition is only applied to the grouped rows that returned after a <code>GROUP BY</code> applied.</li>
</ul>

<p>This means that if you want to filter based on the result of using aggregation function. you need to use <code>HAVING</code> clause and vice-versa.</p>
</details>

#### ROUND

Sometimes we need to round up some numbers, particularly when working with aggregation,so we can use `ROUND()` clause
The SQL round function allows you to specify both the value you wish to round and the precision to which you wish to round it.

`ROUND(value,precision)`

- If no precision is given, SQL will round the value to it's nearest whole value:

```sql
 SELECT song_name,ROUND(avg(song_length),1)
	From songs
	Group By song_name
;	 
```

- This query return avg of `song_length` from the `songs` table, rounded to single decimal point.







