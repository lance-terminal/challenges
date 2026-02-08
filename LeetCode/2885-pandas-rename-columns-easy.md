# 2885.Pandas Rename Columns - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#17 - 2885.Pandas Rename Columns - Easy](https://github.com/lance-terminal/challenges/issues/17) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T04:44:55Z |
| **Closed** | 2026-02-08T15:54:59Z |

---

# [2885. Rename Columns](https://leetcode.com/problems/rename-columns/)

DataFrame `students`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| id          | int    |
| first       | object |
| last        | object |
| age         | int    |
+-------------+--------+
```
Write a solution to rename the columns as follows:
- id to student_id
- first to first_name
- last to last_name
- age to age_in_years

The result format is in the following example.

Example 1:
Input:
```SQL
+----+---------+----------+-----+
| id | first   | last     | age |
+----+---------+----------+-----+
| 1  | Mason   | King     | 6   |
| 2  | Ava     | Wright   | 7   |
| 3  | Taylor  | Hall     | 16  |
| 4  | Georgia | Thompson | 18  |
| 5  | Thomas  | Moore    | 10  |
+----+---------+----------+-----+
```
Output:
```SQL
+------------+------------+-----------+--------------+
| student_id | first_name | last_name | age_in_years |
+------------+------------+-----------+--------------+
| 1          | Mason      | King      | 6            |
| 2          | Ava        | Wright    | 7            |
| 3          | Taylor     | Hall      | 16           |
| 4          | Georgia    | Thompson  | 18           |
| 5          | Thomas     | Moore     | 10           |
+------------+------------+-----------+--------------+
```
Explanation: 
The column names are changed accordingly.




## Comments

---

**lance-terminal** — 2026-02-08T15:52:17Z

```python
# pandas documentation
>>> df = pd.DataFrame({"A": [1, 2, 3], "B": [4, 5, 6]})
>>> df.rename(columns={"A": "a", "B": "c"})
   a  c
0  1  4
1  2  5
2  3  6
```

---

**lance-terminal** — 2026-02-08T15:54:21Z

```python
import pandas as pd

def renameColumns(students: pd.DataFrame) -> pd.DataFrame:
    return students.rename(columns={"id": "student_id", "first": "first_name", "last": "last_name", "age": "age_in_years"})
