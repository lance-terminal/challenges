# 2887.Pandas Fill Missing Data - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#19 - 2887.Pandas Fill Missing Data - Easy](https://github.com/lance-terminal/challenges/issues/19) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T16:01:54Z |
| **Closed** | 2026-02-08T16:15:07Z |

---

# [2887. Fill Missing Data](https://leetcode.com/problems/fill-missing-data/)

DataFrame `products`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| name        | object |
| quantity    | int    |
| price       | int    |
+-------------+--------+
```
Write a solution to fill in the missing value as 0 in the quantity column.
The result format is in the following example.

Example 1:
```SQL
Input:+-----------------+----------+-------+
| name            | quantity | price |
+-----------------+----------+-------+
| Wristwatch      | None     | 135   |
| WirelessEarbuds | None     | 821   |
| GolfClubs       | 779      | 9319  |
| Printer         | 849      | 3051  |
+-----------------+----------+-------+
```
Output:
```SQL
+-----------------+----------+-------+
| name            | quantity | price |
+-----------------+----------+-------+
| Wristwatch      | 0        | 135   |
| WirelessEarbuds | 0        | 821   |
| GolfClubs       | 779      | 9319  |
| Printer         | 849      | 3051  |
+-----------------+----------+-------+
```
Explanation: 
The quantity for Wristwatch and WirelessEarbuds are filled by 0.




## Comments

---

**lance-terminal** — 2026-02-08T16:14:53Z

```python
import pandas as pd

def fillMissingValues(products: pd.DataFrame) -> pd.DataFrame:
    products["quantity"] = products["quantity"].fillna(0)
    return products

# fillna
```
#15 
