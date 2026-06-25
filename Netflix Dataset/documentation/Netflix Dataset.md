# Cleaning Netflix Dataset 


## Dataset Source
Kaggle: [Zomato Dataset](https://www.kaggle.com/datasets/ariyoomotade/netflix-data-cleaning-analysis-and-visualization/code)
Raw Dataset imported from kaagle: `raw_dataset\netflix1.csv`

## Notebook File
Python Notebook: `zomato_dataset_cleaning.ipynb`

## Output Files
`Cleaned Netflix Dataset.xlsx`
`Cleaned_Dataset.csv`


## Python Packages Used
```python 
import pandas as pd
import numpy as np
import openpyxl 
  

print(f"NumPy Version --> {np.__version__}")
print(f"Pandas Version --> {pd.__version__}")
print(f"openpyxl Version --> {openpyxl.__version__}")
```

## End-to-end Cleaning Workflow
### 1) Loading Raw Dataset
```python
df = pd.read_csv("raw_dataset/netflix1.csv")
```

### 2) Exploring Dataset
Exploring the dataset using the following pandas commands:
1. df.sample![[Pasted image 20260625001356.png|450]]
2. df.columns
	![[Pasted image 20260625001425.png|442]]


### 3) Removing Redundant Columns
```python
columns_to_drop = ['show_id','date_added','listed_in']
df.drop(columns = columns_to_drop,inplace = True)
```
Using:
==df.shape==
to compare and verify changes made to the dataset

### 4) Renaming Columns
Using loops to capitalize each and every column of the dataset and neatly updating them :
```python
columns_renamed = []
for i in df.columns:
    columns_renamed.append(i.capitalize())

df.columns = columns_renamed
```

`df.columns:`
1. Type
2. Title
3. Director
4. Country
5. Release_year
6. Rating 
7. Duration

### 5) Removing Duplicate Values in the Dataset
```python
df.drop_duplicates(inplace = True)
```

### 6) Replacing "Not Given" with NaN
```python
df["Country"] = df["Country"].replace("Not Given",np.nan)
df["Director"] = df["Director"].replace("Not Given",np.nan)
```

### 7) Dropping NaN from the dataset
```python
df.dropna(inplace = True)
```

### 8) Resetting Index to maintain uniformity and readability
```python
df.sort_values(["Release_year","Duration"],inplace = True)
df.reset_index(drop = True)
```


### 9) Exporting Cleaned Dataset
```python
df.to_csv("Cleaned_Dataset.csv")
df.to_excel("Cleaned Netflix Dataset.xlsx",index = False)
```


## Final Dataset Description
The Cleaned Netflix Dataset contains:
- Type
- Title
- Director
- Country
- Year of Release
- Rating
- Duration
Sorted the entire dataset by ==Year of Release==. In case of same Year of Release, sorting by ==Duration==

