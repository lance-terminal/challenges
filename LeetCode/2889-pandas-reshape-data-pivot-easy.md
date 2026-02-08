# 2889.Pandas Reshape Data: Pivot - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#21 - 2889.Pandas Reshape Data: Pivot - Easy](https://github.com/lance-terminal/challenges/issues/21) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T16:23:21Z |
| **Closed** | 2026-02-08T17:27:16Z |

---

# [2889. Reshape Data: Pivot](https://leetcode.com/problems/reshape-data-pivot/)
DataFrame `weather`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| city        | object |
| month       | object |
| temperature | int    |
+-------------+--------+
```
Write a solution to pivot the data so that each row represents temperatures for a specific month, and each city is a separate column.
The result format is in the following example.

Example 1:
Input:
```SQL
+--------------+----------+-------------+
| city         | month    | temperature |
+--------------+----------+-------------+
| Jacksonville | January  | 13          |
| Jacksonville | February | 23          |
| Jacksonville | March    | 38          |
| Jacksonville | April    | 5           |
| Jacksonville | May      | 34          |
| ElPaso       | January  | 20          |
| ElPaso       | February | 6           |
| ElPaso       | March    | 26          |
| ElPaso       | April    | 2           |
| ElPaso       | May      | 43          |
+--------------+----------+-------------+
```
Output:
```SQL
+----------+--------+--------------+
| month    | ElPaso | Jacksonville |
+----------+--------+--------------+
| April    | 2      | 5            |
| February | 6      | 23           |
| January  | 20     | 13           |
| March    | 26     | 38           |
| May      | 43     | 34           |
+----------+--------+--------------+
```
Explanation:
The table is pivoted, each column represents a city, and each row represents a specific month.




## Comments

---

**lance-terminal** — 2026-02-08T16:34:18Z

https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.pivot.html
```python
df.pivot(index='foo', columns='bar')['baz']

bar  A   B   C
foo
one  1   2   3
two  4   5   6

```

---

**lance-terminal** — 2026-02-08T16:37:52Z

```python
import pandas as pd

def pivotTable(weather: pd.DataFrame) -> pd.DataFrame:
    return weather.pivot(index='month', columns='city',)['temperature']
    
```
