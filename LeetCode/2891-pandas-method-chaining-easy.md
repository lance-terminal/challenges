# 2891.Pandas Method Chaining - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#23 - 2891.Pandas Method Chaining - Easy](https://github.com/lance-terminal/challenges/issues/23) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T17:39:25Z |
| **Closed** | 2026-02-08T17:45:56Z |

---

# [2891. Method Chaining](https://leetcode.com/problems/method-chaining/)

DataFrame `animals`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| name        | object |
| species     | object |
| age         | int    |
| weight      | int    |
+-------------+--------+
```
Write a solution to list the names of animals that weigh strictly more than 100 kilograms.
Return the animals sorted by weight in descending order.
The result format is in the following example.

Example 1:
Input: 
DataFrame `animals`:
```SQL
+----------+---------+-----+--------+
| name     | species | age | weight |
+----------+---------+-----+--------+
| Tatiana  | Snake   | 98  | 464    |
| Khaled   | Giraffe | 50  | 41     |
| Alex     | Leopard | 6   | 328    |
| Jonathan | Monkey  | 45  | 463    |
| Stefan   | Bear    | 100 | 50     |
| Tommy    | Panda   | 26  | 349    |
+----------+---------+-----+--------+
```
Output:
```SQL 
+----------+
| name     |
+----------+
| Tatiana  |
| Jonathan |
| Tommy    |
| Alex     |
+----------+
```
Explanation: 
All animals weighing more than 100 should be included in the results table.
Tatiana's weight is 464, Jonathan's weight is 463, Tommy's weight is 349, and Alex's weight is 328.
The results should be sorted in descending order of weight.


## Comments

---

**lance-terminal** — 2026-02-08T17:45:24Z

```Python
import pandas as pd

def findHeavyAnimals(animals: pd.DataFrame) -> pd.DataFrame:
    filtered_animals = animals[animals['weight'] > 100]
    sorted_animals = filtered_animals.sort_values(by='weight', ascending=False)

    return sorted_animals[['name']]

```

---

**lance-terminal** — 2026-02-08T17:45:53Z

https://leetcode.com/problems/method-chaining/editorial/#solution
