# 182.SQL Duplicate Emails - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#5 - 182.SQL Duplicate Emails - Easy](https://github.com/lance-terminal/challenges/issues/5) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-07T23:34:08Z |
| **Closed** | 2026-02-08T00:58:40Z |

---

# [182. Duplicate Emails](https://leetcode.com/problems/duplicate-emails/)

Table: `Person`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| email       | varchar |
+-------------+---------+
```
`id` is the primary key (column with unique values) for this table.
Each row of this table contains an email. The emails will not contain uppercase letters.

Write a solution to report all the duplicate emails. Note that it's guaranteed that the email field is not NULL.
Return the result table in any order.

The result format is in the following example.




## Comments

---

**lance-terminal** — 2026-02-08T00:43:31Z

```SQL
select
    distinct p1.Email
from Person p1 
join Person p2 on p1.Email = p2.Email AND p1.Id != p2.Id

```

---

**lance-terminal** — 2026-02-08T00:58:03Z

### SQL Solution 2

This is cleaner

```SQL
SELECT 
    email
FROM Person p1 
GROUP BY email
HAVING COUNT(email) > 1
```
