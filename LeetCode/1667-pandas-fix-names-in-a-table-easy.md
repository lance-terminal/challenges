# 1667.Pandas Fix Names in a Table - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#39 - 1667.Pandas Fix Names in a Table - Easy](https://github.com/lance-terminal/challenges/issues/39) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-10T15:28:29Z |
| **Closed** | 2026-02-10T15:29:23Z |

---

# [1667. Fix Names in a Table](https://leetcode.com/problems/fix-names-in-a-table/)

Table: `Users`
```SQL
+----------------+---------+
| Column Name    | Type    |
+----------------+---------+
| user_id        | int     |
| name           | varchar |
+----------------+---------+
```
`user_id` is the primary key (column with unique values) for this table.
This table contains the ID and the name of the user. The name consists of only lowercase and uppercase characters.


Write a solution to fix the names so that only the first character is uppercase and the rest are lowercase.
Return the result table ordered by `user_id`.
The result format is in the following example.

Example 1:

Input: 
`Users` table:
```SQL
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | aLice |
| 2       | bOB   |
+---------+-------+
```
Output: 
```SQL
+---------+-------+
| user_id | name  |
+---------+-------+
| 1       | Alice |
| 2       | Bob   |
+---------+-------+
```



## Comments

---

**lance-terminal** — 2026-02-10T15:29:08Z

```Python
import pandas as pd

def fix_names(users: pd.DataFrame) -> pd.DataFrame:
    users["name"] = users["name"].str.capitalize()
    return users.sort_values("user_id")

```
[`pandas.Series.str.upper`](https://pandas.pydata.org/docs/reference/api/pandas.Series.str.upper.html)
