# LITA_Customer_Segmentation_Analysis
This project demonstrates my ability to analyze and derive actionable insights from Subscription service customer data using Excel, SQL, and Power BI. The objective was to explore customer preferences and visualize key trends including revenue trends, average subscription duration, and cancellation rates across regions and subscription types. 

# Project 2: Customer Segmentation for a Subscription Service
---
### Project Overview
In this project, I focused on analyzing customer data for a subscription service to uncover key segments, track subscription patterns, and identify trends in cancellations and renewals. The goal is to gain insights into customer behavior and subscription dynamics, ultimately delivering an interactive Power BI dashboard that highlights these findings.

### Data used:
The dataset used for this analysis is the **"Customer_data.csv"** file, containing detailed information about each sale made. It comprises of 8 columns;
1. Customer Id
2. Customer Name
3. Region
4. Subscription Type
5. Subscription Start
6. Subscription End
7. Canceled
8. Revenue

### Tools used:
- **Excel**: For identifying subscription patterns using pivot tables.
- **SQL**: For querying customer behaviors, subscription types, and cancellations.
- **Power BI**: For creating an interactive dashboard to visualize customer trends.

### Data Cleaning/ Preparation
In the initial data preparation phase, I performed the following tasks:
1. Data loading and inspection.
2. Handling missing variables.
3. Data cleaning and formatting.

### Exploratory Data Analysis
In this project, I analyzed customer data for a subscription service to uncover key segments, understand subscription behaviors, and identify trends in cancellations and renewals. Below is the exploratory data analysis process.

**1. Excel Analysis:**

I analyzed customer data using pivot tables and formulas in Excel to uncover initial insights into subscription patterns.

- **Pivot Tables:**
  - **Subscription Patterns:** Used pivot tables to break down customer data by subscription type, region, and duration to identify the most common subscription types and customer demographics.
  - **Subscription Type Popularity:** Analyzed the number of customers by subscription type to find which subscriptions are most popular.
  - **Subscription Duration:** Calculated the average subscription duration to gauge how long customers stay subscribed, using formulas to find the mean and distribution of durations.
- **Additional Reports:**
  - Generated additional reports to uncover insights, such as identifying potential retention strategies and comparing the performance of different regions in terms of subscription renewals and cancellations.
 
**2. SQL**

I loaded the dataset into an SQL Server environment and wrote queries to answer specific questions about customer segments and subscription trends.
- **Total Customers by Region:** Extracted data on how many customers are present in each region, providing insight into geographic patterns.
- **Most Popular Subscription Type:** Retrieved the number of customers by subscription type, identifying the service tiers or products with the highest adoption rates.
- **Cancellations within 6 Months:** Identified customers who canceled their subscriptions within the first 6 months to highlight early churn patterns.
- **Average Subscription Duration:** Calculated the average time customers stay subscribed, providing an overview of customer loyalty.
- **Long-term Subscriptions:** Found customers with subscriptions longer than 12 months, highlighting those who are highly engaged and loyal.
- **Total Revenue by Subscription Type:** Analyzed revenue generated by each subscription type to determine which services are the most profitable.
- **Top 3 Regions by Cancellations:** Pinpointed the regions with the highest subscription cancellations, providing insights for targeted marketing or customer retention strategies.
- **Active vs. Canceled Subscriptions:** Compare the total number of active and canceled subscriptions to understand the balance between customer acquisition and retention.

**3. Power BI Dashboard**

I built a comprehensive and interactive Power BI dashboard that visualizes key insights found during the Excel and SQL analysis.
Customer Segments visualize customer demographics and subscription behavior by region, type, and duration.
- **Cancellations and Renewals:** Displays trends in cancellations and renewals, allowing users to filter by region, subscription type, and periods using slicers.
- **Revenue Insights:** Visualizes revenue distribution by subscription type, helping to identify which services drive the most income.
- **Key Performance Indicators (KPIs):** Summarize active versus canceled subscriptions, average subscription duration, and customer retention rates for a quick snapshot of the service's health.

### Data Analysis
- _**Total number of customers from each region**_
```SQL
SELECT Region, COUNT(CustomerID) AS NumberOfCustomers
FROM [dbo].[CustomerData]
GROUP BY Region;
```
- _**Most popular subscription type by number of customers**_
```SQL
SELECT TOP 1 SubscriptionType, COUNT(CustomerID) AS CustomerCount
FROM [dbo].[CustomerData]
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC;
```
- _**Customers who canceled their subscription within 6 months**_
```SQL
SELECT CustomerName
FROM [dbo].[CustomerData]
WHERE Canceled = 1
AND DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6;
```
- _**Average subscription duration for all customers**_
```SQL
SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) AS AverageSubscriptionDuration
FROM [dbo].[CustomerData]
```
- _**Customers with subscription longer than 12 months**_
```SQL
SELECT CustomerName
FROM [dbo].[CustomerData]
WHERE DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) > 12;
```
- _**Total Revenue by subscription type**_
```SQL
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[CustomerData]
GROUP BY SubscriptionType;
```
- _**Top 3 regions by subscription cancellation**_
```SQL
SELECT TOP 3 Region, COUNT(CustomerID) AS Cancellations
FROM [dbo].[CustomerData]
WHERE Canceled = 1
GROUP BY Region
ORDER BY Cancellations DESC;
```
- _**Total number of active and canceled subscriptions**_
```SQL
SELECT 
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[CustomerData]
```

### Data Visualization
- **Using Excel**

![Total Revenue by Region](
