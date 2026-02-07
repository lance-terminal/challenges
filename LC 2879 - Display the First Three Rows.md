Source: `LeetCode`
Category: `Data Inspection`
Challenge: `Pandas`
Focus Area: `.head`

![[Pasted image 20260207141135.png]]

```python
import pandas as pd
def selectFirstRows(employees: pd.DataFrame) -> pd.DataFrame:
	return employees.head(3) # show top 3
```

**`employees.head(3)`**
- `.head()` = "give me rows from the top"
- `.tail()` = "gives me rows from the bottom"
- `(3)` = "I want 3 rows"
- Returns a new DataFrame with only those rows
- Default is 5 if you don't specify a number