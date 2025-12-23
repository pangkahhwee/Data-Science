![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid1.png)

The project aims to leverage Python for comprehensive data analysis and visualization. Using the “Our World in Data” dataset, I will explore metrics like cases, deaths, vaccinations and testing across countries. The primary focus is on applying core Python data science libraries: Pandas for data manipulation and Matplotlib and Seaborn for visualization. I will progress through seven key activities, starting with data loading and cleaning data. I will then perform exploratory analysis to understand global and regional trends over time. I will create visualizations like bar charts, line plots and heatmaps to uncover patterns. I will also conduct time-series analysis of daily cases and vaccination rates. A significant component involves in-depth country-specific analysis based on user input. This project further explores derived metrics such as fatality and positivity rates and I will investigate potential correlations with external factors like smoking rates and hospital bed availability. This hands-on project is designed to solidify my practical skills in data cleaning, feature engineering, statistical exploration and effective data storytelling through visualization.

## Table of Contents
1. [Step 1 - Project Overview](#ch1)
1. [Step 2 - Data Science Steps](#ch2)
1. [Step 3 - Problem Definition](#ch3)
1. [Step 4 - Data Gathering](#ch4)
1. [Step 5 - Data Preparation](#ch5)
1. [Step 6 - Explanatory Data Analysis (EDA)](#ch6)
1. [Step 7 - Data Visualisation using Pandas, Matplotlib and Seaborn](#ch7)
1. [Step 8 - Conclusion](#ch8)


<a id="ch1"></a>
# Project Overview
COVID-19 is a highly infectious respiratory disease caused by the SARS-CoV-2 virus, first detected in Wuhan, China, in December 2019. It quickly spread across the globe, developing into a pandemic that affected millions of people and placed extraordinary pressure on healthcare systems, economies and everyday life. Typical symptoms include fever, coughing, breathing difficulties, fatigue and loss of taste or smell, with cases ranging from mild illness to severe, life-threatening conditions. Measures such as vaccination, mask use, social distancing and enhanced hygiene practices have played a vital role in reducing transmission and limiting its overall impact, Covid: Prediction the number of death (smoker and non-smoker). I am focusing on predicting the number of casualties of Covid including their lifestyles: smoking or not by following a structured workflow: defining the problem, collecting, cleaning and preparing the data, performing exploratory data analysis, building a model, validating its performance and further optimizing it.

Let's take a look at the steps:

<a id="ch2"></a>
## Data Science Steps
1. **Problem Definition:** Addresses the critical need for clear, timely and accurate understanding of regional trends in cases and deaths by performing a comprehensive, reproducible analysis and visualization.
2. **Data Gathering:** I got the dataset from the website.
3. **Data Preparation:** I cleaned the dataset by remove the duplicates and blanks or outliers.
4. **EDA (Exploratory Data Analysis):** Poor quality data inevitably leads to poor outcomes. Therefore, it is essential to apply descriptive and visual statistical techniques to uncover patterns, relationships and meaningful comparisons within the dataset. At this stage, the data will be examined to ensure it is clear, consistent and analytically meaningful before proceeding further.
5. **Data Visualisations:** Pictures tell a thousand words. A good charts or graph is able to let audiences understand the whole situations easily. 
6. **Validate Model:** I will evaluate its performance and assessed after training as whether it showed signs of overfitting or underfitting.
7. **Optimize Model:** I improved the model by applying techniques such as hyperparameter optimization to enhance its performance.

<a id="ch3"></a>
## Step 1: Problem Definition
The ongoing global impact of the COVID-19 pandemic has generated vast amounts of public health data yet transforming this data into actionable insights remains a critical challenge. Decision-makers require clear, timely and accurate understanding of trends in cases and deaths across different regions to inform policy, allocate resources and communicate risks effectively. In this context, there is a need to systematically analyze and visualize worldwide COVID-19 data to uncover patterns, monitor regional disparities and support evidence-based responses. This project seeks to address that need by performing a comprehensive, reproducible analysis of global pandemic data using Python-based data science and visualization tools.

## Project Summary
This capstone project undertakes a comprehensive analysis and visualization of global COVID-19 data to support data-driven understanding of the pandemic’s evolution across regions. Leveraging Python’s data science ecosystem including pandas for data manipulation, Matplotlib and Seaborn for visualization and Jupyter for reproducible reporting, the project processes publicly available datasets to clean, structure and analyze key metrics such as total cases and deaths by WHO region (represented as continents in the dataset). The analysis includes handling missing values, removing duplicates, standardizing geographic classifications and aggregating statistics to enable meaningful cross-regional comparisons. The resulting visualizations, primarily in the form of informative bar plots, aim to highlight disparities in pandemic impact and provide stakeholders with intuitive, actionable insights to inform public health decisions and strategic planning.

<a id="ch4"></a>
## Step 2: Data Gathering

The dataset can be found here: [COVID-19 dataset via Our World in Data's data catalog](https://catalog.ourworldindata.org/garden/covid/latest/compact/compact.csv)

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid2.PNG)

I begin by importing the required dataset from its source from the URL. Next, I load the imported data into a structured format compatible with the analysis environment, a pandas DataFrame in Python. I have verified that the data has been successfully downloaded and properly formatted by inspecting its schema, dimensions and initial rows.

<a id="ch5"></a>
## Step 3: Data Preparation
I focused on cleaning it up and use it for my Data Science.


## 3.1 Import Libraries
I will begin my project with importing the libraries first.

```
import sys 

import pandas as pd 
import matplotlib 

import numpy as np 
import scipy as sp 

import matplotlib as mpl
import matplotlib.pyplot as plt
import matplotlib.pylab as pylab
import seaborn as sns
from pandas.plotting import scatter_matrix
```

## Core Libraries 

pandas (pd): Data manipulation and analysis with DataFrames

numpy (np): Numerical computing with arrays and matrices

scipy (sp): Scientific computing (statistics, optimization, etc.)

matplotlib: Data visualization and plotting

sys: System-specific pparameters and functions



## Visualization

matplotlib/pyplot/pylab: Creating various plots and charts

seaborn (sns): Statistical data visualization with attractive defaults

scatter_matrix: Creates a grid of scatter plots for multiple variables

## 3.2 Preview of the Data
To gain an initial understanding of the dataset’s structure, I display the first five rows of the DataFrame using the .head() method. Similarly, I inspected the last five rows by invoking the .tail() method to observe how the data concludes.
This dual preview helps identify patterns, anomalies or inconsistencies at both ends of the dataset.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid3.PNG)

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid4.PNG)

## 3.3 Data Pre-processing: 
I began by identifying and removing anomalies and statistical outliers that could distort analytical outcomes, ensuring the dataset’s integrity. Where ddata gaps existed, I carefully imputed missing values using contextually appropriate strategies—such as mean substitution, forward fill or model-based imputation—depending on the nature of the variables. Additionally, I engineered new features to improve model relevance and applied essential transformations, including normalization, encoding categorical variables and scaling, to align the data with analytical requirements.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid5.PNG)

First, I calculated the proportion of missing values in each column of the DataFrame to assess data completeness.
Next, I identified all columns where the percentage of missing values exceeds the 90% threshold as these are unlikely to contribute meaningful information. Finally, I permanently remove those columns from the DataFrame to streamline the dataset and improve computational efficiency for subsequent analysis.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid6.PNG)

For numerical columns, I applied suitable imputation techniques such as replacing missing entries with the mean, median or a value derived from more advanced methods like K-nearest neighbors (KNN) or regression. For categorical columns, I use the mode or introduce a new category like “Unknown” when appropriate. Finally, document the imputation approach for each feature, validate that the imputed values preserve the underlying data distribution and ensure reproducibility by encapsulating the logic in a preprocessing pipeline or function.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid8.PNG)

I ensure that the 'date' column exists in my DataFrame and contains values that represent dates in a recognizable format (e.g strings like '2023-12-25' or '12/25/2023'). Then, I use pandas’ pd.to_datetime() function to convert the column’s data type from its current form—often object (string) to the datetime64 data type, which enables efficient date-based operations such as sorting, filtering by time ranges and extracting components like year, month or day. This conversion also validates the date entries, automatically parsing them into a standardized temporal format and optionally handling errors (e.g. by coercing invalid dates to NaT—Not a Time—if specified), thereby enhancing both data quality and analytical capability.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid7.PNG)

I identifying duplicate rows in the DataFrame using the .duplicated() method, which returns a Boolean Series indicating which rows are exact duplicates of earlier ones. Next, I used the .drop_duplicates() method to remove these redundant entries, optionally specifying a subset of columns to consider if full-row duplication is not required or if duplicates should be evaluated based on key identifiers only. Finally, after verify that the operation was successful by comparing the DataFrame’s shape before and after removal, I ensured data integrity is maintained while eliminating redundancy that could otherwise bias analysis or modeling outcomes.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid9.PNG)

I selected the column that contains country information that typically labeled 'country' and extract all distinct country entries present in the dataset. Next, I wrote a programming(Python) to the same column to obtain a precise count of how many unique countries are represented, which provides a quantitative measure of geographic diversity. 

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid10.PNG)

