# Zomato Dataset - Data Cleaning and Preprocessing Documentation

## Dataset Source
- Kaggle: [Zomato Dataset](https://www.kaggle.com/datasets/rishikeshkonapure/zomato)
- Raw file used in notebook: `../raw_dataset/zomato.csv`

## Notebook File
- `data_cleaning_and_preprocessing/cleaning__dataset.ipynb`

## Output Files
- `data_cleaning_and_preprocessing/Cleaned_Dataset.csv`
- `data_cleaning_and_preprocessing/Zomato_Dataset.xlsx`

## Python Packages Used
```python
import pandas as pd
import numpy as np
import openpyxl

print(f"NumPy Version --> {np.__version__}")
print(f"Pandas Version --> {pd.__version__}")
print(f"openpyxl Version --> {openpyxl.__version__}")
```

## End-to-End Cleaning Workflow

### 1) Load Raw Data
```python
data = pd.read_csv("../raw_dataset/zomato.csv")
```

### 2) Initial Exploration
The notebook inspects the dataset using:
- `data.head(5)`

![data.head](../images/data.head().png)
- `data.shape`

- `data.columns`

![data.shape](../images/data.columns().png)

- `data.info()`

![data.info](../images/data.info().png)

- `data["menu_item"].value_counts()`

This step confirms structure, data types, and candidate columns for cleaning.

### 3) Keep Only Required Columns
```python
columns_to_keep = [
    "name",
    "online_order",
    "book_table",
    "rate",
    "location",
    "approx_cost(for two people)",
]
data = data[columns_to_keep]
```

### 4) Rename Columns
The notebook generates cleaned column names by capitalizing each existing column name:
```python
columns_to_rename = []
for i in data.columns:
    columns_to_rename.append(i.capitalize())

data.columns = columns_to_rename
```

Resulting columns:
- `Name`
- `Online_order`
- `Book_table`
- `Rate`
- `Location`
- `Approx_cost(for two people)`

### 5) Remove Duplicate Rows
```python
data.drop_duplicates(inplace=True)
```

### 6) Clean Yes/No Flags into Binary Values
```python
data["Online_order"] = data["Online_order"].apply(lambda x: 1 if x == "Yes" else 0)
data["Book_table"] = data["Book_table"].apply(lambda x: 1 if x == "Yes" else 0)
```

### 7) Clean Rate Column
```python
data["Rate"] = data["Rate"].replace(["NEW", "-"], np.nan)
data["Rate"] = data["Rate"].str.replace("/", " out of ")
```

This converts non-rating placeholders to missing values and formats ratings like `4.1/5` to `4.1 out of 5`.

### 8) Reset Index
```python
data.reset_index(drop=True, inplace=True)
```

### 9) Remove Missing Values
```python
data.dropna(inplace=True)
```

### 10) Clean Cost Column Type
```python
data["Approx_cost(for two people)"] = data["Approx_cost(for two people)"] \
    .astype(str) \
    .str.replace(",", "")
data["Approx_cost(for two people)"] = data["Approx_cost(for two people)"].astype(int)
```

This removes comma separators and converts the column to integer values.

### 11) Export Clean Dataset
```python
data.to_csv("Cleaned_Dataset.csv")
data.to_excel("Zomato_Dataset.xlsx")
```

## Final Dataset Description
The cleaned dataset contains:
- Restaurant name
- Online ordering availability (`1`/`0`)
- Table booking availability (`1`/`0`)
- Formatted rating text
- Location
- Approximate cost for two people as integer

## Notes
- Exports currently include a default index column from pandas.
- If desired, exports can be changed to omit index using `index=False`.
