# Data Science Final Assignment
**Turkey AI Academy (Türkiye Yapay Zeka Akademisi)**

## Dataset
The same e-commerce dataset used throughout the training (`e_commerce_dataset.csv`).

## Assignment Type
Final Assignment

## Description
In this final assignment, you are expected to bring together the data cleaning, analysis, visualization, and interpretation skills you learned throughout the training on the same dataset. Answer the questions below using the data, support them with appropriate charts, and write a brief business interpretation at the end of each question.

## Submission Rules
1. Prepare your assignment on **Google Colab**.
2. Submit by sending a shareable Google Colab link.
3. Email your Colab link to **info@turkiyeyapayzekaakademisi.com**.
4. The email subject must be in the following format: `Data Science Final Assignment – Name Surname`.
5. Your Colab link must have viewing permissions set to public; links with restricted access may not be evaluated.
6. The code must be fully executable, with all outputs and charts visible inside the notebook.
7. You are expected to write a brief business interpretation/insight at the end of each question.

## Support & Mentorship
- You can ask any questions you have about the assignment during our weekly mentorship meetings.
- You are expected to apply the logic taught in class; it is important to build your own logical flow rather than copying solutions directly.

---

## Assignment Questions

### 1. Which category looks strongest in terms of both commercial performance and customer satisfaction?
- Extract the following metrics on a category basis: order count, total revenue, average order amount, average customer rating, and average delivery days.
- Create a summary table grouped by category.
- Plot a bar plot for total revenue.
- Plot a second bar plot for the average customer rating.
- Identify the strongest category in terms of both revenue and satisfaction, and write a brief business interpretation.

### 2. Which cities hold higher potential?
- Extract the following metrics on a city basis: order count, total revenue, average order amount, and average customer rating.
- Create a summary table grouped by city.
- Sort the cities in descending order by total revenue.
- Plot a bar plot for the top 5 strongest cities.
- Identify cities that have high customer ratings but lag in revenue, and write a brief comment on these candidate cities for growth.

### 3. Which payment method generates more valuable customer behavior?
- Extract the following metrics on a payment method basis: order count, total revenue, average order amount, average customer rating, and average delivery days.
- Create a summary table grouped by payment method.
- Plot a bar plot for the average order amount.
- Plot a second bar plot for the average customer rating.
- Compare the payment method that generates the highest revenue with the one that generates the highest satisfaction, and interpret the result in business language.

### 4. How does sales behavior change over time?
- Convert the `order_date` column to the appropriate datetime data type.
- Extract the following metrics on a monthly basis: order count, total revenue, and average order amount.
- Plot a line plot for the order count.
- Plot a second line plot for total revenue.
- Compare the busiest month with the month that yielded the highest revenue, and comment on the question: *"Do order increases and revenue increases occur in the same period?"*

### 5. Which city-category combinations offer the strongest opportunities?
- Extract the following metrics broken down by both `city` and `category`: order count, total revenue, average order amount, and average customer rating.
- Find the top 10 strongest city-category combinations.
- Create an appropriate bar plot to show these combinations.
- Identify the strongest combination.
- Interpret what this finding could mean in terms of marketing, campaigns, or product strategy.

---

> 📌 **Note:** In the final assignment, the goal is not just to produce tables and charts. The main objective is to extract meaningful conclusions from the data and interpret these findings clearly.
