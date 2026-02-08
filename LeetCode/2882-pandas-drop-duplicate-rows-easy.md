# 2882.Pandas Drop Duplicate Rows - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#14 - 2882.Pandas Drop Duplicate Rows - Easy](https://github.com/lance-terminal/challenges/issues/14) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:37:26Z |
| **Closed** | 2026-02-08T15:32:44Z |

---

# [2882. Drop Duplicate Rows](https://leetcode.com/problems/drop-duplicate-rows/)

DataFrame `customers`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| customer_id | int    |
| name        | object |
| email       | object |
+-------------+--------+
```
There are some duplicate rows in the DataFrame based on the email column.
Write a solution to remove these duplicate rows and keep only the first occurrence.
The result format is in the following example.
 
Example 1:
Input:
```SQL
+-------------+---------+---------------------+
| customer_id | name    | email               |
+-------------+---------+---------------------+
| 1           | Ella    | emily@example.com   |
| 2           | David   | michael@example.com |
| 3           | Zachary | sarah@example.com   |
| 4           | Alice   | john@example.com    |
| 5           | Finn    | john@example.com    |
| 6           | Violet  | alice@example.com   |
+-------------+---------+---------------------+
```
Output:
```SQL  
+-------------+---------+---------------------+
| customer_id | name    | email               |
+-------------+---------+---------------------+
| 1           | Ella    | emily@example.com   |
| 2           | David   | michael@example.com |
| 3           | Zachary | sarah@example.com   |
| 4           | Alice   | john@example.com    |
| 6           | Violet  | alice@example.com   |
+-------------+---------+---------------------+
```
Explanation:
Alic (customer_id = 4) and Finn (customer_id = 5) both use john@example.com, so only the first occurrence of this email is retained.




## Comments

---

**lance-terminal** — 2026-02-08T15:32:42Z

```Python
import pandas as pd
def dropDuplicateEmails(customers: pd.DataFrame) -> pd.DataFrame:
    return customers.drop_duplicates(subset=["email"])
```