I grouped the dataset according to the 'Continent' column (which represents WHO regions) and aggregating the total number of confirmed COVID-19 cases and total deaths for each region. Next, I created two separate bar plots—one displaying the total cases and the other the total deaths per WHO region—using a visualization library such as Matplotlib or Seaborn, ensuring that each bar is clearly labeled, axes are appropriately titled and the plots are visually distinct for easy interpretation.
Finally, I analyze the resulting visualizations to identify regional disparities in pandemic impact and consider enhancing the plots with annotations, color coding or sorting by magnitude to improve clarity and communicative effectiveness.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid11.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid12.PNG)


I aggregating the global COVID-19 case data on a monthly basis by summing or otherwise consolidating daily case counts into total or average monthly figures—to capture temporal patterns over time. I will then use a line plot, created with a visualization library such as Matplotlib or Seaborn in Python, to graphically represent these monthly case totals across the entire pandemic period with time (e.g month-year) on the x-axis and the number of cases on the y-axis. I enhance the plot with appropriate labels, a descriptive title, gridlines for readability and potentially annotations for significant events (e.g variant surges or policy changes) to facilitate clear interpretation of global trends and inform public health insights.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid13.PNG)

I selected the relevant numerical columns, typically 'total_cases' and 'total_deaths' from the dataset and ensuring they are properly cleaned and formatted to avoid distortions in correlation measurement. I then compute the correlation coefficient between these two variables using pandas’ .corr() method, which quantifies the strength and direction of their linear relationship. Finally, I visualize this correlation using a heatmap—generated via Seaborn’s heatmap() function where the intensity of the color (e.g from cool to warm tones) reflects the magnitude of the correlation, accompanied by clear axis labels and an annotated correlation value to enhance interpretability and support evidence-based conclusions about the association between infections and fatalities.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid14.PNG)

I preprocessed the dataset to ensure the date column is in datetime format, then I extracted the month (and optionally year) and combine it with the continent (or WHO region) column to create a structured grouping key. I sum or averaging the 'new_cases' for each unique combination of continent and month, resulting in a pivot-style summary that captures monthly case trends across regions. Then I generate a grouped (or clustered) bar chart—using a library such as Matplotlib or Seaborn where each cluster represents a month and within each cluster, individual bars correspond to continents, enabling clear visual comparison of new case distributions over time and geography to enhance the chart with appropriate labels, a legend, and a descriptive title for clarity and impact.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid16.PNG)

Extracting the year from the date column in the dataset—ensuring the column is in datetime format—and then group or assign each record to its corresponding calendar year. Next, I constructed a box plot (also known as a box-and-whisker plot) using a visualization library such as Matplotlib or Seaborn, with the x-axis representing each year and the y-axis showing the distribution of total COVID-19 cases; this plot will illustrate the median, interquartile range, potential outliers and overall spread of case counts for each year.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid17.PNG)

Aggregating the dataset to compute the sum of total deaths for each continent (or WHO region), ensuring that the continent column is consistently labeled and any missing or ambiguous entries are resolved. I created a bar plot using a visualization library such as Matplotlib or Seaborn, where the x-axis lists the continents and the y-axis represents the cumulative number of deaths, with each bar’s height reflecting the total mortality burden in that region. I enhanced the plot with clear axis labels, a descriptive title, value annotations on top of each bar (if space permits) and a consistent color scheme to enable straightforward visual comparison and effective communication of intercontinental disparities in pandemic-related fatalities.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid18.PNG)

The dataset contains a properly formatted date column, then extract the month (if applicable, the year) to create a time-based grouping key for aggregation. Sum the 'total_cases' or 'new_cases' (depending on data structure) for each unique month to obtain monthly case totals, which will serve as the basis for temporal trend analysis. Visualize these aggregated monthly case counts using a bar plot—implemented with Matplotlib, Seaborn or a similar library where the x-axis represents the months (e.g "Jan 2020", "Feb 2020" etc.) and the y-axis shows the number of cases with bars ordered chronologically to clearly reveal patterns, peaks, and declines in case incidence over time.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid19.PNG)

