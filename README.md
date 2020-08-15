### InsideSherpa
# [Quantium Data Analytics Virtual Experience Program](https://www.insidesherpa.com/virtual-internships/prototype/NkaC7knWtjSbi6aYv/Data%20Analytics%20Virtual%20Experience%20Program#lp)
- This program consists of 3 tasks.
- Each task submission is in each folder. (All submission is personal contribution. None is Quantium's model work file.)

---

### Code and Resources Used
**Python Version:** 3.7\
**Packages:** pandas, numpy, sklearn, matplotlib, datetime, scipy, mlxtend

---

### Task 1 - Data preparation and customer analytics
Conduct analysis on client's transaction dataset and identify customer purchasing behaviours to generate insights and provide commercial recommendations.

#### Data Cleaning:
- Date column was in integer format ([Amount of days after December 30th 1899](https://stackoverflow.com/questions/3963617/why-is-1899-12-30-the-zero-date-in-access-sql-server-instead-of-12-31)). Changed date column to datetime data type.
- Ensuring all products are Chips. Split and counted frequency of each word in "PROD_NAME" column. Removed all rows containing "salsa" in "PROD_NAME".
- Removed outliers rows in "PROD_QTY" column.
- Value counted each first word in "PROD_NAME" column to extract brand name. Combined brands written in multiple ways. Created new column "Cleaned_Brand_Names".

#### Data Analysis on Customer Segments:
- Groupby sum TOT_SALES column and identified top 3 highest total sales contributing segments.
- 


---

### Task 2 - Experimentation and uplift testing
Extend analysis from Task 1 to help identify benchmark stores to test the impact of the trial store layouts on customer sales.

---

### Task 3 - Analytics and commercial application
Use analytics and insights from Task 1 and 2 to prepare a report for the client, the Category Manager.
