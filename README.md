# Ex-02_DS_Outlier_Detection_and_Removal
# AIM
To detect and remove the outliers in the given data set and save the final data.

# Explanation
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
## STEP 1
Import the required packages(pandas,numpy,scipy)
## STEP 2
Read the given csv file
## STEP 3
Convert the file into a dataframe and get information of the data.
## STEP 4
Remove the non numerical data columns using drop() method.
## STEP 5
Detect the outliers in the data set using z scores method.
## STEP 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
## STEP 7
Check if the outliers are removed from data set using graphical methods.
## STEP 8
Save the final data set into the file

# CODE:
`````python
## Dataset - "bhp.csv"
import pandas as pd
import numpy as np
df = pd.read_csv('/content/bhp.csv')
df.head(10)
df.boxplot()
df.shape
q1=df.price_per_sqft.quantile(0.25)
q3=df.price_per_sqft.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df[(df.price_per_sqft<lower_limit)|(df.price_per_sqft>upper_limit)]
df[(df.price_per_sqft<=lower_limit)&(df.price_per_sqft>=upper_limit)]
df = df.drop(["location","size","bhk"],axis=1) 
from scipy import stats
z=np.abs(stats.zscore(df))
z
df2=df.copy()
df2=df2[(z<3).all(axis=1)]
df2
df2.boxplot()

# Dataset - height_weight.csv

import pandas as pd
import numpy as np
df1 = pd.read_csv('/content/height_weight.csv')
df1.head(10)
df1.drop("gender",axis=1)
df1.boxplot()
q1=df1.weight.quantile(0.25)
q3=df1.weight.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()
q1=df1.height.quantile(0.25)
q3=df1.height.quantile(0.75)
IQR=q3-q1
lower_limit=q1-1.5*IQR
upper_limit=q3+1.5*IQR
lower_limit,upper_limit
df1_new=df1[(df1.weight<lower_limit)&(df1.weight>upper_limit)]
df1_new.boxplot()

`````
# OUTPUT:
## reading the dataset file and using Boxplot method.
![Screenshot 2023-09-20 154411](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/692c0ea2-7934-4466-994b-38b5f73c84b1)

![Screenshot 2023-09-20 154643](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/a0d585ff-2191-448e-ba99-20d759254811)

![Screenshot 2023-09-20 154743](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/730198f9-10e5-4bf7-aafa-e799325ada02)


## Using IQR method:

![Screenshot 2023-09-20 154855](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/74fe178e-b437-4b5e-8b31-de52060f0533)

![Screenshot 2023-09-20 154947](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/b6fa78ce-0dfe-4913-b356-aa07c014f16b)

![Screenshot 2023-09-20 155044](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/a71a80b4-7a9b-436f-8fc2-a60e6f84ac6e)

## Removing non-numerical columns:

![Screenshot 2023-09-20 155232](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/73d67f5c-d42b-4997-84a0-b3655175db1e)

## Using z-score Method:

![Screenshot 2023-09-20 155356](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/1f6dd3f5-acf7-4f7c-b8dd-137eadd2190d)

![Screenshot 2023-09-20 155425](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/37414cb3-835c-4f8f-b1f1-84618c5037c2)

![Screenshot 2023-09-20 155449](https://github.com/venkatamohankrishnagithub/ODD2023---Datascience---Ex-02/assets/127727792/985190e7-464b-4180-8579-146a59caa159)

# RESULT:

Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
