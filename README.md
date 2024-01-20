# Road Accident

Analysis

## Table of Contents 
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaning/preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references) 

### Project Overview
---
This Data Analysis Project aims to provide insights into the Road Accident Analysis in the United Kingdom between the years 2021 and 2022. By analyzing various aspects of the road accident data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the where majority of these accidents happen, which road types, vehicle types, and whether climates result in the most road accident casualties. We will the information curated from our analysis to make recommendations to the respective stakeholders.



### Data Sources
Sales Data: The primary data set used for this analysis is the "Road_Accident_Data.xls" file, containing detailed information about each sale made by the company.

### Tools 
- Excel - Data Cleaning
   - [Download here](https://microsoft.com)
- SQL Server
   - [Download here](https://azure.microsoft.com/en-gb/products/azure-sql/managed-instance/?&ef_id=_k_Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB_k_&OCID=AIDcmm4z26duq7_SEM__k_Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB_k_&gad_source=1&gclid=Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB)
- PowerBI - Creating reports
   - [Download here](https://www.microsoft.com/en-us/power-platform/products/power-bi)
 

### Steps in Project:
1. Requirement Gathering
2. Stakeholders in Project
3. Raw Data Overview
4. Connecting Data with PowerBI
5. Data Cleaning
6. Data Processing
7. Data Modelling
8. Data Visualisation/Charts Design
9. Insights
    
### Stakeholders in Project
- Ministry of Transport
- Road Transport Department
- Police force
- Emergency Services Department
- Road Safety Cops
- Transport Operators
- Traffic Management Agencies
- Public
- Media

### Client Requirements
The client wants to create a Road Accident Dashboard for years 2021 and 2022 so they can have insights on the below requirements: 
- Primary KPI - Total Casualties and Total Accident values for the Current Year and YoY growth
- Primary KPIs - Total Casualties by Accident Severity for Current Year and YoY growth
- Secondary KPIs - Total Casualties with respect to vehicle type for Current Year
- Monthly trend showing a comparison of casualties for the Current Year and the Previous Year
- Casualties by Road Type for the Current year
- Current Vear Casualties by Area/ Location & by Day/ Night
- Total Casualties and Total Accidents by Location



### Data Cleaning/Preparation
  In the initial data preparation phase, we performed the following tasks:
 1.  Data loading and inspection.
 2.  Handling missing values.
 3.  Data cleaning and forecasting.

### Exploratory Data Analysis
EDA involved exploring the sales data to answer key questions such as:
 - What is the overall sales trend?
 - Which prospects are top sellers?
 - What are the peak sales periods?

### Data Analysis 

```sql
SELECT " FROM table1
WHERE cond = 2;
```
### Results/Findings
The Analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
2. Product category A is the best-performing category in terms of sales and revenue.
3. Customer segments with high lifetime value (LIV) should be targeted for marketing efforts.

### Recommendations
Based on the analysis, we recommend the following actions:
- Invest in marketing and promotions during peak sales seasons to maximize revenue.
- Focus on expanding and promoting products in Category A.
- Implement a customer segmentation strategy to target high-LTV customers effectively
  
### Limitations
I had to remove all zero values from the budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between budget and the number of votes with revenue.

### References 
1. SQL for Businesses by Herman Ross
2. [Stack Overflow](https://stack.com)
