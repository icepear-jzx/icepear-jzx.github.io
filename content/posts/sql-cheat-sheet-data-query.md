---
date: '2024-10-20T03:03:22-07:00'
draft: true
title: 'SQL Cheat Sheet - Data Query'
tags: [SQL]
---

This article covers basic SQL syntax along with advanced features, such as window functions, for data query (DQL).
These concepts are frequently applied to solve common algorithmic challenges.

# Basic Syntax

## SELECT

`SELECT` is used to retrieve data from one or more tables.

Select specific columns:

```mysql
SELECT column1, column2, ... FROM table_name;
```

Select all columns:

```mysql
SELECT * FROM table_name;
```

Rename columns in the result using `AS`:

```mysql
SELECT column_name AS new_column_name FROM table_name;
```

## FROM

`FROM` specifies the table from which to retrieve the data.

Select data from a single table:

```mysql
SELECT * FROM table_name;
```

Select data from multiple tables:

```mysql
SELECT * FROM table1, table2;
```

This will create a Cartesian product (a.k.a. [`CROSS JOIN`](#cross-join)), meaning every row from `table1` will be paired with every row from `table2`.

> Note: The Cartesian product is rarely used intentionally in real-world queries because it can result in a very large result set, especially for large tables.
> It's generally better to use `JOIN` if there's a logical connection between the tables.

# Filtering

## WHERE

`WHERE` is used to filter records that meet certain conditions.

```mysql
SELECT * FROM table_name
WHERE conditions;
```

The `conditions` can be a single comparison, such as `salary > 100`, or a combination of conditions using logical operators, like `salary > 100 AND department = 'IT'`.
Please refer to the [Operators](#operators) section for additional options.

## HAVING

`HAVING` is used to filter the result set after after applying [aggregate functions](#aggregate-functions).

```mysql
SELECT column1, aggregate_expression, ...
FROM table_name
GROUP BY column1
HAVING aggregate_conditions;
```

The `column1` in `SELECT` and `GROUP BY` must match. It indicates the dimension used to group records.

The `aggregate_expression` is an expression that applies aggregate functions, such as `COUNT(*)`.
There can be multiple aggregate expressions in one `SELECT`.

The `aggregate_conditions` is a conditional expression that involves aggregate functions, such as `COUNT(*) > 1`.

> Note: `HAVING` is always used with aggregate functions and comes after `GROUP BY`.
> In contrast, `WHERE` is used before `GROUP BY` and does not include any aggregate functions.

# Sorting & Limiting

## ORDER BY

`ORDER BY` is used to sort the result set by one or more columns, either in ascending or descending order.

```mysql
SELECT * FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC];
```

You can also use aggregate functions when it's used with `GROUP BY`:

```mysql
SELECT column1, ... FROM table_name
GROUP BY column1
ORDER BY aggregate_expression [ASC|DESC];
```

## LIMIT

`LIMIT` is used to restrict the number of rows returned in the result set.

```mysql
SELECT * FROM table_name
LIMIT number_of_rows;
```

## OFFSET

`OFFSET` is used to skip a specified number of rows before starting to return rows from the result set.
It must be used together with `LIMIT`.

```mysql
SELECT * FROM table_name
LIMIT number_of_rows OFFSET skip_rows;
```

# Joining

## INNER JOIN

## LEFT / RIGHT JOIN

## FULL JOIN

## CROSS JOIN

## SELF JOIN

# Grouping & Aggregation

## GROUP BY

## Aggregate Functions

### COUNT

### SUM / AVG

### MIN / MAX

# Subqueries

# Window Functions

## Basic Syntax

### PARTITION BY

### ORDER BY

### ROWS

### RANGE

## ROW_NUMBER / RANK / DENSE_RANK

## LAG / LEAD

## NTILE

# Set Operations

## UNION

## INTERSECT

## EXCEPT

# Conditional Expressions

## CASE

## COALESCE

## NULLIF

## IF

## Boolean Expressions

## GREATEST / LEAST

## Conditional Aggregates

# Operators

## Arithmetic Operators

## Comparison Operators

## Logical Operators

## String Operators

# Miscellaneous Functions

## String Functions

## Date/Time Functions

## Numeric Functions

# Common Table Expressions
