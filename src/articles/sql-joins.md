---
title: Understanding how SQL joins work
description: A practical guide to joining relational tables, understanding join types, and retrieving meaningful information from databases.
category: SQL · DATABASES
readingTime: 10
articleType: Learning Notes
---

## Why do joins exist?

Relational databases store information in tables. Instead of repeating every detail in a single table, we often separate information into related tables.

For example, one table might store customers, while another stores their orders. A `JOIN` lets us combine information from these tables using a related column.

Without joins, we would often need to duplicate customer details in every order record. This creates unnecessary repetition and makes data harder to maintain.

## Meet our tables

Imagine we have these two tables.

### Customers

| customer_id | name |
|---:|---|
| 1 | Alice |
| 2 | Bob |
| 3 | Charlie |

### Orders

| order_id | customer_id | product |
|---:|---:|---|
| 101 | 1 | Laptop |
| 102 | 2 | Phone |
| 103 | 1 | Keyboard |

Notice that Alice has two orders, Bob has one, and Charlie has none. The `customer_id` column connects the two tables.

## INNER JOIN

An `INNER JOIN` returns only rows that have matching values in both tables.

```sql
SELECT
    customers.name,
    orders.product
FROM customers
INNER JOIN orders
    ON customers.customer_id = orders.customer_id;
