Source: `LeetCode`
Category: `Data Structures`
Challenge: `Pandas`
Focus Area: `pd.DataFrame`

![[Pasted image 20260207125917.png]]

```Python
import pandas as pd # import Pandas library as pd
def createDataframe(student_data: List[List[int]]) -> pd.DataFrame: # input list of student data consisting of int and output a dataframe
	column_names = ['student_id', 'age'] # specify column names
	return pd.DataFrame(student_data, columns=column_names) # return the student raw data into dataframe using the columns specified in the variable above
```

