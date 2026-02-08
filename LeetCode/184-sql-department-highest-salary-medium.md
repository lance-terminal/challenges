# 184.SQL Department Highest Salary - Medium

| Field | Detail |
|-------|--------|
| **Issue** | [#7 - 184.SQL Department Highest Salary - Medium](https://github.com/lance-terminal/challenges/issues/7) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-07T23:56:10Z |
| **Closed** | 2026-02-08T00:38:53Z |

---

# [184. Department Highest Salary](https://leetcode.com/problems/department-highest-salary/)

Table: `Employee`
```SQL
+--------------+---------+
| Column Name  | Type    |
+--------------+---------+
| id           | int     |
| name         | varchar |
| salary       | int     |
| departmentId | int     |
+--------------+---------+
```
`id` is the primary key (column with unique values) for this table.
`departmentId` is a foreign key (reference columns) of the ID from the Department table.

Each row of this table indicates the ID, name, and salary of an employee. It also contains the ID of their department.

Table: `Department`
```SQL
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
+-------------+---------+
`id` is the primary key (column with unique values) for this table. It is guaranteed that department name is not `NULL`.
Each row of this table indicates the ID of a department and its name.
```
Write a solution to find employees who have the highest salary in each of the departments.


## Comments

---

**lance-terminal** — 2026-02-08T00:08:18Z

```SQL
SELECT Department.Name AS Department, Employee.Name AS Employee, Salary
FROM Employee 
LEFT JOIN Department ON Employee.DepartmentId = Department.id
WHERE (DepartmentId, Salary) IN
(SELECT DepartmentId, MAX(Salary) as Salary FROM Employee
GROUP BY DepartmentId)
```

---

**lance-terminal** — 2026-02-08T00:11:45Z

Goal is to find highest paid in each department
Output needs `Department' name , `Employee`, and `Salary`



---

**lance-terminal** — 2026-02-08T00:19:28Z

### 1. Initial thought process
`departmentID` is foreign key that connects to Department table `id`
1. Get department to `LEFT JOIN` to find the department names in one table.
```SQL

SELECT d.name AS Department, e.name as Employee, e.salary as Salary
FROM Employee AS e
LEFT JOIN Department as d on e.departmentId = d.Id



Output
| Department | Employee | Salary |
| ---------- | -------- | ------ |
| IT         | Joe      | 70000  |
| IT         | Jim      | 90000  |
| Sales      | Henry    | 80000  |
| Sales      | Sam      | 60000  |
| IT         | Max      | 90000  |

Expected
| Department | Employee | Salary |
| ---------- | -------- | ------ |
| IT         | Jim      | 90000  |
| Sales      | Henry    | 80000  |
| IT         | Max      | 90000  |
```

---

**lance-terminal** — 2026-02-08T00:30:11Z

### 2. I am almost there
I need to group by the departments to find the highest paid there. Problem is Jim and Max has same department and same salary. Let me reference what I did before. I made a sub-query. 

Ok similar solution. I found this from `Loginov Kirill`
```SQL
SELECT d.name AS Department, e.name as Employee, e.salary as Salary
FROM Employee AS e
LEFT JOIN Department as d on e.departmentId = d.Id
WHERE e.salary = ( --- his query start
    SELECT MAX(salary)
    FROM Employee
    WHERE departmentId = e.departmentId
) -- his query end
```

---

**lance-terminal** — 2026-02-08T00:32:47Z

```SQL
SELECT d.name AS Department, e.name as Employee, e.salary as Salary
FROM Employee AS e
LEFT JOIN Department as d on e.departmentId = d.Id
```
Up to this I got there on my own

```SQL
WHERE e.salary = ( --- where the table matches Employee (represented by e in the following query result
    SELECT MAX(salary) --- select the max salary
    FROM Employee --- from Employee table
    WHERE departmentId = e.departmentId --- where the departmentId of the Employee table matches the departmentId of e
) 
```

This looks similar to for loop

---

**lance-terminal** — 2026-02-08T00:33:43Z

<img width="905" height="913" alt="Image" src="https://github.com/user-attachments/assets/2636324e-1ce8-4b2a-8f0c-e7cd12bd72b6" />
