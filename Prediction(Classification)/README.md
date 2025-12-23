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
1. **Problem Definition:** What factors influenced survival in a disaster? By analyzing passenger data, we are able to identify specific groups that had a higher likelihood of survival.
2. **Data Gathering:** I got the dataset from a website.
3. **Data Preparation:** I cleaned the dataset by remove the duplicates and blanks or outliers.
4. **EDA (Exploratory Data Analysis):** If poor quality data is fed into a system, the results will be equally poor. That is why it is important to apply descriptive and visual statistics to uncover patterns, relationships and comparisons within the dataset. At this stage, I will examine the data to ensure whether it is clear, consistent and meaningful.
5. **Data Visualisations:** Pictures tell a thousand words. A good charts or graph is able to let audiences understand the whole situations easily. 
6. **Validate Model:** I will evaluate its performance and assessed after training as whether it showed signs of overfitting or underfitting.
7. **Optimize Model:** I improved the model by applying techniques such as hyperparameter optimization to enhance its performance.

<a id="ch3"></a>
## Step 1: Problem Definition
The objective of this project is to predict the number of passengers on the Titanic survived when the sinking disaster striked.

## Project Summary
The Titanic disaster is one of the most well-known maritime tragedies in history. On April 15, 1912, the RMS Titanic sank after striking an iceberg. Although it was widely believed to be unsinkable, the ship was lost due to the collision. With insufficient lifeboats on board, 1,502 out of the 2,224 passengers and crew members lost their lives.

Certain groups of passengers appeared to have a higher likelihood of survival than others, though luck also played a role. In this challenge, the objective is to develop a predictive model that determines an individual’s probability of survival based on passenger data such as name, age, gender, social class and other relevant attributes.

<a id="ch4"></a>
## Step 2: Data Gathering

The dataset can be found here: [Titanic: Exploratory Data Analysis with Python Pandas](https://github.com/pangkahhwee/Data-Science/blob/09fb04dea0764ced3fc80ebe0a9b68e480891a98/Image/Dataset/titanic.csv)

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid2.png)

I begin by importing the required dataset from its sourcefrom the URL. Next, I load the imported data into a structured format compatible with the analysis environment— a pandas DataFrame in Python. I verify that the data has been successfully downloaded and properly formatted by inspecting its schema, dimensions and initial rows.

<a id="ch5"></a>
## Step 3: Data Preparation
The data was downloaded into my Github, so I only focused on cleaning it up and use it for my Data Science.


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
Finally, analyze the resulting visualizations to identify regional disparities in pandemic impact and consider enhancing the plots with annotations, color coding or sorting by magnitude to improve clarity and communicative effectiveness.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid11.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid12.PNG)




<a id="ch6"></a>
## Step 4: Explanatory Data Analysis (EDA)

Following data cleaning and organization, I conducted Exploratory Data Analysis (EDA) to examine the dataset, using visualizations to gain a deeper understanding of its characteristics, underlying patterns and statistical properties.



Identify the number of passengers in each individual passenger class:



I created a new column named 'FamilySize' that represents the sum of 'SibSp' and 'Parch'.
Drop the 'Cabin' column from the dataset:



Next, I created a new DataFrame containing only passengers with an age greater than 30.
Sort the DataFrame by 'Fare' in descending order:



I also calculated the survival rate for different passenger classes ('Pclass').
Identify and display the passenger with the highest 'Fare':




![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid13.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid14.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid15.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid16.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid17.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid18.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid19.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid20.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid21.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid22.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid23.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid24.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid25.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid26.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid27.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid28.PNG)
![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid29.PNG)

<a id="ch7"></a>
## Step 7 - Data Visualisation using Pandas, Matplotlib and Seaborn
### 7.1 Visualize passenger survival rate
I created a bar plot using seaborn to display the count of survivors and non-survivors.

![Man_coughing.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Covid19/Covid11.png)

My interpretation:
1.   0 = Not survived
2.   1 = Survived

There are lesser passengers who survived in this disaster.

### 7.2 Visualize passenger survival rate


### 7.3: Analyze Passenger Age Distribution

I constructed a histogram using matplotlib to show the distribution of passenger ages.

![Idata_characteristics.jpg](/Image/Titanic/titanic12.PNG) 

### 7.4: Visualize Passenger Class and Age

I built a scatter plot using matplotlib to show the relationship between passenger age and class.

![Idata_characteristics.jpg](/Image/Titanic/titanic13.PNG) 

My intrepretation:
1.   Elderly are mostly in 1st class.
2.   Most younger age groups are in the 3rd class.
3.   Younger and middle age group spread across all classes.

<a id="ch8"></a>
## Conclusion

The ananlysis of the Titanic dataset reveals clear differences in survival rates across passenger classes. First class passengers had the highest survival rate (=63%), followed by second-class (=47%), while third-class passengers had the lowest survival rate(=24%). This suggests that socio-economic status played a significant role in survival chances.
Additionally, the passengers with the highest fare (512.33) was Ward, Miss Anna, a 3 years old female travelling inn first class, who survived.This highlights the association between higher ticket cost, travel class and increased livelihood  of survival. 

