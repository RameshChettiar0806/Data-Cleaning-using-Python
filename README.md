# Data Cleaning Using Python

This repository contains dataset-specific cleaning notebooks and the cleaned outputs they generate. Each dataset is kept in its own folder so the raw data, notebook, and cleaned files stay together.

## Repository Structure

- `AirBNB Dataset/`
- `Netflix Dataset/`
- `Sales Dataset/`
- `Zomato Dataset/`


## AirBnB Dataset

Source: [Kaggle - Airbnb Open Data](https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata)

Notebook used: [AirBNB Dataset/data cleaning and preprocessing/airbnb_cleaning.ipynb](AirBNB%20Dataset/data%20cleaning%20and%20preprocessing/airbnb_cleaning.ipynb)

What the notebook does:

- Imports the required Python libraries and checks package versions.
- Loads the raw CSV file from `raw-dataset/Airbnb_Open_Data.csv`.
- Reviews the dataset shape, columns, and sample rows.
- Standardizes column names to a consistent format.
- Drops columns that are not needed for the cleaned analysis file.
- Removes duplicate rows.
- Removes rows with missing values.
- Normalizes selected text fields such as host verification and cancellation policy.
- Resets the index and preserves the original row index as a column.
- Cleans currency fields by removing `$` and commas, then converts them to numeric values.
- Standardizes the last review date format.
- Exports the cleaned dataset to `Cleaned_Dataset.csv`.

## Sales Dataset

Source: [Onurbltc/SalesData](https://github.com/Onurbltc/SalesData/tree/main)

Notebook used: [Sales Dataset/data_cleaning/sales_cleaning.ipynb](Sales%20Dataset/data_cleaning/sales_cleaning.ipynb)

What the notebook does:

- Imports the required Python libraries and checks package versions.
- Loads the raw CSV file from `raw dataset/sales.csv`.
- Inspects the dataset using `info()`, column listing, and sample records.
- Cleans the `Transaction ID` field by removing the `TXN_` prefix and converting it to a numeric value.
- Removes rows with missing values.
- Filters out invalid placeholder values such as `UNKNOWN` and `ERROR`.
- Converts `Price Per Unit` and `Total Spent` to floating-point values.
- Converts `Quantity` to an integer value.
- Converts `Transaction Date` to a proper datetime type.
- Sorts the dataset by transaction date and resets the index.
- Exports the cleaned dataset to `Cleaned_Dataset.csv`.
- Exports the cleaned dataset to `Cleaned_Dataset.xlsx` and auto-fits the Excel column widths.

## Zomato Dataset

Source: [Kaggle - Zomato Dataset](https://www.kaggle.com/datasets/rishikeshkonapure/zomato)

Notebook used: [Zomato Dataset/data_cleaning_and_preprocessing/cleaning__dataset.ipynb](Zomato%20Dataset/data_cleaning_and_preprocessing/cleaning__dataset.ipynb)

What the notebook does:

- Imports the required Python libraries and checks package versions.
- Loads the raw CSV file from `Zomato Dataset/raw_dataset/zomato.csv`.
- Inspects the dataset using `head()`, `shape`, `columns`, `info()`, and value counts.
- Keeps only the columns needed for the cleaned output.
- Renames the selected columns to a cleaner display format.
- Removes duplicate rows.
- Converts the online order and table booking flags to binary values.
- Cleans the rating field by handling placeholders and formatting the text.
- Resets the index before dropping remaining missing values.
- Removes missing values.
- Cleans the cost column by removing commas and converting it to integers.
- Exports the cleaned dataset to CSV and Excel.
- The exported files currently include the default pandas index column.

Documentation: [Zomato Dataset/documentation/Zomato Dataset.md](Zomato%20Dataset/documentation/Zomato%20Dataset.md)

## Netflix Dataset

Source: [To be added]

What the notebook does:

- Loads the raw CSV file from `raw_dataset/netflix1.csv`.
- Inspects the dataset using `sample()` and `columns`
- Keeps only the columns needed for the cleaned output.
- Capitalizes column names.
- Removes duplicate rows.
- Replaces values "Not Given" with NaN.
- Drops rows with NaN values.
- Sorts the dataset by `Release_year` and `Duration`.
- Resets the index and preserves the original row index as a column.
- Exports the cleaned dataset to `Cleaned_Dataset.csv` and `Cleaned Netflix Dataset.xlsx`.



## Notes

- If a cleaned Excel file shows `#####` in a column, widen the column before exporting or after saving.
