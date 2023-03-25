# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
## PROGRAM

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
removing ouliers of bhp.csv file using Zscore of 3
from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)
Using IQR detect height outliers and print them( height_weight.csv)
Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)
Using IQR, detect weight outliers and print them( height_weight.csv)
Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)



## OUTPUT

## IQR METHOD df.head() 

![image](https://user-images.githubusercontent.com/103020162/227719451-1e5d8122-3d9d-4428-9519-cb59c611f710.png)

## df.describe()

![image](https://user-images.githubusercontent.com/103020162/227719469-2df69e1b-a18f-41c6-93eb-c290e52ea39f.png)

## df.info()

![image](https://user-images.githubusercontent.com/103020162/227719537-959086fe-89a7-42bd-b1d4-9f6f2cfbecaa.png)

## df.shape()

![image](https://user-images.githubusercontent.com/103020162/227719549-0413c312-bbca-4b7d-93a7-ec26739eb100.png)

## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227719578-ff0f2717-93fb-47ab-86b1-1ce1352a1fe9.png)

## NEWDATA USING IQR

![image](https://user-images.githubusercontent.com/103020162/227719673-191d7fda-8885-406a-a8e3-9200d2b88812.png)

## OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227719696-2f39501e-5478-4e1e-91f2-2829c05933a9.png)

## newdata.shape

![image](https://user-images.githubusercontent.com/103020162/227719717-675b9d6b-4dc1-4ef0-b3f4-53433a4a6300.png)


## BOXPLOT AFTER REMOVING OUTLIERS USING IQR

![image](https://user-images.githubusercontent.com/103020162/227719757-a7b211ac-bc4c-464c-b0af-7269cb14c09f.png)

Zscore of 3
## NEWDATA USING Zscore

![image](https://user-images.githubusercontent.com/103020162/227719821-d6706c79-6cb0-4cd2-a3a4-aa67842f5a92.png)

## OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227719847-04f83883-bb05-4407-b70f-ed22bd9a136a.png)

## newdata2.shape

![image](https://user-images.githubusercontent.com/103020162/227719882-94514d64-544f-4c59-abcc-dc3e1deb26ea.png)

## BOXPLOT AFTER REMOVING OUTLIERS USING Zscore

![image](https://user-images.githubusercontent.com/103020162/227719968-495c4bd5-08ed-4c1e-b10a-d4a4d13e7cc2.png)

height_weight.csv

## dataset.shape

![image](https://user-images.githubusercontent.com/103020162/227720066-14af8e82-6444-426b-a75e-15906b71ea74.png)

## dataset.describe()

![image](https://user-images.githubusercontent.com/103020162/227720099-14c0d89b-7c63-445a-8ec9-f6c84434e163.png)

## dataset.info()

![image](https://user-images.githubusercontent.com/103020162/227720120-f2f5b9aa-8d75-4b49-ae71-2a3441d1f5dd.png)

## BOXPLOT BEFORE REMOVING OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720144-8580673d-7335-492a-9370-20017683eaf8.png)

## HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720177-b8a60264-cb40-49e4-9c7d-de7d0d81e7eb.png)

## DATASET AFTER REMOVING HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720204-acbd9f6e-bfc6-4ff7-9e0c-e454cf029347.png)

## BOXPLOT AFTER REMOVING HEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720233-9f63bb57-05fb-44ff-a9da-81250fa24af4.png)

## WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720325-b05f7a97-53a3-4d1f-8386-56c7cb6ff4e3.png)

## DATASET AFTER REMOVING WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720376-941f5bd1-2e22-4cdd-aa1d-6ea814e21dfb.png)

## BOXPLOT AFTER REMOVING WEIGHT OUTLIERS

![image](https://user-images.githubusercontent.com/103020162/227720395-3ff7899a-5bf2-4be7-a7fd-29ccd41fcbf7.png)


## RESULT

The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
