---
title: "normalization"
draft: false
---

tag: #sql #relationship #queries
## Table Relationships

Relational database is powerful because it allows relations between tables. This relationships helps us to keep our database clean and efficient.A relationship between tables assumes that, A `table` which contain `foreign key` reference it to another table's `primary key`.

**Types of relationships**

1. One to One
2. One to Many
3. Many to Many

### One to One

A `one-to-one` relationship links a single row to single crossponding row in another table which is acheived by defining `foreign key` with a unique constraint to ensure exclusivity. 

```sql
CREATE TABLE users(
	userId Serial PRIMARY KEY,
	name VARCHAR(100) NOT NULL
);

CREATE TABLE user_profiles(
	profileID Serial PRIMARY KEY,
	userId INT UNIQUE NOT NULL,
	bio TEXT,
	FOREIGN KEY (userId) REFERENCES users(userId)
);
```

- This query will create two tables named `users` and `user_profiles`, table users's column `userId` which is `Primary Key` will be referenced to table user_profiles's column `userId` with the help of `Foreign key`.

### One to Many

A `one-to-many` relationship occurs when a single record have relationship with many records in another table. 

```sql
CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    amount INTEGER NOT NULL,
    customer_id INTEGER,
    CONSTRAINT fk_customers FOREIGN KEY (customer_id) REFERENCES customers(id)
);
```


> one->many relationship goes only one way a record in second table cannot be related to multiple record in the first place.


### Many to Many

A many to many relationship occurs when multiple records in one table have relationships with multiple records in another table.

Example,

- A `products` table and `suppliers` table - A product may have 0 to many suppliers and a supplier can have 0 to many products.

#### Joining table

Joining table help define many-to-many relationships between data in database. As an example when defining the relationships between table products and suppliers, we would define a joining table called product_suppliers that contains the primary key and table to be joined.

##### Unique constraint across two fields.

When enforcing specific schema we many need to enforce the `UNIQUE` constraint across different fields.

```sql
Create Table product_suppliers(
	product_id INT,
	supplier_id INT,
	UNIQUE(product_id,supplier_id)
);
```

- This lets multiple rows share the same `product_id` or `supplier_id`, but it prevents from have same row have same `product_id` and `supplier_id`. 



## Database Normalization

Database Normalization is a method that structure your database schema such way that:

1. Improve data integrity.
2. Reduct Data redundancy.

- **Data Integrity :** Data integrity refers to the accuracy and cosistency of data. 
- **Data Redundancy :** Data redundancy occurs when same piece of data stored in multiple places.

### Normal Forms

The creator of "database normalization",Edger F.Codd described different "normal forms" a database can adhere to.  

-Common used normal forms 

- First normal form(1NF)
- Second normal form(2NF)
- third normal form(3NF)
- Boyce-Codd normal form(BC-NF)

In short 1NF is least normalized and boyce-codd one is most normalized.

* The more normalized a database, the better its data integrity, and less duplicate data we'll have.

#### Third normal form (3NF)

- First two normal form is also about data integrity but not that elaborate and efficient.

Third form brings new rule:-

- All column that are not part of primary key are solely dependent on primary key.

#### Boyce-Codd Normal form (BCNF)

BCNF form brings new rule:-

- A column that's part of the primary key can not be entirely dependent on a column that's not part of the primary key.


----
### Rule of thumb for database design

1. Every table must have unique identifier (primary key)
2. 90% the unique identifier will be column id
3. Avoid duplicate data
4. Avoid storing data that is completely dependent on other data. Instead, compute it on the fly.
5. Keep your schema as simple as you can