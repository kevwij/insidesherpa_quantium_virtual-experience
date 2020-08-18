### InsideSherpa
# [Quantium Data Analytics Virtual Experience Program](https://www.insidesherpa.com/virtual-internships/prototype/NkaC7knWtjSbi6aYv/Data%20Analytics%20Virtual%20Experience%20Program#lp)
- This program consists of 3 tasks.
- All files are my personal submission for this program. Not Quantium's model work files.

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
- Groupby sum TOT_SALES column and identified top 3 highest total sales contributing segments. (Older families-Budget, Young Singles/Couples-Mainstream, Retirees-Mainstream)
- Plot the groupby into stacked bar chart with percentage text on each segment stack.
![Total Sales by Segment](/graphs/lifestage_sales.png)
- Groupby nunique to find number of unique customers in each segment. Found high sales amount by segment "Young Singles/Couples - Mainstream" and "Retirees - Mainstream" are due to their large number of unique customers
- Used p-value calculation and found statistically significant TOT_SALES difference (pval < 5%) between "Mainstream Young Midage" to "Budget and Premium Young Midage" segment.
- Divided groupby sum to groupby nunique to get average amount of chips bought per customer segment. Older and Young Families bought the highest average amount of chips.
- Unstacked the groupby and plotted it by segment:
![Avg chips per customer](/graphs/Average%20purchase%20quantity%20per%20segment.png)

#### Insights:
- Top 3 total sales contributor segment are
  - Older families (Budget) $156,864
  - Young Singles/Couples (Mainstream) $147,582
  - Retirees (Mainstream) $145,169
- Young Singles/Couples (Mainstream) has the highest population, followed by Retirees (Mainstream). Which explains their high total sales.
- Despite Older Families not having the highest population, they have the highest frequency of purchase, which contributes to their high total sales.
- Older Families followed by Young Families has the highest average quantity of chips bought per purchase.
- The Mainstream category of the "Young and Midage Singles/Couples" have the highest spending of chips per purchase. And the difference to the non-Mainstream "Young and Midage Singles/Couples" are statistically significant.
- Chips brand Kettle is dominating every segment as the most purchased brand.
- Observing the 2nd most purchased brand, "Young and Midage Singles/Couples" is the only segment with a different preference (Doritos) as compared to others' (Smiths).
- Most frequent chip size purchased is 175gr followed by the 150gr chip size for all segments.

---

### Task 2 - Experimentation and uplift testing
Extend analysis from Task 1 to help identify benchmark stores to test the impact of the trial store layouts on customer sales.
- Client selected store number 77, 86 and 88 as trial stores. The goal of this task is to select 1 control store for each trial store.
- Control store will be chosen based on combined similarity magnitude of "Monthly overall sales revenue" and "Monthly number of customers" of the store with the trial stores.
- Groupby each store into monthly groups and remove stores that had less than 12 months of transaction data.
- Each groupby store has columns consisting total sales, number of customers, transactions per customer, chips per customer and the average price per unit.
- Made 2 functions that calculates trial store's correlation of chosen metric to other stores (using pandas DataFrame.corrwith method) and another that calculates normalized distance magnitude of chosen metric to other store 1 - ( (value - min_value) / (max_value - min_value) )
- The above 2 funcitons are used and averaged to compute the magnitude of similartiy for the trial stores based on Total_Sales and Number_of_Customers.
- Highest average score (average of Total_Sales and Number_of_Customers magnitude of similarity) for each trial store is chosen as the control store.
- Next phase is to assess trial store's performance compared to control store's scaled performance (scaled control store's performance to match trial store's). Used t-value to check if each trial and control store's percentage difference is statistically significant during the trial phase compared to the percentage difference during pre-trial phase.\
\
Total Sales comparison:
![Tot_sales trial vs control](/graphs/TOT_SALES%20compare.png?raw=true)
Number of Customers comparison:
![nCustomers trial vs control](/graphs/nCustomers%20compare.png?raw=true)
- Conclusion: Trial store 77 and 86 had significant increase in total sales and number of customers during trial compared to control store. Trial store 88 had increases as well but insignificant.

---

### Task 3 - Analytics and commercial application
Use analytics and insights from Task 1 and 2 to prepare a report for the client, the Category Manager.
- Used Pyramid Principle method to deliver insigths and recommendation to client in Powerpoint.
