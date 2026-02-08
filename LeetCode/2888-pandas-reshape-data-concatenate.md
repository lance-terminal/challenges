# 2888.Pandas Reshape Data: Concatenate

| Field | Detail |
|-------|--------|
| **Issue** | [#20 - 2888.Pandas Reshape Data: Concatenate](https://github.com/lance-terminal/challenges/issues/20) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T16:19:35Z |
| **Closed** | 2026-02-08T16:19:57Z |

---

# [2888. Reshape Data: Concatenate](https://leetcode.com/problems/reshape-data-concatenate/)

DataFrame `df1`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| student_id  | int    |
| name        | object |
| age         | int    |
+-------------+--------+
```

DataFrame `df2`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| student_id  | int    |
| name        | object |
| age         | int    |
+-------------+--------+
```
Write a solution to concatenate these two DataFrames vertically into one DataFrame.
The result format is in the following example.

Example 1:
Input:
`df1`
```SQL
+------------+---------+-----+
| student_id | name    | age |
+------------+---------+-----+
| 1          | Mason   | 8   |
| 2          | Ava     | 6   |
| 3          | Taylor  | 15  |
| 4          | Georgia | 17  |
+------------+---------+-----+
```
`df2`
```SQL
+------------+------+-----+
| student_id | name | age |
+------------+------+-----+
| 5          | Leo  | 7   |
| 6          | Alex | 7   |
+------------+------+-----+
```
Output:
```SQL
+------------+---------+-----+
| student_id | name    | age |
+------------+---------+-----+
| 1          | Mason   | 8   |
| 2          | Ava     | 6   |
| 3          | Taylor  | 15  |
| 4          | Georgia | 17  |
| 5          | Leo     | 7   |
| 6          | Alex    | 7   |
+------------+---------+-----+
```
Explanation:
The two DataFrames are stacked vertically, and their rows are combined.




## Comments

---

**lance-terminal** — 2026-02-08T16:19:46Z

```python
import pandas as pd

def concatenateTables(df1: pd.DataFrame, df2: pd.DataFrame) -> pd.DataFrame:
    return pd.concat([df1,df2])
```
