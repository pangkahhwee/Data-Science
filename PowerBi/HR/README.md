![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR90.png)

# Powering HR insights: Visualizing employee attrition & performance in Power BI

## Table of Contents
1. [Introduction](#ch1)
1. [Dataset Overview](#ch2)
1. [Problem Definition](#ch3)
1. [Data Gathering](#ch4)
1. [Data Preparation](#ch5)
1. [Explanatory Data Analysis (EDA)](#ch6)
1. [Data Visualisation using Pandas, Matplotlib and Seaborn](#ch7)
1. [Data Relationships](#ch8)
1. [KPI Cards](#ch9)
1. [Bar Chart](#ch10)
1. [Stacked Bar Chart](#ch11)
1. [KPI Cards for Demographics Page](#ch12)
1. [Combined Chart](#ch13)
1. [Filter Slicers](#ch14)
1. [Line and Bar Charts for the Attrition Page](#ch15)
1. [Final presentation of Attrition page](#ch16)

<a id="ch1"></a>
## Introduction
This Microsoft PowerBI project is designed to assess the application of essential analytical and decision-making skills through the end-to-end process of data modelling, analysis and interpretation. I leverage the Microsoft PowerBI to design and develop insightful, interactive data visualizations, with a specific focus on HR analytics. This project centers on analyzing employee attrition and performance data to uncover trends, identify key drivers and support evidence-based workforce planning and strategic decision-making.

In the Microsoft Power BI Desktop, I import the data by connecting to a relevant data source (Excel workbooks) containing the following tables: Education, Attrition Rates, Employee Data 2018 to 2019, Job Involvement, Performance Rating, Satisfaction and Work_Life_Balance. I then loaded each of these tables into the Power BI model using the Get Data functionality and ensuring that all the data types are correctly inferred and that any unnecessary columns or rows are removed during the initial transformation stage in Power Query Editor. I had also verified the integrity and granularity of each table to support subsequent data modeling, relationship establishment and analytical reporting.

<a id="ch2"></a>
# Dataset Overview
The dataset consist of Attrition rate, Education, Employee Data, Job Involvement, Performance rate, Satisfaction & Work Life Balance. The dataset can be found here: [Dataset](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Dataset/HRAnalyticsEmployeeAttritionPerformance.csv)

## Attrition rate

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR1.png)

## Employee Data
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR2.png)

## Education 
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR3.png)

## Job Involvement 
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR4.png)

## Performance Rating
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR7.png)

## Satisfaction 
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR8.png)

## Work Life Balance
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR9.png)

<a id="ch3"></a>
## 1. Data Cleaning

The reliability of measures and fields is greatly enhanced through effective data cleaning. Removing duplicate records simplifies data exploration and results in well-structured columns that can be confidently used as slicers and filters. Complex fields can also be split into more interpretable columns, or multiple related columns can be merged to improve clarity and usability.

By default, Power Query profiles only the first 1,000 rows of data. To ensure comprehensive analysis, the profiling setting should be updated via the status bar by selecting Column profiling based on entire data set, allowing the profiling process to reflect the complete dataset.

## Attrition (Before cleaning - with empty rows) 
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR9a.png)

## Attrition (After cleaning - became more readable and straightforward.) 
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR9b.png)

## Emplyee Data (Before cleaning - with empty rows) 
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR10.png)

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR11.png)

## Emplyee Data (Empty rows removed)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR12.png)

## Employee Data 2018-2025 cleaning columns by using choosing column function
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR13.png)

## Blank columns removed
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR13b.png)

<a id="ch4"></a>

# 2.	Data Transformations Applied
## Attrition rate (adding year column)

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR14.png)

## Attrition rate (insert quarter column)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR15.png)

## Rename Monthly income title (before)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR17.png)

## Monthly income (after using replace value)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR18.png)

## Multiply by 100000 to Monthly income column (Transform -> Standard -> Multiply)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR19.png)

## Choose Fixed decimal format
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR20.png)

## Set currency
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR21.png)

## Final presentation of Monthly income column
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR22.png)

<a id="ch5"></a>

## 3.	Created Columns and Measures
Data Analysis Expressions (DAX) provides the ability to build three distinct calculation types for your semantic model:
•	Calculated tables
•	Calculated columns
•	Measures
## Create the Agebin by adding new column
We can write a DAX formula to add a calculated column to the model.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR23.png)

## Ensure date/time format for Attrition rate

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR24.png)

Measures function as model elements that summarize data. We can write a DAX formula to add a measure to any table in the model. The formula is concerned with achieving summarization over model data. Like calculated column, the formula must return a single value. Measures are only evaluated at query time and their results are never stored in the model.
Created the Measure table for ActiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR25.png)

## Insert DAX for ActiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR26.png)

## Insert DAX for InactiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR26b.png)

## Create another new measure under the Measure table for TotalEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR27.png)

## Insert DAX for TotalEmployee measure

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR28.png)

