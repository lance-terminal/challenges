# 1148.Pandas Article Views I - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#27 - 1148.Pandas Article Views I - Easy](https://github.com/lance-terminal/challenges/issues/27) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-09T18:45:27Z |
| **Closed** | 2026-02-09T19:40:57Z |

---

Table: `Views`
```SQL
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| article_id    | int     |
| author_id     | int     |
| viewer_id     | int     |
| view_date     | date    |
+---------------+---------+
```

There is no primary key (column with unique values) for this table, the table may have duplicate rows.
Each row of this table indicates that some viewer viewed an article (written by some author) on some date. 
Note that equal author_id and viewer_id indicate the same person.
 

Write a solution to find all the authors that viewed at least one of their own articles.
Return the result table sorted by `id` in ascending order.
The result format is in the following example.

Example 1:

Input: 
`Views` table:
```SQL
+------------+-----------+-----------+------------+
| article_id | author_id | viewer_id | view_date  |
+------------+-----------+-----------+------------+
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |
+------------+-----------+-----------+------------+
```
Output: 
```SQL
+------+
| id   |
+------+
| 4    |
| 7    |
+------+
```



## Comments

---

**lance-terminal** — 2026-02-09T19:39:20Z

```python
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:
    df = views[views['author_id'] == views['viewer_id']] # find where author_id is equal viewer_id and set that equal new DataFrame
    df.drop_duplicates(subset=['author_id'], inplace=True) # drop duplicates of author_id
    df.sort_values(by=['author_id'], inplace=True) # sort the values in author_id
    df.rename(columns={'author_id':'id'}, inplace=True) # rename the column from author id to id
    return df[['id']] # return just that column

```

Approach: Selecting rows based on conditions