My interpretation: This plot shows seasonal or wave patterns, if January or October show peaks, it may reflect winter waves or Delta/Omicron surges that repeatedly occurred in those months across years.

I ensure that the dataset contains daily records of new COVID-19 cases and deaths with a properly formatted date column in datetime type to enable chronological sorting and alignment. Next, I aggregated the data at the global level by summing new cases and new deaths for each unique date, resulting in two time series that reflect worldwide daily incidence and mortality.
Finally, I created a dual line plots either overlaid in a single chart with dual y-axes or presented in aligned subplots using library such as Matplotlib or Seaborn, where the x-axis represents time (date) and the y-axes represent the counts of new cases and new deaths, respectively. This enhance the plots with clear labels, a descriptive title, gridlines and smoothing (if appropriate) to reveal trends, surges and correlations in the global pandemic trajectory.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid20.PNG)

I identifying and extracting the relevant columns from the dataset that capture vaccination metrics such as total vaccinations, people fully vaccinated or vaccination rates alongside a properly formatted date column to track changes over time. Next, I aggregated the data at the global level by summing or averaging vaccination figures for each date, ensuring consistent handling of missing values and adjustments for population size if analyzing coverage rates rather than raw counts.
Finally, I visualize the resulting time series using a line plot (or stacked area chart for multiple vaccine metrics), with time on the x-axis and vaccination coverage on the y-axis and enhance the plot with clear labeling, annotations for major milestones (e.g vaccine rollout phases or policy changes) and contextual references to effectively illustrate the pace, scale and progression of global vaccination efforts throughout the pandemic.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid22.PNG)

I identified the relevant columns in the dataset that record daily or cumulative figures for total tests conducted and the number of positive cases, ensuring the date column is in proper datetime format to enable chronological analysis.I aggregated these metrics at the global level for each time point by computing the total number of tests administered worldwide per day or cumulative total and deriving the daily or rolling positive rate as the ratio of new positive cases to new tests (typically expressed as a percentage). Finally, I visualize both trends over time using dual-axis line plots or synchronized subplots: one showing the volume of testing and the other displaying the positivity rate, with clear annotations, axis labels and potentially smoothing techniques to highlight key patterns such as testing capacity expansion, surges in transmission or shifts in pandemic response strategy on a global scale.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid23.PNG)

I begin by ensuring the dataset contains daily or cumulative records of global total cases and total deaths, with a properly formatted date column to track changes over time. Next, I computed the fatality rate for each time point by dividing the cumulative number of deaths by the cumulative number of confirmed cases (commonly expressed as a percentage), taking care to handle division by zero or periods of very low case counts to avoid spurious spikes; optionally apply a rolling average to smooth short-term volatility and reveal underlying trends. Then I visualize the resulting time series using a line plot created with time (date) on the x-axis and the fatality rate (%) on the y-axis, enhanced with a clear title, axis labels, gridlines and contextual annotations (e.g emergence of variants or changes in testing policy) to effectively communicate how the global risk of death among confirmed cases has evolved throughout the pandemic.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid28.PNG)

<a id="ch8"></a>

## Conclusion

This capstone project successfully leveraged Python based data science tools primarily Pandas, Matplotlib and Seaborn to conduct a comprehensive, end-to-end analysis of global COVID-19 data sourced from Our World in Data. Through systematic data cleaning, feature engineering and exploratory data analysis, key insights were uncovered regarding the pandemic’s evolution across time, geography and public health indicators.

The visualizations revealed significant regional disparities: while Asia reported the highest total cases, Europe and the Americas experienced the greatest mortality burden. Temporal analyses highlighted major infection waves, particularly the Omicron surge in early 2022 and demonstrated a global trend toward stabilization and endemicity by 2023–2024. Derived metrics such as fatality and positivity rates illustrated how improved testing, vaccination coverage and clinical management reduced lethality over time, even as case numbers fluctuated.

Furthermore, correlation analyses between health system factors (e.g hospital beds, smoking rates) and outcomes showed limited direct relationships, underscoring the complex interplay of demographic, socioeconomic and policy-driven variables in pandemic impact. Interactive elements such as user-driven country and metric selection, enhanced the project’s utility for tailored exploration.

Overall, this project not only fulfilled the learning objectives of using Data Science to demonstrating proficiency in data manipulation, statistical exploration and data storytelling but also delivered actionable, visually compelling insights that reflect the dynamic global response to one of the most significant public health crises of the 21st century.


