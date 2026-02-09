# 183.Pandas Customers Who Never Order - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#26 - 183.Pandas Customers Who Never Order - Easy](https://github.com/lance-terminal/challenges/issues/26) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-09T03:19:03Z |
| **Closed** | 2026-02-09T14:50:42Z |

---

# [183. Customers Who Never Order](https://leetcode.com/problems/customers-who-never-order/)

Table: `Customers`

+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
+-------------+---------+
`id` is the primary key (column with unique values) for this table.
Each row of this table indicates the ID and name of a customer.

Table: `Orders`
```SQL
+-------------+------+
| Column Name | Type |
+-------------+------+
| id          | int  |
| customerId  | int  |
+-------------+------+
```
`id` is the primary key (column with unique values) for this table.
customerId is a foreign key (reference columns) of the ID from the Customers table.
Each row of this table indicates the ID of an order and the ID of the customer who ordered it.

Write a solution to find all customers who never order anything.
Return the result table in any order.
The result format is in the following example.


Example 1:

Input: 
`Customers` table:
```SQL
+----+-------+
| id | name  |
+----+-------+
| 1  | Joe   |
| 2  | Henry |
| 3  | Sam   |
| 4  | Max   |
+----+-------+
```
Orders table:
```SQL
+----+------------+
| id | customerId |
+----+------------+
| 1  | 3          |
| 2  | 1          |
+----+------------+
```
Output: 
```SQL
+-----------+
| Customers |
+-----------+
| Henry     |
| Max       |
+-----------+
```
 


## Comments

---

**lance-terminal** — 2026-02-09T14:44:21Z

Joins with Pandas
We use a left join on `customers` because we want to include all customers from it, regardless of whether they place an order or not.
Therefore, by using left join, we can preserve all the rows from the left table (`customers`) and match them with corresponding rows from the right table (`orders`) based on `id` and `customerID`, separately.

df = customers.merge(orders, left_on='id', right_on='customerId', how='left')

### Solution with `LEFT JOIN`
```Python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers.merge(orders, left_on='id', right_on='customerId', how='left')
    df = df[df['customerId'].isna()]
    return df[['name']].rename(columns={'name': 'Customers'})
```

---

**lance-terminal** — 2026-02-09T14:45:12Z

### LeetCode Solution
```Python
import pandas as pd

def customers_who_never_order(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers.merge(orders, left_on='id', right_on='customerId', how='left')
    df = df[df['customerId'].isna()]
    df = df[['name']].rename(columns={'name': 'Customers'})
    return df

```

---

**lance-terminal** — 2026-02-09T14:46:06Z

### Solution with Exclusion Criteria
```Python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    # Select the rows which `id` is not present in orders['customerId'].
    df = customers[~customers['id'].isin(orders['customerId'])]

    # Build a dataframe that only contains the column `name` 
    # and rename the column `name` as `Customers`.
    df = df[['name']].rename(columns={'name': 'Customers'})
    return df
```

---

**lance-terminal** — 2026-02-09T14:50:31Z

`~` used as negation statement
```Python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:
    df = customers[~customers['id'].isin(orders['customerId'])]
    return df[['name']].rename(columns={'name': 'Customers'})
```
