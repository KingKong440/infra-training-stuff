# GOD-32: Day11 | Task3 | E-Commerce Data Cleaning and Preprocessing

- **Jira:** https://sudhaharrajeshkannan.atlassian.net/browse/GOD-32
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-27T11:00:54.279Z
- **Updated:** 2026-10-27T12:43:10.194Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Select a unique e-commerce dataset from a public source and perform basic data cleaning and preprocessing using Python and Pandas. Identify data quality issues, clean the dataset, and perform simple business analysis.

Tasks and Commands

1. Select and Inspect a Dataset

- Download a unique e-commerce dataset from Kaggle, UCI, or GitHub.
- Load the dataset and inspect its structure.

```
import pandas as pd

df = pd.read_csv("ecommerce.csv")

print(df.head())
print(df.shape)
print(df.info())
```

2. Identify Missing Values

- Find missing values in every column.
- Count missing values and handle them appropriately.

```
print(df.isnull().sum())
print(df.isnull().sum() / len(df) * 100)

# Remove rows with missing values, if appropriate
df = df.dropna()
```

3. Identify and Remove Duplicate Orders

- Find repeated order IDs.
- Check whether they represent actual duplicates or legitimate items belonging to the same order.
- Remove only confirmed duplicate records.

```
print(df["OrderID"].duplicated().sum())

# Remove exact duplicate rows
df = df.drop_duplicates()
```

Replace OrderID with the actual order ID column name in your dataset.

4. Find the Highest-Priced Product

- Identify the product with the highest valid unit price.
- Display its name and price.

```
print(df.loc[df["UnitPrice"].idxmax()])
```

5. Calculate Revenue by City

- Calculate revenue using quantity multiplied by unit price.
- Group revenue by city and identify the highest-revenue city.

```
df["Revenue"] = df["Quantity"] * df["UnitPrice"]

city_revenue = df.groupby("City")["Revenue"].sum()

print(city_revenue.sort_values(ascending=False))
```

6. Identify Possible Causes and Solutions

Document the possible causes and solutions for the following issues:

- Missing values — incomplete data entry or failed imports.
- Duplicate records — repeated uploads or transactions.
- Invalid prices — data entry errors or incorrect formats.
- Inconsistent city names — spelling differences or inconsistent formatting.
Suggest a suitable solution for each issue.

## Attachments

- [task-3-causes-solutions.xlsx](attachments/task-3-causes-solutions.xlsx)
- [task-3-ecommerce.csv](attachments/task-3-ecommerce.csv)
- [task-3-ecommerce.ipynb](attachments/task-3-ecommerce.ipynb)
