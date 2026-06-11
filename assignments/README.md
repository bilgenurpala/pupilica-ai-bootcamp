# Repository Assignments Dashboard

<div align="center">

[![Assignments](../assets/main_banner.png)](../README.md)

</div>

> Midterm and final assignment specifications for the Pupilica AI Bootcamp.

---

## Assignment Modules

| Assignment | Specification Link | Primary Focus | Target Dataset | Status |
|:---|:---|:---|:---|:---|
| **Midterm Assignment** | [![Midterm Spec](https://img.shields.io/badge/Midterm-Specification-blue?style=flat-square)](./midterm/midterm_assignment.md) | Exploratory Data Analysis, Cleaning, Type Parsing, Duplicates, and IQR Outlier Detection | `e_commerce_dataset.csv` | Completed |
| **Final Assignment** | [![Final Spec](https://img.shields.io/badge/Final-Specification-blue?style=flat-square)](./final/final_assignment.md) | End-to-end analytics, commercial metric aggregation, multi-dimensional groupings, and data-driven business insights | `e_commerce_dataset.csv` | Completed |

---

## Midterm Assignment Overview

The midterm assignment validates hands-on understanding of data science fundamentals. Key milestones include:
1. **Initial Inspection**: Loading datasets and evaluating columns/types using `info()` and `describe()`.
2. **Missing Value Imputation**: Handling missing numerical values (using the median) and categorical values (using the mode).
3. **Data Type Correction**: Converting temporal variables to datetime formats and performing component extraction.
4. **Data Cleaning**: Deduplicating records and standardizing inconsistent strings (casing/spaces).
5. **Outlier Mitigation**: Isolating outliers using the **Interquartile Range (IQR)** method.
6. **Descriptive Aggregations**: Extracting categorical frequencies, numerical distributions, and calculating targeted averages.

*Specification File:* [midterm/midterm_assignment.md](./midterm/midterm_assignment.md) (Original document: `midterm_assignment.docx`)

---

## Final Assignment Overview

The final assignment is a comprehensive analytics project focusing on business logic and data storytelling:
1. **Commercial Performance Analysis**: Aggregating revenue, ratings, and shipping delays across different categories to identify top-performing product groups.
2. **Geographical Potential Analysis**: Slicing revenue by cities to rank locations and highlight high-potential growth markets.
3. **Payment Method Analysis**: Evaluating average transaction sizes and customer ratings to understand checkout behavior.
4. **Temporal Patterns**: Analyzing monthly revenue trends to determine if order quantity increases align with overall revenue increases.
5. **Multi-Dimensional Opportunities**: Cross-referencing city and category distributions to locate targeted marketing targets.

*Specification File:* [final/final_assignment.md](./final/final_assignment.md) (Original document: `final_assignment.docx`)

---

## General Submission Rules

> [!IMPORTANT]
> - Assignments are completed and compiled using **Google Colab**.
> - Submissions are sent as shareable public Google Colab links to **info@turkiyeyapayzekaakademisi.com**.
> - Email subject formatting rules:
>   - Midterm: `Data Science First Assignment – Name Surname`
>   - Final: `Data Science Final Assignment – Name Surname`
> - Notebooks must be fully executed, with all charts, matrix outputs, and textual explanations visible.

---

[← Back to Main](../README.md)
