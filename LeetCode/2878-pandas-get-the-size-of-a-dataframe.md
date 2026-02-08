# 2878.Pandas Get the Size of a DataFrame

| Field | Detail |
|-------|--------|
| **Issue** | [#10 - 2878.Pandas Get the Size of a DataFrame](https://github.com/lance-terminal/challenges/issues/10) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T03:55:54Z |
| **Closed** | 2026-02-08T03:58:30Z |

---

# [2878. Get the Size of a DataFrame](https://leetcode.com/problems/get-the-size-of-a-dataframe/)

DataFrame `players`:
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| player_id   | int    |
| name        | object |
| age         | int    |
| position    | object |
| ...         | ...    |
+-------------+--------+
```
Write a solution to calculate and display the number of rows and columns of players.
Return the result as an array:
[number of rows, number of columns]
The result format is in the following example.


## Comments

---

**lance-terminal** — 2026-02-08T03:57:57Z

```Python
import pandas as pd
def getDataframeSize(players: pd.DataFrame) -> List[int]:
    return [players.shape[0], players.shape[1]]
```
.shape[0] = rows
.shape[1] = columns
