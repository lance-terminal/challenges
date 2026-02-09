# 1757.Pandas Recyclable and Low Fat Products - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#25 - 1757.Pandas Recyclable and Low Fat Products - Easy](https://github.com/lance-terminal/challenges/issues/25) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-09T03:07:01Z |
| **Closed** | 2026-02-09T03:15:46Z |

---

# [1757. Recyclable and Low Fat Products](https://leetcode.com/problems/recyclable-and-low-fat-products/)

Table: `Products`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| product_id  | int     |
| low_fats    | enum    |
| recyclable  | enum    |
+-------------+---------+
```
`product_id` is the primary key (column with unique values) for this table.
`low_fats` is an ENUM (category) of type ('Y', 'N') where 'Y' means this product is low fat and 'N' means it is not.
recyclable is an ENUM (category) of types ('Y', 'N') where 'Y' means this product is recyclable and 'N' means it is not.

Write a solution to find the ids of products that are both low fat and recyclable.
Return the result table in any order.
The result format is in the following example.

Example 1:

Input: 
`Products` table:
```SQL
+-------------+----------+------------+
| product_id  | low_fats | recyclable |
+-------------+----------+------------+
| 0           | Y        | N          |
| 1           | Y        | Y          |
| 2           | N        | Y          |
| 3           | Y        | Y          |
| 4           | N        | N          |
+-------------+----------+------------+
```
Output: 
```SQL
+-------------+
| product_id  |
+-------------+
| 1           |
| 3           |
+-------------+
```
Explanation: Only products 1 and 3 are both low fat and recyclable.




## Comments

---

**lance-terminal** — 2026-02-09T03:15:33Z

```python
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    filtered_products = products[(products['low_fats'] == 'Y') & (products['recyclable'] == 'Y')]
    return filtered_products[['product_id']]
```
