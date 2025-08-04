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

###Interview Questions Related To Above Task:
###1. What are missing values and how do you handle them?
Missing values are empty or null entries in your dataset — places where data is incomplete or not available. In Pandas, they are typically represented as NaN.

How to handle missing values:
Remove them: Use dropna() to remove rows or columns with missing values.

Impute them:

Mean/median/mode: df['col'].fillna(df['col'].mean())

Forward fill: df.fillna(method='ffill')

Backward fill: df.fillna(method='bfill')

Use interpolation: For time series or continuous data.

Flag them: Create a new column indicating missingness.

2. How do you treat duplicate records?
Duplicate records are rows that appear more than once in the dataset.

#How to handle:
##Check for duplicates:
df.duplicated()

##Remove duplicates:
df.drop_duplicates(inplace=True)
###You can also use:
df.drop_duplicates(subset=['column1', 'column2'])
To remove duplicates based on specific columns.

3. Difference between dropna() and fillna() in Pandas?
| Feature  | `dropna()`                      | `fillna()`                                    |
| -------- | ------------------------------- | --------------------------------------------- |
| Action   | Removes missing values          | Replaces missing values                       |
| Result   | Shorter dataset                 | Same size dataset                             |
| Use when | Missing data is not recoverable | You want to retain rows with estimates        |
| Example  | `df.dropna()`                   | `df.fillna(0)` or `df.fillna(method='ffill')` |



4. What is outlier treatment and why is it important?
Outliers are extreme values that differ significantly from the rest of the data. They can skew analysis and affect model performance.

Why treat them?
Can distort statistical summaries (mean, std)

Affect ML model accuracy

Outlier treatment methods:
Remove them: Use IQR or Z-score techniques.

Cap them: Limit them to a max/min threshold.

Transform them: Use log, sqrt, or Box-Cox transformations.

Impute them: Replace with median or nearest valid value.


5. Explain the process of standardizing data.
Standardization (or Z-score normalization) scales data to have:

Mean = 0

Standard deviation = 1

Why?
Some ML algorithms (like SVM, KNN, PCA) are sensitive to scale.

How to standardize:
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df_scaled = scaler.fit_transform(df[['feature1', 'feature2']])



6. How do you handle inconsistent data formats (e.g., date/time)?
Inconsistent formats cause parsing issues and affect analysis.

Steps to handle:
Use pd.to_datetime():
df['date'] = pd.to_datetime(df['date'], errors='coerce')
Unify format explicitly using format=...

Clean symbols or noise using str.replace()

Check types:

df.dtypes


7. What are common data cleaning challenges?
Missing values

Duplicates

Inconsistent formats (dates, casing, currencies)

Invalid entries (e.g., negative sales)

Outliers

Data type mismatches

Encoding issues (especially with text data)

Merged columns or multi-level headers

8. How can you check data quality?
9. | Check                   | Method/Function in Pandas                                           |
| ----------------------- | ------------------------------------------------------------------- |
| **Missing values**      | `df.isnull().sum()`                                                 |
| **Duplicates**          | `df.duplicated().sum()`                                             |
| **Inconsistent types**  | `df.dtypes`                                                         |
| **Unique values**       | `df['col'].nunique()`                                               |
| **Value ranges**        | `df.describe()`                                                     |
| **Invalid entries**     | Use filters like `df[df['age'] < 0]`                                |
| **Date parsing errors** | `pd.to_datetime(..., errors='coerce')`                              |
| **Schema validation**   | Use libraries like `pandera` or `great_expectations` for data rules |


