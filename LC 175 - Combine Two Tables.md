![[Pasted image 20260207014629.png]]
### Personal Notes

### SQL
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
### Pandas (python)

