# 183.SQL Customer Who Never Order - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#6 - 183.SQL Customer Who Never Order - Easy](https://github.com/lance-terminal/challenges/issues/6) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-07T23:54:40Z |
| **Closed** | 2026-02-08T03:37:30Z |

---

# [183. Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/)

Table: `Customers`
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
+-------------+---------+
`id` is the primary key (column with unique values) for this table.
Each row of this table indicates the ID and name of a customer.

Table: `Orders`
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| customerId  | int  |
+-------------+------+

`id` is the primary key (column with unique values) for this table.
customerId is a foreign key (reference columns) of the ID from the Customers table.
Each row of this table indicates the ID of an order and the ID of the customer who ordered it. 

Write a solution to find all customers who never order anything.




## Comments

---

**lance-terminal** — 2026-02-08T03:26:22Z

```SQL
SELECT
    name AS Customers
FROM customers
WHERE Id NOT IN (SELECT CustomerId FROM Orders)
```
