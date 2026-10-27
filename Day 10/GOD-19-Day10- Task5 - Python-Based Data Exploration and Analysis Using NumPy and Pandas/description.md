# GOD-19: Day10| Task5 | Python-Based Data Exploration and Analysis Using NumPy and Pandas

- **Jira:** https://sudhaharrajeshkannan.atlassian.net/browse/GOD-19
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Sujitha M
- **Created:** 2026-10-26T10:29:18.663Z
- **Updated:** 2026-10-26T12:43:01.428Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

1. NumPy – 1D Array Operations

- Array Creation: np.array()
- Array Dimensions: arr.ndim
- Array Shape: arr.shape
- Total Elements: arr.size
- Data Type: arr.dtype
- Sum: np.sum(arr)
- Average: np.mean(arr)
- Minimum: np.min(arr)
- Maximum: np.max(arr)
- Array Manipulation: Increase all values by 10%.
- Array Filtering: Filter values greater than 2,000.
2. NumPy – 2D Array Operations

- 2D Array Creation: np.array()
- Array Dimensions: arr.ndim
- Array Shape: arr.shape
- Total Elements: arr.size
- Data Type: arr.dtype
- Sum of All Elements: np.sum(arr)
- Sum of Each Row: np.sum(arr, axis=1)
- Sum of Each Column: np.sum(arr, axis=0)
- Average: np.mean(arr)
- Minimum and Maximum: np.min(arr), np.max(arr)
- Indexing and Slicing: Access specific elements, rows, and columns.
3. Pandas – DataFrame Exploration

- Load Dataset: pd.read_csv()
- First Five Rows: df.head()
- First Three Rows: df.head(3)
- Last Five Rows: df.tail()
- Dataset Dimensions: df.shape
- Column Names: df.columns
- Data Types and Non-Null Counts: df.info()
- Descriptive Statistics: df.describe()
- Descriptive Statistics for All Columns: df.describe(include='all')
- Missing Values: df.isnull()
- Count Missing Values: df.isnull().sum()
- Duplicate Records: df.duplicated()
- Count Duplicate Records: df.duplicated().sum()
4. Pandas – Create a Column

- Create a new column using existing columns.
- Calculate revenue using quantity and price.
- Example formula: df['Revenue'] = df['Quantity'] * df['Price']
5. Pandas – Filtering

- Filter rows using a single condition.
- Filter records where revenue is greater than 2,000.
- Filter using multiple conditions, such as a specific city and a minimum number of orders.
6. Pandas – Categorization

- Categorize products or records based on specified conditions.
- Create categories such as High, Medium, and Low revenue.
- Use conditional logic or pd.cut() for categorization.
7. Pandas – Overall Statistics

- Total: df.sum(numeric_only=True)
- Average: df.mean(numeric_only=True)
- Minimum: df.min(numeric_only=True)
- Maximum: df.max(numeric_only=True)
- Count: df.count()
- Statistical Summary: df.describe()
- Total Revenue: df['Revenue'].sum()
- Average Revenue: df['Revenue'].mean()
- Revenue by City: df.groupby('City')['Revenue'].sum()
Expected Outcome:

Understand NumPy 1D and 2D array operations, explore datasets using Pandas, inspect data quality, create new columns, filter and categorize records, and calculate overall statistics from a sales dataset.

## Attachments

- [elden_ring_classes.csv](attachments/elden_ring_classes.csv)
- [numpy-pandas-task.ipynb](attachments/numpy-pandas-task.ipynb)
