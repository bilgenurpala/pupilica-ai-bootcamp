# 01 — Data Science Fundamentals

> My notes from the first week of the Pupilica AI Bootcamp.
> Instructor's repo: [turkiyeyapayzekaakademisi/veri-bilimi](https://github.com/turkiyeyapayzekaakademisi/veri-bilimi)

---

## What's in this folder

| File | Description |
|------|-------------|
| `Veri_Bilimi_Egitimi.ipynb` | Instructor's notebook — I follow along and add my own comments |
| `veri_bilimi_egitim_akis_semasi.svg` | Education flow diagram — 17-module data science learning path |
| `e_ticaret_veri_seti.csv` | Raw e-commerce dataset used throughout the exercises |
| `e_ticaret_veri_seti_eksik_veriler_duzenlendi.csv` | Dataset after handling missing values |
| `e_ticaret_veri_seti_aykiri_degerler_duzenlendi.csv` | Dataset after outlier treatment |
| `e_ticaret_veri_seti_tekrarlayan_kayitlar_duzenlendi.csv` | Dataset after removing duplicates |
| `e_ticaret_veri_seti_veri_tipleri_duzenlendi.csv` | Dataset after fixing data types |

---

## Learning Path

The diagram below shows the full 17-module data science learning path covered in this module.

![Data Science Learning Path](./veri_bilimi_egitim_akis_semasi.svg)

---

## Topics Covered

### Getting to Know the Dataset
The first thing I learned is that before touching any model, you have to actually *understand* your data. This means checking `df.shape`, `df.info()`, `df.describe()`, looking at the first and last rows, and understanding what each column represents.

### Missing Values
Missing data is way more common than I expected. I practised three approaches:
- Dropping rows with `dropna()` — simple but loses data
- Filling numerical columns with mean or median via `fillna()`
- Filling categorical columns with the most frequent value (mode)

The tricky part is deciding *which* method to use. Dropping rows is fine when there are very few missing values; otherwise you lose too much information.

### Data Types & Conversions
I learned that pandas doesn't always detect the correct type automatically. For example, the `order_date` column was loaded as a string and I had to convert it to `datetime` using `pd.to_datetime()`. This matters a lot for time-series analysis later.

### Duplicate & Inconsistent Records
I didn't realise how messy real data can be — same customer appearing twice with slightly different names, city names written in both uppercase and lowercase. `df.duplicated()` finds exact duplicates, but inconsistent strings need manual cleaning with `.str.strip().str.lower()`.

### Outlier Detection
Used the IQR method: anything below `Q1 - 1.5*IQR` or above `Q3 + 1.5*IQR` is considered an outlier. Visualising with boxplots before and after cleaning was really helpful to see the effect.

### Categorical & Numerical Analysis
- For categorical columns: frequency tables, bar plots, value counts
- For numerical columns: histograms, basic stats (mean, std, min, max)
- Groupby + aggregation to slice data by category, city, payment type

### Pivot Tables
`pd.pivot_table()` is basically Excel pivots but in Python. I used it to compare revenue across categories and payment types at the same time — much cleaner than nested groupbys.

### Data Visualisation
Practised the main chart types:
- **Line plot** → trends over time
- **Scatter plot** → relationship between two numerical variables
- **Bar plot** → comparisons across categories
- **Histogram** → distribution of a single variable
- **Heatmap** → correlation matrix

### Time Series Analysis
Extracted `month`, `day_of_week`, `week` from the date column and looked at order patterns over time. The most interesting insight: order volume and average spend both vary significantly by day of the week.

### Correlation Analysis
Built a correlation matrix and visualised it as a heatmap with `seaborn`. High correlation between two features means they carry similar information — useful to keep in mind for feature selection in ML.

### Data Storytelling
The last section was about turning analysis into business insights — not just "correlation is 0.85" but "customers who use credit cards tend to spend 30% more per order." This was my favourite part.

---

## Key Things I Want to Remember

- Always explore data before cleaning. Never assume it's clean.
- `df.info()` tells you dtypes and null counts at a glance — run it first.
- The order of cleaning steps matters: fix types → handle missing → remove duplicates → treat outliers.
- Visualisation is not just for presentation; it helps *you* spot problems in the data.

---

[← Back to Main](../README.md) &nbsp;|&nbsp; [Next: Machine Learning →](../02-Machine-Learning/)
