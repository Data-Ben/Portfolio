# Retail Sample 
This is a Power BI dashboard that provides a high-level overview of yearly sales at a retail store. The goal is to give executive stakeholders an overview of:

 1.Total units sold, total revenue, total profit, total cost, best-selling category, and the most profitable quarter.
                    
2.Profits broken down by product category and customer profile.
                    
 3.Revenue broken down by month, along with a running total of profit.

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
