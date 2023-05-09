# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
# ALGORITHM

### STEP 1
Read the given Data.

### STEP 2
Get the information about the data.

### STEP 3
Detect the Outliers using IQR method and Z score.

### STEP 4
Remove the outliers.

### STEP 5
Plot the datas using Box Plot.

# PROGRAM

import pandas as ps
import numpy as np
import seaborn as sns
df=ps.read_csv("bhp.csv")
df
df.head()
df.describe()
df.info()
df.isnull().sum()
df.shape
sns.boxplot(x="price_per_sqft",data=df)
q1=df['price_per_sqft'].quantile(0.35)
q3=df['price_per_sqft'].quantile(0.65)
print("First Quantile =",q1,"Second quantile =",q3)
IQR=q3-q1 #INTERQUARTILE RANGE
u1=q3+1.5*IQR
l1=q1-1.5*IQR
df1=df[((df['price_per_sqft']<=l1)&(df['price_per_sqft']>u1))]
df1
df1.shape
sns.boxplot(x='price_per_sqft',data=df1)
from scipy import stats
z=np.abs(stats.zscore(df['price_per_sqft']))
df2=df[(z<3)]
df2
print(df2.shape)
sns.boxplot(x='price_per_sqft',data=df2)
df3=ps.read_csv('height_weight.csv')
df3
df3.head()
df3.info()
df3.describe()
df3.isnull().sum()
df3.shape
sns.boxplot(x='weight',data=df3)
q1=df3['weight'].quantile(0.25)
q3=df3['weight'].quantile(0.75)
print('First Quantile =',q1,'Second Quantile =',q3)
IQR=q3-q1
u1=q3+1.5*IQR
l1=q1-1.5*IQR
df4 =df3[((df3['height']>=l1)&(df3['height']<=u1))]
df4
df4.shape
sns.boxplot(x='height',data=df4)


# OUTPUT

### DATASET FOR BHP_CSV
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/1.png)
### DATASET HEAD(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/2.png)
### DATASET DESCRIBE(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/3.png)
### DATASET INFO(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/4.png)
### DATASET NULL VALUES(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/5.png)
### DATASET SHAPE WITH OUTLIERS(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/6.png)
### DATASET BOXPLOT WITH OUTLIERS(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/7.png)
### DATASET WITHOUT OUTLIERS(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/8.png)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/9.png)
### DATASET SHAPE WITHOUT OUTLIERS(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/10.png)
### DATASET BOXPLOT WITHOUT OUTLIERS(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/11.png)
### DATASET AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/12.png)
### DATASET SHAPE AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/13.png)
### DATASET BOXPLOT AFTER REMOVAL OF OUTLIERS USING Z-SCORE(BHP)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/14.png)
### DATASET FOR WEIGHT_HEIGHT_CSV
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/15.png)
### DATASET HEAD(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/16.png)
### DATASET INFO(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/17.png)
### DATASET DESCRIBE(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/18.png)
### DATASET NULL VALUES(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/19.png)
### DATASET BOXPLOT WITH OUTLIERS(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/20.png)
### DATASET AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/22.png)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/21.png)
### DATASET SHAPE(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/23.png)
### DATASET BOXPLOT AFTER REMOVING OUTLIERS USING IQR METHOD(WEIGHT_HEIGHT)
![](https://raw.githubusercontent.com/21001052/Ex02-Outlier/main/24.png)

# RESULT
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
