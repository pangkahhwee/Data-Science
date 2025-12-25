![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR90.png)

# Powering HR Insights: Visualizing Employee Attrition & Performance in Power BI
This PowerBI project designed to assess the application of essential analytical and decision-making skills through the end-to-end process of data modelling, analysis and interpretation. I leverage the PowerBI to design and develop insightful, interactive data visualizations, with a specific focus on HR analytics. This project centers on analyzing employee attrition and performance data to uncover trends, identify key drivers and support evidence-based workforce planning and strategic decision-making.

In the Microsoft Power BI Desktop, I import the data by connecting to a relevant data source (Excel workbooks) containing the following tables: Education, Attrition Rates, Employee Data 2018 to 2019, Job Involvement, Performance Rating, Satisfaction, and Work_Life_Balance. Load each of these tables into the Power BI model using the Get Data functionality, ensuring that data types are correctly inferred and that any unnecessary columns or rows are removed during the initial transformation stage in Power Query Editor. Verify the integrity and granularity of each table to support subsequent data modeling, relationship establishment and analytical reporting.

# Dataset Overview
The dataset consist of Attrition rate, Education, Employee Data, Job Involvement, Performance rate, Satisfaction & Work Life Balance

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

## 3.	Created Columns and Measures
Data Analysis Expressions (DAX) provides the ability to build three distinct calculation types for your semantic model:
•	Calculated tables
•	Calculated columns
•	Measures
## Create the Agebin by adding new column
We can write a DAX formula to add a calculated column to the model.

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR23.png)

Ensure date/time format for Attrition rate

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR24.png)

Measures function as model elements that summarize data. We can write a DAX formula to add a measure to any table in the model. The formula is concerned with achieving summarization over model data. Like calculated column, the formula must return a single value. Measures are only evaluated at query time and their results are never stored in the model.
Created the Measure table for ActiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR25.png)

Insert DAX for ActiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR26.png)

Insert DAX for InactiveEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/HR/HR26b.png)

Create another new measure under the Measure table for TotalEmployee

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR27.png)

Insert DAX for TotalEmployee measure

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR28.png)

Create another new measure for %Attrition

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR29.png)

Insert DAX for %Atrition

![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR30.png)


![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR31.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR32.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR33.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR34.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR35.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR36.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR37.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR38.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR39.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR40.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR41.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR42.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR43.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR44.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR45.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR46.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR47.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR48.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR49.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR49a.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR50.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR51.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR52.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR53.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR54.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR55.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR56.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR57.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR58.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR59.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR60.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR61.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR62.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR63.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64a.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR64b.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR65.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR66.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR67.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR68.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR69.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR70.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR71.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR72.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR73.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR74.png)
![Man_coughing.jpg](https://github.com/pangkahhwee/Microsoft_PowerBi/blob/main/image/HR/HR75.png)




