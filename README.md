# Supermarket Sales Analysis Report

This report presents a comprehensive analysis of supermarket sales data using Python. It includes data cleaning, exploration, and visualization to derive insights into customer behavior, product trends, and sales performance.

---

## 1. Introduction

The analysis aims to understand the key drivers of sales in a supermarket by exploring trends across different branches, product lines, customer types, and payment methods. Data was sourced from a CSV file and cleaned before analysis.

---

## 2. Data Loading and Overview

```python
import pandas as pd
df = pd.read_csv("/kaggle/input/supermarket-analysis-python/SuperMarket Analysis.csv")
print(df.head())
```

The dataset contains various fields including:
- Invoice ID
- Branch
- Customer Type
- Gender
- Product line
- Unit price
- Quantity
- Total
- Date
- Time
- Payment
- COGS
- Gross margin percentage
- Gross income
- Rating

---

## 3. Data Cleaning

```python
df.dropna(inplace=True)
df['Date'] = pd.to_datetime(df['Date'])
df['Quantity'] = pd.to_numeric(df['Quantity'], errors='coerce')
df['Unit price'] = pd.to_numeric(df['Unit price'], errors='coerce')
print(df.isnull().sum())
```

Missing values were removed. Date was converted to datetime format. Quantity and Unit price were ensured to be numeric.

---

## 4. Data Exploration

### Summary Statistics
```python
print(df.describe())
```

This helps understand the distribution of numerical values such as unit price, quantity, total sales, gross income, and ratings.

### Sales by Branch
```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.countplot(x='Branch', data=df)
plt.title("Number of Sales per Branch")
plt.show()
```

### Sales by Product Line
```python
sns.countplot(y='Product line', data=df, order=df['Product line'].value_counts().index)
plt.title("Sales by Product Line")
plt.show()
```

---

## 5. Insights and Trends

- **Branch B** had the highest number of sales.
- **Food and beverages** and **Fashion accessories** were the top-selling product lines.
- **Electronic accessories** showed high gross income.
- **Ewallet** and **Cash** were dominant payment methods.
- **Female** customers slightly outnumbered male customers in purchase count.

---

## 6. Visualizations

Several plots were used to identify key trends:

- Sales trends over time
- Product line-wise income
- Payment method distribution
- Customer ratings

These visualizations provided insight into customer preferences and purchasing patterns.

---

## 7. Conclusion

This analysis provided key insights into supermarket sales patterns. The data was effectively cleaned, analyzed, and visualized using Python, Pandas, and Seaborn. The findings can help inform stock decisions, promotional strategies, and customer engagement efforts.

---
