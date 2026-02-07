Source: `LeetCode`
Category: `Data Inspection`
Challenge: `Pandas`
Focus Area: `.shape`

![[Pasted image 20260207140656.png]]

```python
import pandas as pd
def getDataframeSize(players: pd.DataFrame) -> List[int]:
	return [players.shape[0], players.shape[1]] # return calculated rows and columns 
```


**`players.shape[0]`**
- `.shape` gives you the dimensions: `(rows, columns)`
- `[0]` grabs the first number = number of rows
- If you have 5 players, this returns `5`

**`players.shape[1]`**
- `[1]` grabs the second number = number of columns
- If you track name, age, team, this returns `3`

**`return [players.shape[0], players.shape[1]]`**
- Packages both numbers into a list: `[5, 3]`