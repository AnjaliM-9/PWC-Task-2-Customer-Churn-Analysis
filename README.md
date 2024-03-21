# PWC-Task-2-Customer-Churn-Analysis
## Problem Statement:
Task given by retention manager
- Customers who left within the last month
 - Services each customer has signed up for: phone, multiple lines, internet, online security, online backup, device protection, tech support, and streaming TV and movies 
- Customer account information: how long as a customer, contract, payment method, paperless billing, monthly charges, total charges and number of tickets opened in the categories administrative and technical 
- Demographic info about customers – gender, age range, and if they have partners and dependents.
  
## Datasource and Preparation
Data set for this task was provided by PWC Job sim [02 Churn-Dataset.xlsx](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/files/14692101/02.Churn-Dataset.xlsx)
-The dataset contained 7004 rows and 23 columns.
- Applied Format as table in excel sheet
Steps performed for Data transformation in Power Query after the dataset loaded into Microsoft Power BI Desktop for modelling:
- Each of the columns in the table were validated to have the correct data type
- Filtered out missing values row from data set
- inserted a calculated column for evaluating years of service.
- Replaced 0 with “No” and 1 with  “Yes”
  
## Data Modeling
It is a flat file schema

![Picture 2](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/711d481b-6ba6-4087-9cd8-8726c7bda7da)

## Data Analysis (DAX)
Following are the measures created:-
-  ```ARPU = DIVIDE(SUM(CustomerChurn[MonthlyCharges]),COUNT(CustomerChurn[customerID]),0)```
-  ``` Churn by 2year = CALCULATE(COUNTROWS(CustomerChurn),(FILTER(CustomerChurn,CustomerChurn[Contract]="Two year" && CustomerChurn[Churn]="Yes")))```
-  ```Churn by month = CALCULATE(COUNTROWS(CustomerChurn),(FILTER(CustomerChurn,CustomerChurn[Contract]="Month-to-month" && CustomerChurn[Churn]="Yes")))```
-  ```Churn by year = CALCULATE(COUNTROWS(CustomerChurn),(FILTER(CustomerChurn,CustomerChurn[Contract]="One year" && CustomerChurn[Churn]="Yes")))```
-  ```Churn rate = DIVIDE([No of churned],COUNTROWS(CustomerChurn),0)*100``` 
-  ```Customer count = COUNT(CustomerChurn[customerID])```
-  ```No of churned = Calculate(distinctcount(CustomerChurn[customerID]),Filter('CustomerChurn',CustomerChurn[Churn]="yes"))```
-  ```No of stayed = Calculate(distinctcount(CustomerChurn[customerID]),Filter('CustomerChurn',CustomerChurn[Churn]="No"))```
-  ```Total Revenue = SUMX(CustomerChurn,CustomerChurn[TotalCharges])```
## Dashboard (Data Visualization)
### Summary
![0001](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/d4fbc731-41ec-4844-bdc5-5a82ed93b26a)
### Churn risk
![0002](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/060c697e-d312-49da-a826-f2c4392c3a45)
### Service Information
![0003](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/92629894-b3dc-42ec-b255-cb16b1ee0980)
### Demographics
![0004](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/7674168c-05bb-4e86-baf4-0ea4e244b5fe)
### Customer Info
![0005](https://github.com/AnjaliM-9/PWC-Task-2-Customer-Churn-Analysis/assets/155083462/93fe03db-a2f8-44b0-ae83-a82f4555245f)
## Insights!
Following conclusions could be drawn:
- Customers on the Two-Year contract, have been with the company for long, while most of the customers on Month-to-Month contract are churning mostly at the rate of 28.31%.
- There are total 7043 customers in dataset of which 1869 are churned,bChurn rate is 26.54%. ARPU of the company is round about $65.
- Total revenue collected is $16.06 M , Average of total charges $2,28K.
- 2955 tech tickets were opened and 3632 admin tickets were opened.
- It a lot of customers had an issue with Fiber Optic . Up to 42% of the customers churned were using Fiber Optic as their Internet Service.
