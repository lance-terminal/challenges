# 595.Pandas Big Countries - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#24 - 595.Pandas Big Countries - Easy](https://github.com/lance-terminal/challenges/issues/24) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T23:32:38Z |
| **Closed** | 2026-02-09T00:05:59Z |

---

# [595. Big Countries](https://leetcode.com/problems/big-countries/)

Table: `World`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| name        | varchar |
| continent   | varchar |
| area        | int     |
| population  | int     |
| gdp         | bigint  |
+-------------+---------+
```
`name` is the primary key (column with unique values) for this table.
Each row of this table gives information about the name of a country, the continent to which it belongs, its area, the population, and its GDP value.

A country is big if:
    it has an area of at least three million (i.e., 3000000 km2), or
    it has a population of at least twenty-five million (i.e., 25000000).

Write a solution to find the name, population, and area of the big countries.
Return the result table in any order.
The result format is in the following example.

Example 1:

Input: 
`World` table:
```SQL
+-------------+-----------+---------+------------+--------------+
| name        | continent | area    | population | gdp          |
+-------------+-----------+---------+------------+--------------+
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |
+-------------+-----------+---------+------------+--------------+
```
Output: 
```SQL
+-------------+------------+---------+
| name        | population | area    |
+-------------+------------+---------+
| Afghanistan | 25500100   | 652230  |
| Algeria     | 37100000   | 2381741 |
+-------------+------------+---------+
```




## Comments

---

**lance-terminal** — 2026-02-09T00:05:29Z

```Python
import pandas as pd

def big_countries(world: pd.DataFrame) -> pd.DataFrame:
    countries = world[(world['area'] >= 3000000) | (world['population'] >= 25000000)]
    return countries[['name', 'population', 'area']]

```
