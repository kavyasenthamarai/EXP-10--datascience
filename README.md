# EXP-10--datascience

# AIM :
 To Perform Data Science Process on a complex dataset and save the data to a file.
# ALGORITHM :
##STEP 1:
  Read the given Data
##STEP 2:
  Clean the Data Set using Data Cleaning Process 
##STEP 3:
  Apply Feature Generation/Feature Selection Techniques on the data set 
##STEP 4:  
  Apply EDA /Data visualization techniques to all the features of the data set
  Program:
# Program:
Developed by : k.kavya
Register number : 212222230065
```
import numpy as np 
import pandas as pd 
import seaborn as sns
import matplotlib.pyplot as plt
df_automobile = pd.read_csv("Automobile_data.csv")

#Data Cleaning
df_data = df_automobile.replace('?',np.NAN) 
df_data.isnull().sum()

#Missing Data
df_temp = df_automobile[df_automobile['normalized-losses']!='?']
normalised_mean = df_temp['normalized-losses'].astype(int).mean()
df_automobile['normalized-losses'] = df_automobile['normalized-losses'].replace('?',normalised_mean).astype(int)

df_temp = df_automobile[df_automobile['price']!='?']
normalised_mean = df_temp['price'].astype(int).mean()
df_automobile['price'] = df_automobile['price'].replace('?',normalised_mean).astype(int)

df_temp = df_automobile[df_automobile['horsepower']!='?']
normalised_mean = df_temp['horsepower'].astype(int).mean()
df_automobile['horsepower'] = df_automobile['horsepower'].replace('?',normalised_mean).astype(int)
d
df_temp = df_automobile[df_automobile['peak-rpm']!='?']
normalised_mean = df_temp['peak-rpm'].astype(int).mean()
df_automobile['peak-rpm'] = df_automobile['peak-rpm'].replace('?',normalised_mean).astype(int)

df_temp = df_automobile[df_automobile['bore']!='?']
normalised_mean = df_temp['bore'].astype(float).mean()
df_automobile['bore'] = df_automobile['bore'].replace('?',normalised_mean).astype(float)

df_temp = df_automobile[df_automobile['stroke']!='?']
normalised_mean = df_temp['stroke'].astype(float).mean()
df_automobile['stroke'] = df_automobile['stroke'].replace('?',normalised_mean).astype(float)


df_automobile['num-of-doors'] = df_automobile['num-of-doors'].replace('?','four')
df_automobile.head()

#Summary statistics of variable
df_automobile.describe()

#Univariate Analysis
df_automobile[['engine-size','peak-rpm','curb-weight','horsepower','price']].hist(figsize=(10,8),bins=6,color='black')

plt.tight_layout()
plt.show()

import seaborn as sns
corr = df_automobile.corr()
plt.figure(figsize=(20,9))
a = sns.heatmap(corr, annot=True, fmt='.2f')

#Bivariate Analysis
plt.rcParams['figure.figsize']=(23,10)
ax = sns.boxplot(x="make", y="price", data=df_automobile)

plt.rcParams['figure.figsize']=(19,7)
ax = sns.boxplot(x="body-style", y="price", data=df_automobile)

#violin
sns.catplot(data=df_automobile, x="num-of-cylinders", y="horsepower",kind="violin")
#normalized losess
sns.catplot(data=df_automobile, y="normalized-losses", x="symboling" , hue="body-style" ,kind="point")
```
# Output:
