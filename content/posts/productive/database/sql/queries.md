---
title: "queries"
draft: false
---


Tag: #sql #query
# Basic Sql Queries

SQL supports a wide range of quries to manage, retrieve and manipulate data in a database. 

## 1. Data Retrieval (SELECT)

**Basic Query:**

```sql
Select * From table_name;
```

- This query retrieve every column from table.

**Specific Column:**

```sql
SELECT column1,column2 FROM table_name WHERE condtion;

-- example, Select name,id From users WHERE  id = 2
```

**Ordering Results:**

```sql
Select * From table_name Order By column_name (ASC|DESC);
```

**Limit Results:**

```sql
Select * From table_name LIMIT n;
```

## 2. Data Manipulation (Insert,Update,Delete)

**Insert Data:**

```sql
INSERT INTO table_name (column1,column2) Values (value1,value2);
```

**Update Data:**

```sql
UPDATE table_name SET column = value1 WHERE condtion;
```

**Delete Data:**

```sql
Delete FROM table_name Where condtion;
```








