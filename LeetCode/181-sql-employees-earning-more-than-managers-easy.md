# 181.SQL Employees Earning More Than Managers - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#3 - 181.SQL Employees Earning More Than Managers - Easy](https://github.com/lance-terminal/challenges/issues/3) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-07T20:53:50Z |
| **Closed** | 2026-02-08T03:42:01Z |

---

# [181. Employees Earning More Than Their Managers](https://leetcode.com/problems/employees-earning-more-than-their-managers/)

Table: `Employee`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| salary      | int     |
| managerId   | int     |
+-------------+---------+
```
id is the primary key (column with unique values) for this table.
Each row of this table indicates the ID of an employee, their name, salary, and the ID of their manager.

 
Write a solution to find the employees who earn more than their managers.
Return the result table in any order.
The result format is in the following example.
 



## Comments

---

**lance-terminal** — 2026-02-07T20:55:35Z

### SQL Solution

```SQL
select 
    e.name as Employee

from employee as e  -- represent e as employee table
left join employee as m on m.id = e.managerId  -- left join (self-join) the employee table to represent manager data (m)
where m.salary < e.salary -- look for higher than manager salary in employee salary data
```



---

**lance-terminal** — 2026-02-08T03:42:00Z

```SQL 
SELECT 
    emp.name as Employee

FROM employee emp
LEFT JOIN employee man ON emp.managerId = man.Id
WHERE emp.salary > man.salary
```
