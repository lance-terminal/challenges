# 2883.Pandas Drop Missing Data - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#15 - 2883.Pandas Drop Missing Data - Easy](https://github.com/lance-terminal/challenges/issues/15) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:38:52Z |
| **Closed** | 2026-02-08T15:39:32Z |

---

# [2883. Drop Missing Data](https://leetcode.com/problems/drop-missing-data/)

DataFrame `students`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| student_id  | int    |
| name        | object |
| age         | int    |
+-------------+--------+
```
There are some rows having missing values in the name column.
Write a solution to remove the rows with missing values.
The result format is in the following example.

Example 1:

Input:
```SQL
+------------+---------+-----+
| student_id | name    | age |
+------------+---------+-----+
| 32         | Piper   | 5   |
| 217        | None    | 19  |
| 779        | Georgia | 20  |
| 849        | Willow  | 14  |
+------------+---------+-----+
```
Output:
```SQL
+------------+---------+-----+
| student_id | name    | age |
+------------+---------+-----+
| 32         | Piper   | 5   |
| 779        | Georgia | 20  | 
| 849        | Willow  | 14  | 
+------------+---------+-----+
```
Explanation: 
Student with id 217 havs empty value in the name column, so it will be removed.




## Comments

---

**lance-terminal** — 2026-02-08T15:38:40Z

```python
import pandas as pd

def dropMissingData(students: pd.DataFrame) -> pd.DataFrame:
    return students.dropna(subset=["name"])
```

---

**lance-terminal** — 2026-02-08T15:39:30Z

[pandas.DataFrame.dropna](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html)
