# Retail Sample 
This is a Power BI dashboard that provides a high-level overview of yearly sales at a retail store. The goal is to give executive stakeholders an overview of:

 1.Total units sold, total revenue, total profit, total cost, best-selling category, and the most profitable quarter.
                    
2.Profits broken down by product category and customer profile.
                    
 3.Revenue broken down by month, along with a running total of profit.

 Follow this link to download the full project: https://github.com/Data-Ben/Portfolio

# Dashboard
![Retail Report_page-0001](https://github.com/user-attachments/assets/5ca4ec01-f60b-4f78-b4bc-9175a7d2d249)

# ETL Process
I performed the following transformations in Power Query:

1.Removed unnecessary columns and defined appropriate data types.

2.Created a Product dimension table.

3.Created a Date dimension table.

4.Parameterized the data source connection.

# Data Modeling
The Date and Product dimension tables are linked to the fact table through a one-to-many relationship with a single-direction filter, as shown below:
![image](https://github.com/user-attachments/assets/3ebc3122-a0ab-4959-8a44-b12f21a1719b)

# DAX
I created the following calculated columns:

1.Profit = Sales[Total Amount] * RELATED(Products[Profit Margin])

2.Cost = Sales[Total Amount] - Sales[Profit]

For the measures, I used the following functions:

1.For totals, I used the SUM() function.
Example:
       Total Revenue = SUM(Sales[Total Amount])

2.For subgroups, I used the CALCULATE() function.

Example:

    Total Female Customers = 
    VAR calc = CALCULATE([Total Customers], Sales[Gender] = "Female")  
    RETURN IF(calc = BLANK(), 0, calc)

3.For top values, I used the TOPN() function.

Example:

    Best Selling Category =FIRSTNONBLANK(TOPN(1, VALUES(Products[Category]), [Total Units Sold]), 1)

4.For running totals, I also used the CALCULATE() function.

Example:

    Profit Running Total =CALCULATE(
        SUM(Sales[Profit]),
        FILTER(
            ALLSELECTED('Date'[Date]),
            ISONORAFTER('Date'[Date], MAX('Date'[Date]), DESC)
        )
    )

