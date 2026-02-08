# 2877.Pandas Create a DataFrame from List - EASY

| Field | Detail |
|-------|--------|
| **Issue** | [#9 - 2877.Pandas Create a DataFrame from List - EASY](https://github.com/lance-terminal/challenges/issues/9) |
| **Author** | @lance-terminal |
| **Labels** | None |
| **Created** | 2026-02-08T03:44:41Z |
| **Closed** | 2026-02-08T03:54:06Z |

---

# [2877. Create a DataFrame from List](https://leetcode.com/problems/create-a-dataframe-from-list/)
Write a solution to create a DataFrame from a 2D list called student_data. This 2D list contains the IDs and ages of some students.
The DataFrame should have two columns, student_id and age, and be in the same order as the original 2D list.
The result format is in the following example.

Example 1:

Input:
student_data:

```SQL
[
  [1, 15],
  [2, 11],
  [3, 11],
  [4, 20]
]
```

Output:
```SQL
+------------+-----+
| student_id | age |
+------------+-----+
| 1          | 15  |
| 2          | 11  |
| 3          | 11  |
| 4          | 20  |
+------------+-----+
```
Explanation:
A DataFrame was created on top of student_data, with two columns named student_id and age.




## Comments

---

**lance-terminal** — 2026-02-08T03:45:06Z

```Python
import pandas as pd # import Pandas library as pd
def createDataframe(student_data: List[List[int]]) -> pd.DataFrame: # input list of student data consisting of int and output a dataframe
	column_names = ['student_id', 'age'] # specify column names
	return pd.DataFrame(student_data, columns=column_names) # return the student raw data into dataframe using the columns specified in the variable above
```
