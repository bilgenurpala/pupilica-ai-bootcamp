# Data Science Midterm Assignment
**Turkey AI Academy (Türkiye Yapay Zeka Akademisi)**

## Dataset
The same e-commerce dataset used throughout the training (`e_commerce_dataset.csv`).

## Assignment Type
Midterm Assignment

## Description
In this assignment, you are expected to apply the following steps on the dataset we covered during the training: understanding the dataset, handling missing values, data types and conversions, cleaning duplicate and inconsistent records, outlier analysis, categorical data analysis, and numerical data analysis. It is recommended to solve the questions in order, maintaining a single logical flow.

## Submission Rules
1. Prepare your assignment on **Google Colab**.
2. Submit by sending a shareable Google Colab link.
3. Email your Colab link to **info@turkiyeyapayzekaakademisi.com**.
4. The email subject must be in the following format: `Data Science First Assignment – Name Surname`.
5. Your Colab link must have viewing permissions set to public; links with restricted access may not be evaluated.
6. The code must be fully executable, with all outputs and charts visible inside the notebook.
7. You are expected to write a brief comment/interpretation under each question.

## Support & Mentorship
- You can ask any questions you have about the assignment during our weekly mentorship meetings.
- You are expected to apply the logic taught in class; it is important to build your own logical flow rather than copying solutions directly.

---

## Assignment Questions

1. Load the dataset and print its first 10 rows and last 10 rows to the screen.
2. Print the number of rows, number of columns, and all column names of the dataset to the screen.
3. Get the outputs of `info()` and `describe()`. Then, list the numerical columns and categorical columns in the dataset separately.
4. Calculate the number of missing values in each column. Then, calculate the missing data ratios as percentages and print the top 5 columns with the highest missing data ratio.
5. Filter the rows containing at least one missing value and print the first 20 of these rows to the screen.
6. Fill the missing values in the `discount_rate` and `customer_rating` columns with the median. Compare the number of missing values in these two columns before and after filling them.
7. Fill the missing values in the `payment_method` and `customer_type` columns with the mode. Then check if there are any missing values left in these columns.
8. Convert the `order_date` column to datetime type. Then, extract 4 new columns named `order_year`, `order_month`, `order_day`, and `day_of_week` from this column and display the first 10 rows.
9. Find the number of duplicate records in the dataset. Remove duplicate records and print the number of rows in the dataset before and after the cleaning.
10. Examine the unique values in the `city` column. Standardize different spellings that mean the same thing (e.g. İstanbul, istanbul, Istanbul) into a single standard format. Compare the number of unique values before and after cleaning.
11. Examine inconsistent values in the `category` column. For example, convert different spellings like "Home & Living", "home and living", "home&living" into a single format. Print the `value_counts()` output after cleaning.
12. Find logically incorrect records that meet the following conditions: `unit_price <= 0`, `total_amount <= 0`, `delivery_days < 0`, `customer_rating > 5`. Print the count of these records and remove them from the dataset.
13. Calculate the Q1, Q3, IQR, lower limit, and upper limit values for the `unit_price` column using the IQR method. Then print the number of records containing outliers.
14. Plot a histogram and a box plot for the `total_amount` column. Then write a brief 2-3 sentence comment about its distribution.
15. Perform the following analyses:
    - Print the `value_counts()` output for the `category` column.
    - Calculate the percentage distribution for the `customer_type` column.
    - Plot a count plot for the `payment_method` column.
    - Extract basic statistics for the `unit_price`, `total_amount`, and `customer_rating` columns.
    - Finally, answer these two questions:
      - Which category has the highest average `total_amount` value?
      - Which customer type has the highest average `customer_rating` value?

> 📌 **Note:** Maintain the original state of the dataset throughout the assignment. It is recommended to perform cleaning and transformation operations on copies of the datasets as much as possible.