## Create another new measure for %Attrition

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR29.png)

## Insert DAX for %Atrition

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR30.png)

## Create a presentation for all the measures using a multi-row card

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR32.png)

## Set %Attrition to percentage

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR33.png)

## Final Presentation

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR34.png)

<a id="ch6"></a>

# 4. Data Model
Power BI enables the creation of relationships across tables sourced from different systems, providing a powerful capability to integrate data from Microsoft Excel with tables from relational databases. Once these relationships are established, the tables can be linked and used collectively as a single, integrated semantic model for analysis and reporting.

## a)Link "Education" to "Employee Data"
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR35.png)

## There is already a relationship exists.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR36.png)

## Link "Job Involvement" to "Employee Data"

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR37.png)

## There is already a relationship exists.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR38.png)

## Link "Performance Rating" to "Employee Data

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR39.png)

## Link "Satisfaction" to "Employee Data

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR40.png)

## Link "WorkLifeBalance" to "Employee Data

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR41.png)

## There is already a relationship exists

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR42.png)

## Overview of the five relationships

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR43.png)

<a id="ch7"></a>

# 5.	Created Hierarchies
Created a hierachy under agebin

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR44.png)

## Relabelled the newly created hierarchy as ‘Employee Data”

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR45.png)

## Added the Department to Employee Data

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR46.png)

## Also added Job role to Employee Data

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR47.png)

## Final presentation of the hierarchy

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR48.png)

<a id="ch8"></a>

# 6. Data Relationships
A well-designed data model adheres to star schema principles when defining relationships between tables. This design approach is widely adopted in relational data warehousing because it provides a clear and intuitive structure while supporting high-performance analytical queries.

In Microsoft Power BI, only one active relationship can exist between any two tables and represented by a solid line in the model view. This active relationship automatically controls filter propagation. Any additional relationships between the same tables remain inactive and are indicated by dashed lines.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR48.png)

<a id="ch9"></a>
# 7. KPI Cards
Key Performance Indicators (KPIs) are valuable tools for tracking performance and measuring progress against predefined targets over time. Numeric values, often presented using card visuals, act as high-priority indicators that immediately draw attention. They are highly effective in dashboards and analytical reports, as they convey critical information at a glance.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR49a.png)

<a id="ch10"></a>
# 8.	Bar Chart
   
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR49.png)

<a id="ch11"></a>
# 9.	Stacked Bar Chart
    
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR51.png)

Drillthrough pages enable report users to navigate from a visual to a more detailed report page. By default, the drillthrough feature transfers all filters applied to the selected visual onto the target drillthrough page. When a report is designed with drillthrough functionality, users can seamlessly move from one visual element to another report page to access deeper insights and contextual information.

Before Drillthrough Mode:

Y-axis: Department & Job Role

X-axis: Active Employees

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR52.png)

<a id="ch12"></a>
# 10.	KPI Cards for Demographics Page.
    
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR53.png)

## Created a barchart with Agebin and Totalemployee (not sorted)

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR54.png)

## Amend the DAX for Agebin

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR55.png)

## Sort the barchart by Agebin

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR56.png)


![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR57.png)

## Sort the barchart by Ascending order

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR58.png)

## Final presentation

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR58a.png)

## Marital status of the total employee pie chart created.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR59.png)

<a id="ch13"></a>
# 13.	Combined Chart.
Line and stacked column chart was selected

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR60.png)

## Agebin,department and jobrole were first selected

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR61.png)

## Follow by the monthly income (average)

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR62.png)

## Final presentation

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR63.png)

<a id="ch14"></a>
# 14. Filter Slicers
Slicers provide a user-friendly interface for navigating reports and are among the most commonly used interactive features in Power BI. They allow users to easily apply, modify, or remove filters, and the built-in search functionality enables rapid identification of specific items for filtering. Due to their simplicity and effectiveness in enabling data exploration, slicers are one of the most widely implemented visuals on report pages.

In this report, a slicer was created using Employee ID to facilitate targeted data filtering.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64a.png)

## Bar Chart
Max value for Education

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64.png)

## Max value for job satisfaction

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64b.png)

## Max value for Job Involvement 

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR65.png)

## Max value for Relationship Satisfaction 

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR66.png)

## Max value for Performance Rating

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR67.png)

## Max value for Work Life Balance 

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR68.png)

## Max value for Environment Satisfaction

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR69.png)

## Added gauges for performance rating and work life balance in the Performance Tracker page

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR70.png)

<a id="ch15"></a>
# 15. Line and Bar Charts for the Attrition Page
Line or column charts should be used when visualizing values across time periods, as they effectively highlight trends and changes over time. The X-axis should represent time in a clear chronological sequence, arranged from the earliest to the most recent periods (left to right), to ensure accurate interpretation and readability.

# The total attrition rate is 16.12%

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR71.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR72.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR73.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR74.png)

<a id="ch16"></a>
## Final presentation of Attrition page
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR75.png)




