![titanic.jpg](https://github.com/pangkahhwee/Data-Science/blob/main/Image/Titanic/titanic1.jpg.png?raw=true)

I am doing a forecasting about the number of passengers survival outcomes following a disaster.

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
1. [References](#ch90)


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

**The input data ** 
Core Libraries

sys: System-specific pparameters and functions
pandas (pd): Data manipulation and analysis with DataFrames
numpy (np): Numerical computing with arrays and matrices
scipy (sp): Scientific computing (statistics, optimization, etc.)
matplotlib: Data visualization and plotting
IPython: Enhanced interactive Python (typically used in Jupyter notebooks)

Machine Learning (sklearn)
The code imports a wide range of scikit-learn algorithms:

Classifiers: SVM, decision trees, linear models, k-nearest neighbors, naive Bayes, ensemble methods (like Random Forest), discriminant analysis, and Gaussian processes
XGBoost: A powerful gradient boosting library (imported separately)
Preprocessing: OneHotEncoder (converts categorical variables to binary columns) and LabelEncoder (converts labels to numbers)
Feature selection: Tools to identify the most important features
Model selection: Cross-validation and hyperparameter tuning utilities
Metrics: Performance evaluation (accuracy, precision, recall, etc.)

Visualization

matplotlib/pyplot/pylab: Creating various plots and charts
seaborn (sns): Statistical data visualization with attractive defaults
scatter_matrix: Creates a grid of scatter plots for multiple variables

Utilities

random and time: Random number generation and timing operations
check_output: Executes shell commands from Python



## 3.2 Pre-view of the Data
The *Survived* variable is the outcome or dependent variable. The datatype is 1 if the person survived and 0 if they did not survive. The rest of the variables are independent variables. Most variable names are self explanatory but a couple may be worth mentioning. The *SibSp* represents the number of siblings / spouses aboard the Titanic and *Parch* represents the number of parents / children aboard the Titanic.

![pre-view_dataframe.jpg](/images/titanic/titanic1.jpg)

![dataframe.jpg](/images/titanic/titanic2.jpg)

<a id="ch5"></a>
## 3.3 Data Pre-processing: 
I cleaned the data by identifying and removing abnormal values and outliers, filled in missing data where appropriate, worked on improving the features, and performed data conversion. I used Label encoder to convert objects to categories. 

Divided the data into 75/25 format. 75 is training and 25 is test. 

<a id="ch6"></a>
# Step 4: Explanatory Data Analysis (EDA)

After cleaning and organizing the data, it is important to explore it in order to find any insights. I used EDA to visualize the data I am working with, in order to better understand its properties and statistics. 

![Titanic_Project_28_1.jpg](/images/titanic/titanic3.jpg)

Looking at individual features by survival:

![Titanic_Project_29_1.jpg](/images/titanic/titanic4.jpg)

I then compared class and a 2nd feature:

![Titanic_Project_30_1.jpg](/images/titanic/titanic5.jpg)

Followed by comparing sex and a 2nd feature:

![Titanic_Project_31_1.jpg](/images/titanic/titanic6.jpg)

Family size and sex vs survival and class and sex vs survival:

![Titanic_Project_32_1.jpg](/images/titanic/titanic7.jpg)

Embark data visualization with class and sex vs survival:

![Titanic_Project_33_1.jpg](/images/titanic/titanic8.jpg)

Distributions of age of passengers who survived or did not survive:

![Titanic_Project_34_1.jpg](/images/titanic/titanic9.jpg)

Histogram comparison of sex, class, and age by survival:

![Titanic_Project_35_1.jpg](/images/titanic/titanic10.jpg)

Pairplot to see the entire dataset:

![Titanic_Project_36_1.jpg](/images/titanic/titanic11.jpg)

Heatmap of the entire dataset:

![Titanic_Project_37_0.jpg](/images/titanic/titanic12.jpg)

<a id="ch7"></a>
# Step 5: Data Modelling

I will use a supervised learning classification algorithm for predicting the binary ourcome (survived or not). Here are some resources I found helpful: 

**Some Machine Learning Classification Algorithms:**
* [Ensemble Methods](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble)
* [Generalized Linear Models (GLM)](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.linear_model)
* [Naive Bayes](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.naive_bayes)
* [Nearest Neighbors](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.neighbors)
* [Support Vector Machines (SVM)](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.svm)
* [Decision Trees](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.tree)
* [Discriminant Analysis](http://scikit-learn.org/stable/modules/classes.html#module-sklearn.discriminant_analysis)


### Which Machine Learning Algorithm (MLA) to choose ?
Deciding on which model to use is never a straight answer. In practice, best approach is to work on different algorithms and then compare their performace. Below I summarized the models I worked with, and their performances:

![compare_mla.jpg](/images/titanic/titanic13.jpg)

Then let's see the barplot showing the accuracy score:

![Titanic_Project_39_1.jpg](/images/titanic/titanic14.jpg)

<a id="ch8"></a>
## 5.1 Evaluate Model Performance
After some data pre-processing, analysis, and machine learning algorithms (MLA), I was able to predict passenger survival with ~82% accuracy. Can I do better?


### Somethings to consider: ###
I improved the data by using the learnings from EDA. This is the result of the Decision Tree model after data improvements:


![handmade_model_score.jpg](/images/titanic/titanic15.jpg)

The confusion matrix without normalization:

![Titanic_Project_44_1.jpg](/images/titanic/titanic16.jpg)

Confusion matrix with normalization:

![Titanic_Project_44_2.jpg](/images/titanic/titanic17.jpg)

<a id="ch9"></a>
# 5.11 Model Performance with Cross-Validation (CV) 
In this section, I worked on cross validation (CV). I leveraged the [sklearn cross_validate function](https://scikit-learn.org/stable/modules/cross_validation.html#multimetric-cross-validation). Some advantages of sklearn cross_validate function are:

- It allows specifying multiple metrics for evaluation.
- It returns a dict containing fit-times, score-times in addition to the test score.

 By using CV I was also automatically able to split and score the model multiple times, to get an idea of how well it will perform on unseen data.

<a id="ch10"></a>
# 5.12 Tune Model with Hyper-Parameters
I worked on hyper-parameter optimization to see how various hyper-parameter settings will change the model accuracy. 

Decision trees are simple to understand usually. They can also be visualized. Data prep is quite easy compared to other methods. They can handle both numeric and categorical data. We can validate a model using tests.

However, decision trees do not generalize data well, they do have a tendency to memorize (overfitting). Pruning can be used to overcome this issue. Small variations may impact the decision trees hugely. They can be biased if some classes dominate.


DT before any optimization:

![dt_parameters.jpg](/images/titanic/titanic18.jpg)

<a id="ch11"></a>
## 5.13 Tune Model with Feature Selection
Recursive feature elimination (RFE) with cross validation (CV) is used for feature selection:

![feature_elimination.jpg](/images/titanic/titanic19.jpg)

<a id="ch12"></a>
# Step 6: Correlation of Models

Comparison of algorithm predictions with each other, where 1 = similar and 0 = not similar in a heatmap:

![Titanic_Project_54_0.jpg](/images/titanic/titanic20.jpg)

I have been working on using multiple models instead of choosing one. This gave me a chance to create a supermodel. Removed models that correlates exactly with another model (1).

I worked on voting rules that used hard or majority votes, as well as those that used weighted probabilities. I tuned each estimator before creating a supermodel.

<a id="ch13"></a>
# Conclusion

The model achieved an accuracy of about 78% when predicting the outcomes of unseen data. This was achieved with a simple decision tree. Which decision tree algorithm is best for my data: simple vs an improved model? The simple decision tree algorithm had a better default submission score, and with tuning, I was still able to achieve the same best accuracy score as the one I achieved using a simple decision tree model. The cross-validation accuracy score was much higher than the submission accuracy score.

Next steps will involve further preprocessing and feature engineering to improve the CV score and Kaggle score as well as the overall accuracy.

<a id="ch90"></a>
# References
I would like to thank the following resources and developers:

* [Kaggle: Titanic - Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic/overview) - Kaggle project overview.
* [Introduction to Machine Learning with Python: A Guide for Data Scientists by Andreas Müller and Sarah Guido](https://www.amazon.com/gp/product/1449369413/ref=as_li_tl?ie=UTF8&tag=kaggle-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=1449369413&linkId=740510c3199892cca1632fe738fb8d08) - Machine Learning 101 written by a core developer of sklearn
* [Visualize This: The Flowing Data Guide to Design, Visualization, and Statistics by Nathan Yau](https://www.amazon.com/gp/product/0470944889/ref=as_li_tl?ie=UTF8&tag=kaggle-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=0470944889&linkId=f797da48813ed5cfc762ce5df8ef957f) - Learn the art and science of data visualization
* [Machine Learning for Dummies by John Mueller and Luca Massaron ](https://www.amazon.com/gp/product/1119245516/ref=as_li_tl?ie=UTF8&tag=kaggle-20&camp=1789&creative=9325&linkCode=as2&creativeASIN=1119245516&linkId=5b4ac9a6fd1da198d82f9ca841d1af9f) - Easy to understand for a beginner book, but detailed to actually learn the fundamentals of the topic






