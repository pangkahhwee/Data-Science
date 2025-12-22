![titanic.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Titanic/titanic1.jpg.png?raw=true)

I am performing exploratory data analysis (EDA) on the Titanic dataset using Pandas. This dataset contains detailed information about the passengers aboard the Titanic, including demographic attributes and their survival status. The primary objective of my analysis is to uncover meaningful insights into the characteristics and patterns of the passengers, helping to better understand factors that may have influenced their chances of survival. 

## Table of Contents
1. [Chapter 1 - Project Overview](#ch1)
1. [Chapter 2 - Data Science Steps](#ch2)
1. [Chapter 3 - Step 1: Problem Definition](#ch3)
1. [Chapter 4 - Step 2: Data Gathering](#ch4)
1. [Chapter 5 - Step 3: Data Preparation](#ch5)
1. [Chapter 6 - Step 4: Explanatory Data Analysis (EDA)](#ch6)
1. [Chapter 13 - Conclusion](#ch7)


<a id="ch1"></a>
# Project Overview
In this project, I selected a widely used classification task with binary outcomes: either 0 or 1 where an event either occurs or does not. Examples include whether it will rain tomorrow or whether a production component is functioning or not.

I worked with a project based on my interest after watching a movie, Titanic: Exploratory Data Analysis with Pandas, Matplotlib and Seaborn. I am concentrating on predicting passenger survival outcomes by following a structured workflow: defining the problem, collecting, cleaning and preparing the data, performing exploratory data analysis, building a model, validating its performance and further optimizing it.

Let's take a look at the steps:

<a id="ch2"></a>
## Data Science Steps
1. **Problem Definition:** What factors influenced survival in a disaster? By analyzing passenger data, we are able to identify specific groups that had a higher likelihood of survival.
2. **Data Gathering:** I got the dataset from a website.
3. **Data Preparation:** I cleaned the dataset by remove the duplicates and blanks or outliers.
4. **EDA (Exploratory Data Analysis):** If poor quality data is fed into a system, the results will be equally poor. That is why it is important to apply descriptive and visual statistics to uncover patterns, relationships and comparisons within the dataset. At this stage, I will examine the data to ensure whether it is clear, consistent and meaningful.
5. **Data Modeling:** Choosing the right model is important. If an inappropriate model is selected for a given use case, the effectiveness of all subsequent steps is compromised. 
6. **Validate Model:** I will evaluate its performance and assessed after training as whether it showed signs of overfitting or underfitting.
7. **Optimize Model:** I improved the model by applying techniques such as hyperparameter optimization to enhance its performance.

<a id="ch3"></a>
## Step 1: Problem Definition
The objective of this project is to predict the number of passengers on the Titanic survived when the sinking disaster striked.

**Project Summary**
The Titanic disaster is one of the most well-known maritime tragedies in history. On April 15, 1912, the RMS Titanic sank after striking an iceberg. Although it was widely believed to be unsinkable, the ship was lost due to the collision. With insufficient lifeboats on board, 1,502 out of the 2,224 passengers and crew members lost their lives.

Certain groups of passengers appeared to have a higher likelihood of survival than others, though luck also played a role. In this challenge, the objective is to develop a predictive model that determines an individual’s probability of survival based on passenger data such as name, age, gender, social class and other relevant attributes.

<a id="ch4"></a>
## Step 2: Data Gathering

The dataset can be found here: [Titanic: Exploratory Data Analysis with Python Pandas](https://github.com/pangkahhwee/Data-Science/blob/09fb04dea0764ced3fc80ebe0a9b68e480891a98/Image/Dataset/titanic.csv)

![Downloading_data.jpg](/Image/Titanic/titanic1.PNG) 

<a id="ch5"></a>
## Step 3: Data Preperation
The data was downloaded into my Github, so I only focused on cleaning it up and use it for my Data Science.

![Downloading_data.jpg](/Image/Titanic/titanic2.png) 

## 3.1 Import Libraries

```
import sys 

import pandas as pd 
import matplotlib 

import numpy as np 
import scipy as sp 

import IPython
import sklearn 

import random
import time

from subprocess import check_output

from sklearn import svm, tree, linear_model, neighbors, naive_bayes, ensemble, discriminant_analysis, gaussian_process
from xgboost import XGBClassifier

from sklearn.preprocessing import OneHotEncoder, LabelEncoder
from sklearn import feature_selection
from sklearn import model_selection
from sklearn import metrics

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

IPython: Enhanced interactive Python (typically used in Jupyter notebooks)

sys: System-specific pparameters and functions

## Machine Learning (sklearn) 

The code imports a wide range of scikit-learn algorithms:

Classifiers: SVM, decision trees, linear models, k-nearest neighbors, naive Bayes, ensemble methods (like Random Forest), discriminant analysis, and Gaussian processes

XGBoost: A powerful gradient boosting library (imported separately)

Preprocessing: OneHotEncoder (converts categorical variables to binary columns) and LabelEncoder (converts labels to numbers)

Feature selection: Tools to identify the most important features

Model selection: Cross-validation and hyperparameter tuning utilities

Metrics: Performance evaluation (accuracy, precision, recall, etc.)

## Visualization

matplotlib/pyplot/pylab: Creating various plots and charts

seaborn (sns): Statistical data visualization with attractive defaults

scatter_matrix: Creates a grid of scatter plots for multiple variables

This setup is typical for Kaggle competitions or exploratory data analysis projects where you want many ML algorithms available to experiment with.

## Utilities

random and time: Random number generation and timing operations
check_output: Executes shell commands from Python

This setup is typical for Kaggle competitions or exploratory data analysis projects where many ML algorithms available to experiment with.

## 3.2 Preview of the Data
I have displayed the first 5 and last 5 rows of the DataFrame here to validate that I had download the corrct dataset. Also, the survived variable serves as the outcome (or dependent) variable, coded as 1 if the passenger survived and 0 if they did not. All other variables are independent (predictor) variables. While most variable names are self-explanatory, two merit clarification: SibSp denotes the number of siblings or spouses aboard the Titanic and Parch indicates the number of parents or children aboard the vessel.

![Downloading_data.jpg](/Image/Titanic/titanic3.PNG) 

<a id="ch5"></a>
## 3.3 Data Pre-processing: 
I performed data cleaning by removing anomalies and outliers, imputing missing values where appropriate, enhancing features and carrying out necessary data transformations. 

![Downloading_data.jpg](/Image/Titanic/titanic4.PNG) 

<a id="ch6"></a>
## Step 4: Explanatory Data Analysis (EDA)

Following data cleaning and organization, I conducted exploratory data analysis (EDA) to examine the dataset, using visualizations to gain a deeper understanding of its characteristics, underlying patterns and statistical properties.

![Downloading_data.jpg](/Image/Titanic/titanic5.PNG) 

Identify the number of passengers in each individual passenger class:

![Number_of_passengers.jpg](/Image/Titanic/titanic6.PNG) 

I created a new column named 'FamilySize' that represents the sum of 'SibSp' and 'Parch'.
Drop the 'Cabin' column from the dataset:

![Idata_characteristics.jpg](/Image/Titanic/titanic7.PNG) 

Next, I created a new DataFrame containing only passengers with an age greater than 30.
Sort the DataFrame by 'Fare' in descending order:

![Idata_characteristics.jpg](/Image/Titanic/titanic8.PNG) 

I also calculated the survival rate for different passenger classes ('Pclass').
Identify and display the passenger with the highest 'Fare':

![Idata_characteristics.jpg](/Image/Titanic/titanic9.PNG) 

<a id="ch7"></a>
## Conclusion

The ananlysis of the Titanic dataset reveals clear differences in survival rates across passenger classes. First class passengers had the highest survival rate (=63%), followed by second-class (=47%), while third-class passengers had the lowest survival rate(=24%). This suggests that socio-economic status played a significant role in survival chances.
Additionally, the passengers with the highest fare (512.33) was Ward, Miss Anna, a 3 years old female travelling inn first class, who survived.This highlights the association between higher ticket cost, travel class and increased livelihood  of survival. 




