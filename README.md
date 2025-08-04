# task1-data-cleaning
# Task 1: Data Cleaning and Preprocessing

## 🧹 Cleaning Performed:

- Filled missing values in `addressline2`, `state`, `territory`, and `postalcode` using group-based mode.
- Removed duplicate rows using `drop_duplicates()`.
- Standardized all column names to lowercase and snake_case.
- Standardized string columns by stripping and lowering text.
- Converted `orderdate` to consistent `datetime` format.
- Verified and corrected data types for columns.

## 💾 Output:
- Cleaned dataset: `cleaned_sales_data.csv`
- Code file: `sales_data_cleaning.ipynb`

## 🔧 Tools Used:
- Python 3
- Pandas
- Jupyter Notebook


