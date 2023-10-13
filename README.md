# ODD2023-Datascience-Ex-04
## AIM
To perform Multivariate EDA on the given data set.

## EXPLANATION
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning. The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM

## STEP 1
Import the built libraries required to perform EDA and outlier removal.

## STEP 2
Read the given csv file

## STEP 3
Convert the file into a dataframe and get information of the data.

## STEP 4
Return the objects containing counts of unique values using (value_counts()).

## STEP 5
Plot the counts in the form of Histogram or Bar Graph.

## STEP 6
Use seaborn the bar graph comparison of data can be viewed.

## STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()

## STEP 8
Save the final data set into the file

# CODE :
# Diabetes.csv
```
DEVELOPED BY:BALAMURUGAN B
REFERENCE NUMBER:212222230016

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
import matplotlib.pyplot as plt
df = pd.read_csv("/content/diabetes.csv")
df.info()
df.isnull().sum()
sns.boxplot(data=df)

#DATA CLEANING
z = np.abs(stats.zscore(df['Glucose']))
dfc=df[(z<2)]
z = np.abs(stats.zscore(dfc['BloodPressure']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['SkinThickness']))
dfc=dfc[(z<3)]
z = np.abs(stats.zscore(dfc['BMI']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Insulin']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['DiabetesPedigreeFunction']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Age']))
dfc=dfc[(z<2)]
z = np.abs(stats.zscore(dfc['Outcome']))
dfc=dfc[(z<3)]

sb.boxplot(data=dfc)
plt.figure(figsize = (14,6))
sb.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
sb.scatterplot(x = 'Glucose',y='Insulin',data = df)
sb.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
sb.scatterplot(x = 'Glucose',y='Age',data = df)
sb.heatmap(df.corr(),annot = True)
```
# Superstore.csv
```
import numpy as np
import pandas as pd
import seaborn as sns
from scipy import stats
import matplotlib.pyplot as plt
df=pd.read_csv('/content/SuperStore.csv')
df.head(10)
df.info()
df.isnull()
df.isnull().sum()
sns.boxplot(data=df)
#FILLING ALL NULL VALUES
df['Postal Code'] = df['Postal Code'].fillna(value=df['Postal Code'].mode()[0])
df.isnull().sum()
#REMOVING OUTLIERS
z = np.abs(stats.zscore(df['Sales']))
df = df[z<3]
sns.scatterplot(x = 'Postal Code',y='Sales',data = df)
sns.scatterplot(x = 'Row ID',y='Sales',data = df)
sns.heatmap(df.corr(),annot = True)
```
## OUTPUT :
## Diabetes.csv

BEFORE DATA CLEANING:
![4a1](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/ff5fdc6e-d1bd-42e9-9f58-112640757d74)

AFTER DATA CLEANING:
![4a2](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/835b28af-56d7-46e6-9876-78b7208361e3)
![4a3](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/f16267a6-82c3-4cf9-a092-b675fcfddf84)
![4a4](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/b0b847e3-6cc8-4821-9b21-cdd44747afe4)
![4a5](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/9f765860-7259-4624-b91d-5534b03ff415)

HEATMAP:
![4a6](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/648ffbb3-e133-4340-9e6a-db722622df46)

## Superstore.csv

BEFORE DATA CLEANING:
![4b1](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/748ec1b4-0a3b-4660-b2c8-353911bf12fb)

AFTER DATA CLEANING:
![4b2](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/d79009bb-3fec-4652-9e71-bef52b6ac994)
![4b3](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/b6cf9190-960e-434b-b7e1-0c978007a7bc)
![4b4](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/5abcf4bc-0af1-462f-9a28-1d4c8d62a124)

HEATMAP:
![4b5](https://github.com/BALA291/ODD2023-Datascience-Ex-04/assets/120717501/07ab98aa-defb-4e04-99b7-d9eb91414fc8)

## RESULT
Thus we have read the given data and performed the multivariate analysis with different types of plots.
