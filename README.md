# Road Accident Analysis
#### *Disclaimer: This analysis is for educational purposes only. The numbers do not reflect real data. The inspiration and data for this project come from this [YouTube video](https://youtu.be/RX0ehXijbSk?si=KAmIaTjhLVT2RHNL).* 

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
Road Accident Data: The primary data set used for this analysis is the "Road_Accident_Data.xls" file, containing detailed information about each sale made by the company.

### Tools 
- Excel - Data Cleaning
   - [Download here](https://microsoft.com)
- SQL Server
   - [Download here](https://azure.microsoft.com/en-gb/products/azure-sql/managed-instance/?&ef_id=_k_Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB_k_&OCID=AIDcmm4z26duq7_SEM__k_Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB_k_&gad_source=1&gclid=Cj0KCQiAtaOtBhCwARIsAN_x-3Lctv0lZSHFlwiSdXfgrVr-DWLt72NCWcUIdr4lXTDSLI0H4nqQ7MUaAkfBEALw_wcB)
- PowerBI - Creating reports
   - [Download here](https://www.microsoft.com/en-us/power-platform/products/power-bi)
 

### Steps in Project:
1. Requirement Gathering
2. Raw Data Overview
3. Connecting Data with PowerBI
4. Data Cleaning
5. Data Processing
6. Data Modelling
7. Data Visualisation/Charts Design
8. Insights
    
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

### Connecting Data with PowerBI
After opening up the Road Accident xls document in PowerBI, I went ahead to transformed the data in the Power Query editor. We can refer to this editor as the kitchen of our PowerBi desktop in the sense that we cook our data here by cleaning and giving shape to our data after which we go back to our PowerBI to start designing around it. During this stage, I corrected some spelling errors in the data using the 'Replace value' function. I also made sure that the number of rows and columns was the same as the Excel document data.
### Data Cleaning
### Data Processing
In this step, I used custom DAX formulas to Transform the data set.
In the requirements, the client asked us to determine the year-to-date (YTD) casualties, year-on-year casualties growth (%), and whether they are increasing with respect to last year and what the (%) increase/decrease is. To do this, I used some time intelligence functions by creating a 'date table' to allow me to extract the year and months when calculating YTD and YOY growth. I named this table as 'calendar'. The calendar table initially had dates starting from 1899 and we don't have data from

During this step, I used the following DAX operations..
```DAX
Calendar = CALENDARAUTO(3)
```
```
Calendar = CALENDAR(MIN(Datat[AccidentDate]),MAX(Data[AccidentDate])
```
```
I then created a new column to extract the Year from the Dates and named it Year...
```
Year = YEAR('Calendar'[Date])
```
Then another column to extract Month..
``
Month = FORMAT('Calendar'[Date],"mmm")
```
### Data Modelling
In this stage, I connected the Calendar and Date table. To do this, I switched to the PowerBI model view and and connected the "AccidentDate" field in the Data table with the "Date" field in the Calendar table and this created a relationship that is 1 to many as seen below.

<img width="334" alt="Picture2" src="https://github.com/CikuAnalyst/Power-Bi-Dashboard-on-RA-Analysis/assets/132788939/1ccb7202-c315-4f18-bee0-238111815e52">

This simply tells us that the "Date" field in the Calendar table has dates that are distinct (and in a chronological list), while the "AccidentDate" field has repeated dates because some accidents may have occurred on the same day.

From this point on, all operations performed were performed on the "Date" field from the Calendar table because I have now made the relationship connection.

### Data Visualization/Charts Design 
I then created a custom Measure to determine 'Year to Date' (YTD) since this is a requirement from our Primary KPIs 
To do this I created a 'New Measure' and named it 'CY Casualties' to represent Current year Casualties then I used the 'TOTALYTD' DAX function as seen below
```DAX
CY Casualties = TOTALYTD(SUM(Data[Number_of_casualties]),'Calendar'[Data])
```
After doing this, the CY Casualties field appeared under the "Data table"

Next up, I created a KPI card for CY Casualties 

<img width="112" alt="Picture3" src="https://github.com/CikuAnalyst/Power-Bi-Dashboard-on-RA-Analysis/assets/132788939/5621eb66-6419-4124-a38c-bcc3ce2cfd92">

At the bottom of the KPI Card, I included the percentage for Year on Year CY Casualties growth 
using the following formula:
<img width="416" alt="Picture4" src="https://github.com/CikuAnalyst/Power-Bi-Dashboard-on-RA-Analysis/assets/132788939/da7252e8-4f44-4732-9b3d-445015d2edc0">

In order to use this, formula, I had to determine the Past Year Casualties. To do this I wrote the following DAX formula...

```DAX
PY Casualties = CALCULATE (SUM[Number_of_Casualties]),SAMEPERIODLASTYEAR('Calnedar'[Date]))
```
and..

```DAX
YoY Casualties = ([CY Casualties] - [PY Casualties])/[PY Casualties]
```

Next up, I created a KPI card fro Current Year Accidents using the same logic, same to the three types of casualties (fatal, serious and slight).

<img width="434" alt="Picture5" src="https://github.com/CikuAnalyst/Power-Bi-Dashboard-on-RA-Analysis/assets/132788939/86d35c0a-2129-4a8e-a7a3-048579ddd524">

I added a Multi-row card showing the different casualties by vehicle type,
A Area Chart showing CY Casualties vs PY Casualties Monthly Trend,
Casualties by Road Type Stacked bar chart,
Casualties by Urban/Rural area donut chart 
Casualties by Light Conditions donut chart 
Map of the United Kingdom

<img width="434" alt="Picture6" src="https://github.com/CikuAnalyst/Power-Bi-Dashboard-on-RA-Analysis/assets/132788939/7d654518-2063-466f-9219-642f600967d5">

### Insights and Recommendations
The Analysis results are summarized as follows:
1. W.r.t the previous year, the total CY Casualties have reduced by -11.9%
2.   The number of Accidents has fallen by 11.7% in the current year
3. The Fatal Accident severity casualty percentage dropped by the biggest margin compared to the other lesser severities. This is a positive insight as it shows that less people died in the 2022 road accidents.
4. Majority of the accidents were caused by PSV cars followed by vans
T5. the Single Carriageway Road type accounted for the most accidents in the current year (144653) which was over 50% 
6. According to the monthly accident trend for CY and PY, the majority of accidents occurred in November 
7. Most Accidents happened in Light conditions and in the Urban area 
### Recommendations
- Ministry of Transport may need to put in place road safety regulations to reduce the number of casualties further from -11.9% to -50% - -60%
- The government should work with the media should target PSV car owners to bring awareness of the dangers of reckless driving and the importance of adhering to the rules. Most especially in November.
- The government should also place Road safety signages such as speed limits on the Single Carriageway to reduce number of accidents
- It is observed that most accidents happen during the daytime (light) conditions, however, this is expected because the road is most active during the day. So I would recommend that the Ministry of Transport reduces the number of accidents occurring at night by increasing street lighting and the use of reflector material on road signages to improve visibility.


### Validation of Values using MsSQL 
After creating the PowerBI dashboard, I fired some queries on the values I had gotten in my Analysis.
The following are some of the SQL Queries I fired and their effect.

```SQL
SELECT * FROM road_accident

SELET SUM(number_of_causualties) AS CY_Casualties
FROM road_accident
WHERE YEAR (accident_date) = '2022'
```
The result of this query was 195737, which validated the Total Sum of CY Casualties from our dashboard

```sql
SELECT CAST(SUM(number_of_casualties0 AS DECIMAL
(10,2))/
(SELECT CAST(SUM(number_of_casualties) AS DECIMAL
(10,2)) FROM road_accident) AS PCT
FROM road_accident
WHERE accident_severity = 'Slight'
```
The result was 84.1%, which confirms the CY Slight Accident Severity percentage 

### Limitations
- Initially, it took me a while to grasp the Time intelligence functions and how to use them, however with practice and deep focus I was able to use them successfully
  
### References 
1. SQL for Businesses by Herman Ross
2. [Stack Overflow](https://stack.com)
3. [YouTube video](https://youtu.be/RX0ehXijbSk?si=KAmIaTjhLVT2RHNL) 
