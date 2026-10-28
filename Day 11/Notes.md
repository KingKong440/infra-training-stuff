# Data Cleaning and Preprocessing: A Beginner's Guide

## Introduction

Before analyzing data, it's almost always necessary to clean and prepare it. Raw data often contains errors, inconsistencies, and missing values that can lead to incorrect conclusions. This guide will walk you through the essential steps of data cleaning and preprocessing using **pandas**, a powerful Python library for data manipulation.

Think of data cleaning like preparing ingredients for cooking: you wash, chop, and measure them before starting your recipe. Similarly, you clean and format your data before performing any analysis.

---

## 1. Data Quality: Common Problems

Real-world data is rarely perfect. Here are the most common issues you'll encounter:

### Missing Values
Some data points are not recorded. For example, a customer might forget to enter their age.

**How to handle missing values:**
- **Fill with a value**: Replace missing data with a specific number (e.g., 0).
- **Use mean or median**: Fill missing values with the average (mean) or middle value (median) of that column. This works well when data is evenly distributed or has outliers.
- **Remove the record**: Delete the entire row if it has missing values. Do this only if the missing data is minimal and won't affect your analysis.
- **Create a missing value indicator**: Add a new column (e.g., `age_missing`) that shows 1 if the value was missing and 0 otherwise. This helps your model understand that the missingness might be meaningful.

### Duplicate Records
The same data entry appears multiple times. For example, a customer might have two identical orders due to a system error.

**Solution**: Use `drop_duplicates()` to remove duplicate rows.

### Inconsistent Data
Data is recorded in different formats. For example, a city might be written as "New York", "NY", or "new york".

**Solution**: Standardize text using methods like `str.strip()` (remove extra spaces) and `str.title()` (capitalize first letter of each word).

### Incorrect Data Types
A column containing numbers might be stored as text (e.g., "100" instead of 100). This prevents mathematical operations.

**Solution**: Convert data types using `pd.to_numeric()` or `pd.to_datetime()`.

### Outliers
Values that are extremely different from others in the same column. For example, a person's income might be $5,000,000 when most others earn $50,000.

**Solution**: Identify outliers using the IQR method (explained later) and decide whether to remove, cap, or keep them.

### Invalid Values
Data that doesn't make sense. For example, a negative age or an email without "@".

**Solution**: Filter out or correct invalid entries based on domain knowledge.

---

## 2. Data Formatting and Type Conversion

### Common Data Types
- **int**: Whole numbers (e.g., 1, 2, 3)
- **float**: Decimal numbers (e.g., 1.5, 3.14)
- **object/string**: Text (e.g., "hello", "New York")
- **datetime**: Dates and times (e.g., 2023-10-05)

### Key Pandas Functions for Inspection

Before making changes, explore your data:

```python
# Show the first few rows
df.head()

# Get the shape (number of rows and columns)
df.shape

# List all column names
df.columns

# Show data types and non-null counts
df.info()

# Get summary statistics
df.describe()
```

### Converting Data Types

**To numeric**:
```python
# Convert to numeric, invalid values become NaN
df["Quantity"] = pd.to_numeric(df["Quantity"], errors="coerce")
```

**To datetime**:
```python
df["Date"] = pd.to_datetime(df["Date"])
```

---

## 3. Data Transformation and Feature Engineering

**Feature engineering** is creating new meaningful columns from existing ones. For example:
- Extract year from a date
- Create age from birth date
- Combine first and last name into full name

Use the `apply()` function to apply custom transformations:
```python
# Example: Create a "full_name" column
df["full_name"] = df["first_name"] + " " + df["last_name"]
```

---

## 4. Essential Pandas Functions for Data Cleaning

Here are the most commonly used pandas functions:

### Checking for Missing Values
```python
# Check for missing values
df.isnull()  # or df.isna()
df.isnull().sum()  # Count missing values per column
```

### Handling Missing Values
```python
# Remove rows with missing values
df.dropna()

# Fill missing values
df.fillna(0)  # Replace with 0
df.fillna(df["column"].mean())  # Replace with mean
df.fillna(df["column"].median())  # Replace with median
```

### Handling Duplicates
```python
# Check for duplicates
df.duplicated()

# Remove duplicates
df.drop_duplicates()
```

### Text Cleaning
```python
# Remove extra spaces and standardize capitalization
df["column"] = df["column"].str.strip().str.title()
```

### Outlier Detection Using IQR

The IQR method helps identify outliers:
1. **IQR** = Q3 - Q1 (Interquartile Range)
2. **Lower Bound** = Q1 - 1.5 × IQR
3. **Upper Bound** = Q3 + 1.5 × IQR
4. Any value outside these bounds is considered an outlier.

**Example**:
```python
Q1 = df["UnitPrice"].quantile(0.25)
Q3 = df["UnitPrice"].quantile(0.75)
IQR = Q3 - Q1
lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

# Filter out outliers
df = df[(df["UnitPrice"] >= lower_bound) & (df["UnitPrice"] <= upper_bound)]
```

### Visualizing Outliers
```python
df["UnitPrice"].plot(kind="box")
```

---

## 5. Putting It All Together: A Step-by-Step Workflow

1. **Inspect your data**: Use `head()`, `info()`, `describe()` to understand its structure.
2. **Check for missing values**: Use `isnull().sum()` and decide how to handle them.
3. **Remove duplicates**: Use `drop_duplicates()`.
4. **Fix data types**: Convert columns to correct types using `pd.to_numeric()` or `pd.to_datetime()`.
5. **Clean text data**: Use `str.strip()`, `str.title()` to standardize.
6. **Handle outliers**: Use the IQR method to identify and decide what to do with them.
7. **Transform data**: Create new features using `apply()` if needed.
8. **Save cleaned data**: Use `to_csv()` to export your cleaned dataset.

---

## Summary

Data cleaning is a critical step in any data analysis project. The key concepts are:
- **Identify problems**: Missing values, duplicates, incorrect types, outliers.
- **Handle missing values**: Fill, remove, or create indicators.
- **Clean text**: Standardize formatting.
- **Convert types**: Ensure data is in the right format for analysis.
- **Detect outliers**: Use the IQR method.
- **Transform data**: Create new features to improve analysis.

By following these steps, you'll transform raw, messy data into a clean, reliable dataset ready for analysis.
