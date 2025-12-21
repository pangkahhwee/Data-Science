![titanic.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Titanic/titanic1.jpg.png?raw=true)

I am doing a forecasting about the number of passengers survival outcomes following a famous disaster in history.

# Table of Contents
1. [Chapter 1 - Project Overview](#ch1)
1. [Chapter 2 - Data Science Steps](#ch2)
1. [Chapter 3 - Step 1: Problem Definition](#ch3)
1. [Chapter 4 - Step 2: Data Gathering](#ch4)
1. [Chapter 5 - Step 3: Data Preparation](#ch5)
1. [Chapter 6 - Step 4: Explanatory Data Analysis (EDA)](#ch6)
1. [Chapter 7 - Step 5: Data Modelling](#ch7)
1. [Chapter 8 - Evaluate Model Performance](#ch8)
1. [Chapter 9 - Model Performance with Cross-Validation (CV)](#ch9)
1. [Chapter 10 - Tune Model with Hyper-Parameters](#ch10)
1. [Chapter 11 - Tune Model with Feature Selection](#ch11)
1. [Chapter 12 - Step 6: Validate Model](#ch12)
1. [Chapter 13 - Conclusion](#ch13)


<a id="ch1"></a>
# Project Overview
In this project, I selected a widely used classification task with binary outcomes: either 0 or 1 where an event either occurs or does not. Examples include whether it will rain tomorrow or whether a production component is functioning or not.

I worked with a project based on my interest after watching a movie, Titanic: Exploratory Data Analysis with Python Pandas. I concentrated on predicting passenger survival outcomes by following a structured workflow: defining the problem, collecting, cleaning and preparing the data, performing exploratory data analysis, building a model, validating its performance and further optimizing it.

Let's take a look at the steps:

<a id="ch2"></a>
# Data Science Steps
1. **Problem Definition:** What factors influenced survival in a disaster? By analyzing passenger data, we are able to identify specific groups that had a higher likelihood of survival.
2. **Data Gathering:** I got the dataset from a website.
3. **Data Preparation:** I cleaned the dataset by remove the duplicates and blanks or outliers.
4. **EDA (Exploratory Data Analysis):** If poor quality data is fed into a system, the results will be equally poor. That is why it is important to apply descriptive and visual statistics to uncover patterns, relationships and comparisons within the dataset. At this stage, I will examine the data to ensure whether it is clear, consistent and meaningful.
5. **Data Modeling:** Choosing the right model is important. If an inappropriate model is selected for a given use case, the effectiveness of all subsequent steps is compromised. 
6. **Validate Model:** I will evaluate its performance and assessed after training as whether it showed signs of overfitting or underfitting.
7. **Optimize Model:** I improved the model by applying techniques such as hyperparameter optimization to enhance its performance.

<a id="ch3"></a>
# Step 1: Problem Definition
The objective of this project is to predict the number of passengers on the Titanic survived when the sinking disaster striked.

**Project Summary**
The Titanic disaster is one of the most well-known maritime tragedies in history. On April 15, 1912, the RMS Titanic sank after striking an iceberg. Although it was widely believed to be unsinkable, the ship was lost due to the collision. With insufficient lifeboats on board, 1,502 out of the 2,224 passengers and crew members lost their lives.

Certain groups of passengers appeared to have a higher likelihood of survival than others, though luck also played a role. In this challenge, the objective is to develop a predictive model that determines an individual’s probability of survival based on passenger data such as name, age, gender, social class and other relevant attributes.

<a id="ch4"></a>
# Step 2: Data Gathering

The dataset can be found here: [Titanic: Exploratory Data Analysis with Python Pandas](https://github.com/pangkahhwee/Data-Science/blob/09fb04dea0764ced3fc80ebe0a9b68e480891a98/Image/Dataset/titanic.csv)

<a id="ch5"></a>
# Step 3: Data Preperation
The data was downloaded into my Github, so I only focused on cleaning it up and use it for my Data Science.

[Downloading the dataset](/Image/Titanic/titanic2.png) 

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

# Core Libraries 

pandas (pd): Data manipulation and analysis with DataFrames

numpy (np): Numerical computing with arrays and matrices

scipy (sp): Scientific computing (statistics, optimization, etc.)

matplotlib: Data visualization and plotting

IPython: Enhanced interactive Python (typically used in Jupyter notebooks)

sys: System-specific pparameters and functions

# Machine Learning (sklearn) 

The code imports a wide range of scikit-learn algorithms:

Classifiers: SVM, decision trees, linear models, k-nearest neighbors, naive Bayes, ensemble methods (like Random Forest), discriminant analysis, and Gaussian processes

XGBoost: A powerful gradient boosting library (imported separately)

Preprocessing: OneHotEncoder (converts categorical variables to binary columns) and LabelEncoder (converts labels to numbers)

Feature selection: Tools to identify the most important features

Model selection: Cross-validation and hyperparameter tuning utilities

Metrics: Performance evaluation (accuracy, precision, recall, etc.)

# Visualization

matplotlib/pyplot/pylab: Creating various plots and charts

seaborn (sns): Statistical data visualization with attractive defaults

scatter_matrix: Creates a grid of scatter plots for multiple variables

This setup is typical for Kaggle competitions or exploratory data analysis projects where you want many ML algorithms available to experiment with.

# Utilities

random and time: Random number generation and timing operations
check_output: Executes shell commands from Python

This setup is typical for Kaggle competitions or exploratory data analysis projects where many ML algorithms available to experiment with.

## 3.2 Pre-view of the Data
The survived variable serves as the outcome (or dependent) variable, coded as 1 if the passenger survived and 0 if they did not. All other variables are independent (predictor) variables. While most variable names are self-explanatory, two merit clarification: SibSp denotes the number of siblings or spouses aboard the Titanic and Parch indicates the number of parents or children aboard the vessel.

![pre-view_dataframe.jpg](/images/titanic/titanic1.jpg)

![dataframe.jpg](/images/titanic/titanic2.jpg)

<a id="ch5"></a>
## 3.3 Data Pre-processing: 
I performed data cleaning by removing anomalies and outliers, imputing missing values where appropriate, enhancing features and carrying out necessary data transformations. Specifically, I used a Label Encoder to convert object-type variables into categorical representations.

The dataset was then split into a 75/25 ratio, with 75% allocated for training and 25% reserved for testing.

<a id="ch6"></a>
# Step 4: Explanatory Data Analysis (EDA)

Following data cleaning and organization, I conducted exploratory data analysis (EDA) to examine the dataset, using visualizations to gain a deeper understanding of its characteristics, underlying patterns and statistical properties.

![Titanic_Project_28_1.jpg](/images/titanic/titanic3.jpg)

Examining each feature in relation to survival:

![Titanic_Project_29_1.jpg](/images/titanic/titanic4.jpg)

I then compared passenger class with a second feature:

![Titanic_Project_30_1.jpg](/images/titanic/titanic5.jpg)

Next, I compared sex with a second feature:

![Titanic_Project_31_1.jpg](/images/titanic/titanic6.jpg)

I examined the relationships between family size and sex with respect to survival as well as between passenger class and sex with respect to survival.:

![Titanic_Project_32_1.jpg](/images/titanic/titanic7.jpg)

I also visualized embarkation data in conjunction with passenger class and sex while analyzing their relationships with survival.:

![Titanic_Project_33_1.jpg](/images/titanic/titanic8.jpg)

The age distributions of passengers who survived and those who did not survive:

![Titanic_Project_34_1.jpg](/images/titanic/titanic9.jpg)

A histogram-based comparison of sex, passenger class and age, stratified by survival status:

![Titanic_Project_35_1.jpg](/images/titanic/titanic10.jpg)

A pairplot was used to visualize the entire dataset and examine relationships among all variables:

![Titanic_Project_36_1.jpg](/images/titanic/titanic11.jpg)

A heatmap was generated to visualize correlations across all variables in the dataset:

![Titanic_Project_37_0.jpg](/images/titanic/titanic12.jpg)

<a id="ch7"></a>
# Step 5: Data Modelling

I will employ a supervised learning classification algorithm to predict the binary outcome—whether a passenger survived or not.

### Which Machine Learning Algorithm (MLA) to choose ?
Selecting the most suitable model is rarely straightforward. In practice, the optimal approach involves experimenting with multiple algorithms and comparing their performance. Below, I have summarized the models I evaluated along with their respective results:

![compare_mla.jpg](/images/titanic/titanic13.jpg)

Let us examine the bar plot displaying the accuracy scores:

![Titanic_Project_39_1.jpg](/images/titanic/titanic14.jpg)

<a id="ch8"></a>
## 5.1 Evaluate Model Performance
Following data preprocessing, exploratory analysis and the application of various machine learning algorithms (MLAs), I achieved a passenger survival prediction accuracy of approximately 82%. Can this performance be further improved?


### Somethings to consider: ###
I refined the dataset by incorporating insights gained from exploratory data analysis (EDA). The following result reflects the performance of the Decision Tree model after these data enhancements:


![handmade_model_score.jpg](/images/titanic/titanic15.jpg)

The confusion matrix without normalization:

![Titanic_Project_44_1.jpg](/images/titanic/titanic16.jpg)

Confusion matrix with normalization:

![Titanic_Project_44_2.jpg](/images/titanic/titanic17.jpg)

<a id="ch9"></a>
# 5.11 Model performance evaluated using with Cross-Validation (CV) 
In this section, I implemented cross-validation (CV) using the [sklearn cross_validate function](https://scikit-learn.org/stable/modules/cross_validation.html#multimetric-cross-validation) function offers several advantages, including:

1) Support for evaluating multiple scoring metrics simultaneously.
2) Provision of a dictionary that includes not only the test scores but also the fit times and score times.
   
By employing cross-validation (CV), I was able to automatically split the data and evaluate the model multiple times, providing a robust estimate of its performance on unseen data.

<a id="ch10"></a>
# 5.12 Optimize the model by using Hyperparameters
I conducted hyperparameter optimization to assess how different hyperparameter configurations affect the model’s accuracy.

Decision trees are generally intuitive and easy to interpret which often visualizable and makes them accessible. They require relatively minimal data preprocessing compared to other algorithms and can naturally handle both numerical and categorical features. Additionally, their performance can be validated using statistical tests.

However, decision trees tend to generalize poorly to unseen data as they are more prone to overfitting by essentially memorizing the training set. This issue can be mitigated through techniques like pruning. Moreover, they can be highly sensitive to minor variations in the data and may exhibit bias toward dominant classes when the class distribution is imbalanced.

DT prior to any optimization:

![dt_parameters.jpg](/images/titanic/titanic18.jpg)

<a id="ch11"></a>
## 5.13 Optimize the model through feature selection
Recursive feature elimination (RFE) with cross validation (CV) is used for feature selection:

![feature_elimination.jpg](/images/titanic/titanic19.jpg)

<a id="ch12"></a>
# Step 6: Models correlations

A heatmap comparing algorithm predictions against one another where a value of 1 indicates high similarity and 0 indicates dissimilarity:

![Titanic_Project_54_0.jpg](/images/titanic/titanic20.jpg)

I have been experimenting with ensemble methods by combining multiple models rather than selecting a single one which enabled me to construct a "supermodel." As part of this process, I removed any model that was perfectly correlated (correlation = 1) with another to avoid redundancy.

I explored various voting strategies which both hard (majority-based) voting and soft voting based on weighted probabilities. Prior to assembling the supermodel, I carefully tuned each individual estimator to optimize its performance
<a id="ch13"></a>
# Conclusion

The model attained an accuracy of approximately 78% on unseen data using a basic decision tree. This raises the question: which approach is better suited for my dataset? A simple decision tree or an enhanced version? Interestingly, the untuned (default) simple decision tree yielded a higher initial submission score and even after hyperparameter tuning, the best accuracy achieved matched that of the simple model.

Notably, the cross-validation accuracy was significantly higher than the submission score.

Moving forward, I plan to focus on additional preprocessing and more sophisticated feature engineering to bridge this gap and improve both the cross-validation as well as overall model accuracy.

<a id="ch90"></a>



