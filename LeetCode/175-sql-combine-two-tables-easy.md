# 175.SQL Combine Two Tables - Easy

| Field | Detail |
|-------|--------|
| **Issue** | [#2 - 175.SQL Combine Two Tables - Easy](https://github.com/lance-terminal/challenges/issues/2) |
| **Author** | @lance-terminal |
| **Labels** | LeetCode |
| **Created** | 2026-02-07T20:48:19Z |
| **Closed** | 2026-02-08T00:06:53Z |

---

# [175. Combine Two Tables](https://leetcode.com/problems/combine-two-tables/)

Table: `Person`
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| personId    | int     |
| lastName    | varchar |
| firstName   | varchar |
+-------------+---------+
personId is the primary key (column with unique values) for this table.
This table contains information about the ID of some persons and their first and last names.

 

Table: `Address`
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| addressId   | int     |
| personId    | int     |
| city        | varchar |
| state       | varchar |
+-------------+---------+
addressId is the primary key (column with unique values) for this table.
Each row of this table contains information about the city and state of one person with ID = PersonId.

 

Write a solution to report the first name, last name, city, and state of each person in the Person table. If the address of a personId is not present in the Address table, report null instead.


## Comments

---

**lance-terminal** — 2026-02-07T20:50:51Z

### SQL Solution
```SQL
SELECT
	p.firstName AS firstName, -- column A: firstName
	p.lastName AS lastName, -- column B: lastName
	a.city AS city, -- column C: city
	a.state AS state -- column D: state
FROM Person p -- represent p for table:Person
LEFT JOIN Address a ON p.personId = a.personId 
-- left join where person ID in table:Person (p) is the same as person ID in table:address (a)
```
