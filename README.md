Credit Card Financial Dashboard

Project Overview

This project involves the development of a comprehensive Credit Card Analysis Dashboard using Power BI. The goal is to provide real-time insights into customer demographics, spending patterns, and financial health to support data-driven decision-making for the banking sector.

Data Cleaning (ETL)

The raw dataset was processed in Power Query to ensure high-quality reporting:

Resolved Date Conflict: Addressed a **58% error rate** in the `Week_Start_Date` column caused by mixed formats (DD-MM-YYYY and DD/MM/YYYY). I used manual parsing logic (`#date` function) to recover 100% of the records.

Custom Binning: Created Age Groups (18-25, 26-35, 36-45, etc.) and Income Tiers (Low, Mid, High) to enable deep-dive demographic analysis.

DAX Measures: Used advanced DAX for Year-over-Year growth and dynamic KPI calculations.

Age Group = SWITCH(TRUE(),
    'customer'[Customer_Age] <= 25, "18-25",
    'customer'[Customer_Age] <= 35, "26-35",
    'customer'[Customer_Age] <= 45, "36-45",
    "45+")

  Income Level = IF('customer'[Income] <= 30000, "Low",
    IF('customer'[Income] <= 100000, "Medium", "High"))

Total Revenue = SUM('CreditCard'[Interest_Earned]) + SUM('CreditCard'[Annual_Fees])


Data Modeling

Implemented a Star Schema logic.

Established a One-to-Many (1:*)relationship between the `Customer` and `CreditCard` tables using `Client_Num`.
  

Dashboard Reports

Page 1: Credit Card Customer Report (The "Who")

Focus: Customer Profiles, Behavior, and Risk.

KPI Cards: Total Customers, Total Revenue, Avg. Satisfaction Score, and Total Income.

Analysis:

Revenue by Age Group: Identifying which generation drives the most interest.

Revenue by Income Level: Analyzing spending power across Low, Mid, and High-income tiers.

Risk Profile: Monitoring Delinquent Accounts by Marital Status and Education.

Geographic Performance: Revenue distribution by `State_cd` via Map Visual.

Customer Job Analysis: Identifying top revenue-generating professions.

Page 2: Credit Card Transaction Report (The "How")

Focus: Sales Trends, Profitability, and Channel Usage.

KPI Cards: Total Transaction Amount, Total Transaction Vol, and Avg. Utilization Ratio.

Analysis: 
Weekly Revenue Trend: Time-series line chart tracking weekly performance.

Spending by Expense Type: Treemap showing distribution across Bills, Food, Fuel, Entertainment, etc.

Transaction Method:Pie chart comparing Swipe, Chip, and Online transactions.
      
Card Performance: Comparison of Blue, Silver, Gold, and Platinum card categories.

Quarterly Growth:Q1 to Q4 revenue progression using Area Charts.

Key Business Insights

Profitability: Identified that mid-age (26-45) customers in the High-Income bracket provide the best ROI.

Utilization: A high Credit Utilization Ratio correlates with higher revenue but also shows a spike in delinquency risk.

Channel Adoption: "Online" and "Chip" transactions are growing faster than traditional "Swipe" methods.

Category Focus: The "Blue" card category maintains the highest customer volume, while "Gold/Platinum" cards show higher revenue per user.

