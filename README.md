# Lita_Capstone_Project2


### TOPIC: CUSTOMER SEGMENTATION FOR SUBSCRITION SERVICE                                      

### Overview
This project involves analyzing customer data for a subscription service to identify segments and trends

## Project Objective
This project was designed to address the following analysis goals:
i. Understand customer behaviour 
ii. Track subscription types
iii. Identify key trends in cancellations and renewals

## Data Collected
The customer data includes the following columns:
•	CustomerID: A unique identifier for each customer.
•	CustomerName: The name of the customer.
•	Region: Geographic region where the customer is located.
•	SubscriptionType: Type of subscription (Basic, Premium, Standard, etc.).
•	SubscriptionStart: Start date of the subscription.
•	SubscriptionEnd: End date of the subscription.
•	Canceled: Whether the subscription was canceled (True/False).
•	Revenue: Revenue generated by the customer.

## Tools Used
1. Miicrosoft Excel:
- Data cleaning: This is the removal of all unwanted attachment from your data,ensure there are no missing or inaccurate values provide data quality and consistency
- Data Analysis: Utilizing Excel's pivot tables and charting features, visualizations to uncover trends and insights related to different aspects of the dataset, summarize and filter the data for easier   interpretation, culminates in a visual dashboard which provides an overview of the sales data and allows users to explore key metrics and trends.
- Data Visualization: This provide the necessary context for data to be interpreted and acted upon.
2. SQL: Structured Query Language for quering data
3. Power BI for data modelling
4. Github for Portfolio building
  
## Visual Analysis
Pivot Table
- The Average Subscription duration
![image](https://github.com/user-attachments/assets/4ea96c51-e3f4-4f09-b3bb-f99b43549682)

- Subscription Patterns

![image](https://github.com/user-attachments/assets/f721527f-cfb1-4b3d-bf89-788ba4f0e795)

- Bar Chart
  
 ![image](https://github.com/user-attachments/assets/5a7f676a-9feb-4ef5-8c21-72334aa07a82)

![image](https://github.com/user-attachments/assets/e39c5442-995a-431b-a946-801baa89f209)

- Total number of customers from each region

```
Select Region, Count(CustomerID) As Total_Customers from Customer_Data
group by Region;
```
  
  ```
  SELECT Region, COUNT(CustomerID) AS TotalCustomers FROM CustomerData
GROUP BY Region;
```

2. Most popular subscription type by the number of customers

```
SELECT SubscriptionType, COUNT(CustomerID) AS NumberOfCustomers FROM CustomerData
GROUP BY SubscriptionType
ORDER BY NumberOfCustomers DESC
LIMIT 1;
```

3. Customers who canceled their subscription within 6 months

```
SELECT AVG(DATEDIFF(SubscriptionEnd, SubscriptionStart)) AS AvgSubscriptionDuration
FROM CustomerData;
```

5.	Customers with subscriptions longer than 12 months

```
SELECT CustomerID, CustomerName, SubscriptionType, SubscriptionStart, SubscriptionEnd
FROM CustomerData
WHERE DATEDIFF(SubscriptionEnd, SubscriptionStart) > 365;
```

6. Total revenue by subscription type

```
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM CustomerData
GROUP BY SubscriptionType;
```

7. Top 3 regions by subscription cancellations

```
SELECT Region, COUNT(CustomerID) AS Cancellations
FROM CustomerData
WHERE Canceled = True
GROUP BY Region
ORDER BY Cancellations DESC
LIMIT 3;
```

8. Total number of active and canceled subscriptions

```
SELECT 
    COUNT(CASE WHEN Canceled = False THEN 1 END) AS ActiveSubscriptions,
    COUNT(CASE WHEN Canceled = True THEN 1 END) AS CanceledSubscriptions
FROM CustomerData;
```




