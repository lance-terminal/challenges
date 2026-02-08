# 2886.Pandas Change Data Type - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#18 - 2886.Pandas Change Data Type - Easy](https://github.com/lance-terminal/challenges/issues/18) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T15:56:16Z |
| **Closed** | 2026-02-08T16:00:07Z |

---

DataFrame `students`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| student_id  | int    |
| name        | object |
| age         | int    |
| grade       | float  |
+-------------+--------+
```
Write a solution to correct the errors:
The grade column is stored as floats, convert it to integers.
The result format is in the following example.

Example 1:
Input:
DataFrame `students`:
```SQL
+------------+------+-----+-------+
| student_id | name | age | grade |
+------------+------+-----+-------+
| 1          | Ava  | 6   | 73.0  |
| 2          | Kate | 15  | 87.0  |
+------------+------+-----+-------+
```
Output:
```SQL
+------------+------+-----+-------+
| student_id | name | age | grade |
+------------+------+-----+-------+
| 1          | Ava  | 6   | 73    |
| 2          | Kate | 15  | 87    |
+------------+------+-----+-------+
```
Explanation: 
The data types of the column grade is converted to int.




## Comments

---

**lance-terminal** — 2026-02-08T15:58:40Z

```python
import pandas as pd
def changeDatatype(students: pd.DataFrame) -> pd.DataFrame:
    students = students.astype({'grade': int})
    return students
```

---

**lance-terminal** — 2026-02-08T15:59:50Z

###### Key Concepts
`DataFrame`: a 2D table-like structure, similar to a spreadsheet or SQL table. Each row represents an individual record and each column represents a different attribute. It is size-mutable and designed to handle a mix of different types of data.
    
`astype` Function: The `astype` function is used to cast a pandas object to a specified `dtype` (data type). `astype` can be used to cast a pandas object to any `dtype`. The `astype` function does not modify the original DataFrame in place. Instead, it returns a new DataFrame with the specified data type changes. If you want to reflect changes in the original DataFrame, you need to reassign the result back to it or use the copy parameter accordingly. The function’s syntax is:
```python
ataFrame.astype(dtype, copy=True, errors='raise')
```
