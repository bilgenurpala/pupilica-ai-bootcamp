# 01 — Data Science Fundamentals

<div align="center">

[![Data Science Fundamentals](../assets/data_science_banner.png)](../README.md)

</div>

> My notes from the first week of the Pupilica AI Bootcamp.
> Instructor's repo: [turkiyeyapayzekaakademisi/veri-bilimi](https://github.com/turkiyeyapayzekaakademisi/veri-bilimi)

---

## What's in this folder

| File / Resource | Action / Type | Description |
|:---|:---|:---|
| `Data_Science_Training.ipynb` | [![Notebook](https://img.shields.io/badge/Jupyter-Notebook-blue?logo=jupyter&style=flat-square)](./Data_Science_Training.ipynb) | Instructor's notebook — contains data science workflow walkthroughs and comments |
| `../assets/data_science_training_flowchart.svg` | [View Image](../assets/data_science_training_flowchart.svg) | 17-module data science learning path flowchart |
| `e_commerce_dataset.csv` | [![Raw Dataset](https://img.shields.io/badge/CSV-Raw-lightgrey?logo=pandas&style=flat-square)](./e_commerce_dataset.csv) | Raw e-commerce dataset loaded for analysis |
| `e_commerce_dataset_missing_values_handled.csv` | [![Imputed Dataset](https://img.shields.io/badge/CSV-Imputed-green?logo=pandas&style=flat-square)](./e_commerce_dataset_missing_values_handled.csv) | Dataset after applying missing value imputation |
| `e_commerce_dataset_dtypes_fixed.csv` | [![Dtypes Fixed](https://img.shields.io/badge/CSV-Dtypes%20Fixed-green?logo=pandas&style=flat-square)](./e_commerce_dataset_dtypes_fixed.csv) | Dataset after parsing and correcting incorrect data types |
| `e_commerce_dataset_duplicates_removed.csv` | [![Deduplicated](https://img.shields.io/badge/CSV-Deduplicated-green?logo=pandas&style=flat-square)](./e_commerce_dataset_duplicates_removed.csv) | Dataset after identifying and removing duplicate rows |
| `e_commerce_dataset_outliers_handled.csv` | [![Outliers Handled](https://img.shields.io/badge/CSV-Outliers--Handled-green?logo=pandas&style=flat-square)](./e_commerce_dataset_outliers_handled.csv) | Final clean dataset with mathematical outlier clipping/imputation |

---

## Learning Path

Click the diagram below to open and trace the full 17-module data science workflow inside the Jupyter Notebook:

[![Data Science Learning Path](../assets/data_science_training_flowchart.svg)](./Data_Science_Training.ipynb)

---

## Topics Covered & Methodologies

### 1. Exploratory Data Analysis (EDA)
Understanding data quality before building any machine learning pipeline. This phase includes:
- **Structural Inspection**: Printing dimensions (`df.shape`), listing column data types and memory details (`df.info()`), and inspecting summary distributions (`df.describe()`).
- **Target Analysis**: Locating which features are categorical versus numerical to guide downstream cleaning and feature engineering.

### 2. Missing Value Imputation
Real-world data contains gaps. We handle them selectively based on variable types:
- **Numerical Features**: Filled using the **Median** rather than the Mean when the data distribution is skewed (as the median is robust against extreme outliers).
- **Categorical Features**: Filled using the **Mode** (the most frequently occurring text value) to maintain realistic categories.
- **Critical Deletion**: Dropping rows (`df.dropna()`) only when the null ratio is minimal ($<1-2\%$) to preserve sample volume.

### 3. Data Types & Conversions
Pandas often loads temporal or categorical fields as general object types.
- **Datetime Parsing**: Converting string-formatted dates using `pd.to_datetime()`.
- **Feature Extraction**: Breaking datetime values down into seasonal or cyclical sub-components:
  $$\text{order\_date} \longrightarrow \text{year, month, day, day\_of\_week}$$
  This extraction allows models to learn weekly cyclical patterns (e.g. higher order volume on weekends).

### 4. Duplicate & Inconsistent Records
- **Exact Duplicates**: Found and removed via `df.drop_duplicates()` to avoid overfitting models to redundant data points.
- **Text Standardization**: Curing typos, trailing whitespace, and case sensitivity errors (e.g., standardizing `İstanbul`, `istanbul`, `Istanbul` using `.str.strip().str.lower()`).

### 5. Outlier Detection via the IQR Method
Outliers distort statistical estimates and degrade model accuracy. We systematically isolate them using the **Interquartile Range (IQR)**:

1. Compute the first quartile ($Q_1$, 25th percentile) and third quartile ($Q_3$, 75th percentile).
2. Calculate the IQR:
   $$IQR = Q_3 - Q_1$$
3. Establish the lower and upper anomaly detection fences:
   $$\text{Lower Fence} = Q_1 - 1.5 \times IQR$$
   $$\text{Upper Fence} = Q_3 + 1.5 \times IQR$$
4. Records falling outside $[\text{Lower Fence}, \text{Upper Fence}]$ are classified as outliers and are handled by capping them at the boundary fences or filtering them out.

### 6. Correlation Analysis & Heatmaps
To evaluate linear relationships between variables, we compute **Pearson's Correlation Coefficient ($r$)**:
$$r = \frac{\sum (x - \bar{x})(y - \bar{y})}{\sqrt{\sum (x - \bar{x})^2 \sum (y - \bar{y})^2}}$$
- $r \approx +1$: Perfect positive correlation (variables rise together).
- $r \approx -1$: Perfect negative correlation (one rises, the other falls).
- $r \approx 0$: No linear relationship.
We plot these values as a colored heatmap to quickly detect highly correlated features that could cause multicollinearity.

### 7. Pivot Tables & Aggregations
- **Bivariate Grouping**: Using `pd.pivot_table()` to slice numerical metrics across multiple dimensions simultaneously (e.g. examining Average Revenue broken down by both `city` and `payment_method`).

---

## Key Things I Want to Remember
- Always split your data before scaling/imputing when transitioning to Machine Learning to avoid **Data Leakage**.
- Categorical string inconsistencies (like casing or whitespace) can quietly double your category features during one-hot encoding if left unchecked.
- The order of data cleaning is critical:
  $$\text{Fix Data Types} \longrightarrow \text{Impute Missing} \longrightarrow \text{Remove Duplicates} \longrightarrow \text{Handle Outliers}$$

---

[← Back to Main](../README.md) &nbsp;|&nbsp; [Next: Machine Learning →](../02-Machine-Learning/)
