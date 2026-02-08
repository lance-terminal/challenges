# 2890.Pandas Reshape Data: Melt - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#22 - 2890.Pandas Reshape Data: Melt - Easy](https://github.com/lance-terminal/challenges/issues/22) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-08T17:29:51Z |
| **Closed** | 2026-02-08T17:32:13Z |

---

# [2890. Reshape Data: Melt](https://leetcode.com/problems/reshape-data-melt/)
DataFrame `report`
```SQL
+-------------+--------+
| Column Name | Type   |
+-------------+--------+
| product     | object |
| quarter_1   | int    |
| quarter_2   | int    |
| quarter_3   | int    |
| quarter_4   | int    |
+-------------+--------+
```
Write a solution to reshape the data so that each row represents sales data for a product in a specific quarter.
The result format is in the following example.

Example 1:
Input:
```SQL
+-------------+-----------+-----------+-----------+-----------+
| product     | quarter_1 | quarter_2 | quarter_3 | quarter_4 |
+-------------+-----------+-----------+-----------+-----------+
| Umbrella    | 417       | 224       | 379       | 611       |
| SleepingBag | 800       | 936       | 93        | 875       |
+-------------+-----------+-----------+-----------+-----------+
```
Output:
```SQL
+-------------+-----------+-------+
| product     | quarter   | sales |
+-------------+-----------+-------+
| Umbrella    | quarter_1 | 417   |
| SleepingBag | quarter_1 | 800   |
| Umbrella    | quarter_2 | 224   |
| SleepingBag | quarter_2 | 936   |
| Umbrella    | quarter_3 | 379   |
| SleepingBag | quarter_3 | 93    |
| Umbrella    | quarter_4 | 611   |
| SleepingBag | quarter_4 | 875   |
+-------------+-----------+-------+
```
Explanation:
The DataFrame is reshaped from wide to long format. Each row represents the sales of a product in a quarter.




## Comments

---

**lance-terminal** — 2026-02-08T17:32:02Z

### Overview
The problem involves reshaping a given DataFrame that captures sales data of products across different quarters. Initially, the data is structured in a wide format, where each product has separate columns for sales of every quarter. The task is to transform this data into a long format, where each row represents sales data for a specific product in a particular quarter, effectively consolidating the multiple quarter columns into two columns: one indicating the quarter and the other detailing the sales for that quarter.

Key Concepts:

    `melt` Function: pandas' melt function is used to transform or reshape data. It changes the DataFrame from a wide format, where columns represent multiple variables, to a long format, where each row represents a unique variable. In our case, we want to transform the sales data from having separate columns for each quarter to a format where there's a single column for the quarter and a single column for the sales value.

`melt` Function Argument Definition:

1. `id_vars`: This specifies the columns that should remain unchanged. For this problem, only the product column remains unchanged because we want every row in the output to be associated with a product.
2. `value_vars`: This specifies the columns that we want to "melt" or reshape into rows. In our case, these are the sales data columns for each quarter: quarter_1, quarter_2, quarter_3, and quarter_4.
3. `var_name`: This is the name of the new column that will store the header names from the value_vars. In our problem, these are the quarter names.
4. `value_name`: This is the name of the new column that will store the values from the value_vars. In our problem, this will be the sales figures for each product for each quarter.



```python
import pandas as pd

def meltTable(report: pd.DataFrame) -> pd.DataFrame:
    report = report.melt(
        id_vars=["product"], 
        value_vars=["quarter_1", "quarter_2", "quarter_3", "quarter_4"],
        var_name="quarter",
        value_name='sales',
    )
    return report
```
