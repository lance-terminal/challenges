# 1527.Pandas Patients With a Condition

| Field | Detail |
|-------|--------|
| **Issue** | [#41 - 1527.Pandas Patients With a Condition](https://github.com/lance-terminal/challenges/issues/41) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-12T15:08:04Z |
| **Closed** | 2026-02-12T15:09:22Z |

---

# [1527. Patients With a Condition](https://leetcode.com/problems/patients-with-a-condition/)

Table: `Patients`
```SQL
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| patient_id   | int     |
| patient_name | varchar |
| conditions   | varchar |
+--------------+---------+
```
`patient_id` is the primary key (column with unique values) for this table.
'conditions' contains 0 or more code separated by spaces. 
This table contains information of the patients in the hospital.

Write a solution to find the patient_id, patient_name, and conditions of the patients who have Type I Diabetes. Type I Diabetes always starts with `DIAB1` prefix.

Return the result table in any order.
The result format is in the following example.

Example 1:

Input: 
`Patients` table:
```SQL
+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        |              |
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |
| 5          | Alain        | DIAB201      |
+------------+--------------+--------------+
```
Output: 
```SQL
+------------+--------------+--------------+
| patient_id | patient_name | conditions   |
+------------+--------------+--------------+
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 | 
+------------+--------------+--------------+
```
Explanation: Bob and George both have a condition that starts with DIAB1.


## Comments

---

**lance-terminal** — 2026-02-12T15:09:10Z

```Python
import pandas as pd

def find_patients(patients: pd.DataFrame) -> pd.DataFrame:
    return patients[patients["conditions"].str.contains(r"(^|\s)DIAB1")]
```

The regex `(^|\s)DIAB1` matches "DIAB1" only when it appears:

`^` - at the start of the string, OR
`\s` - after a whitespace character
