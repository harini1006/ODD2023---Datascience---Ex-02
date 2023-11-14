# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
## ALGORITHM:
### STEP 1:
Read the given Data.

### STEP 2:
Get the information about the data.

### STEP 3:
Detect the Outliers using IQR method and Z score.

### STEP 4:
Remove the outliers:

### STEP 5:
Plot the datas using box plot.

## PROGRAM:
```
DEVELOPED BY: HARINI V
REGISTER NUMBER: 212222230044
```
```
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
```
### Removing ouliers of bhp.csv file using IQR
```
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)
```
### New dataframe.
```
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)
```

### Removing ouliers of bhp.csv file using Zscore of 3
```
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
```

### Using IQR detect height outliers and print them( height_weight.csv)
```
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
```

### Using IQR, detect weight outliers and print them( height_weight.csv)
```
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
```
## OUTPUT:

### df.head():
![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/abac7189-f7b3-489d-b1da-6dec528c63a8)


### df.describe():
![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/56b8cee3-fc1a-496c-8484-c17f6b9c60a2)


### df.info():

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/bab046fe-f4b4-42f1-8ffd-56e8ea2a6747)


### df.shape:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/2295bf8e-d30b-4920-a28e-811f221b8eeb)


### BOXPLOT BEFORE REMOVING OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/6ffe7d48-9566-47e0-8e2e-c79a5df193b9)


### NEWDATA USING IQR:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/895211b7-41ef-4c59-a9f0-ab3dad4e0ac2)


### OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/8d449476-00b7-49bb-99ef-0ee16ea6b342)


### newdata.shape:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/68cdf9cb-b3bc-41dd-a4f4-0ea1859a5d75)


### BOXPLOT AFTER REMOVING OUTLIERS USING IQR:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/d2deebe7-5875-4e1e-b5dd-dd05089d4771)


### Zscore of 3: NEWDATA USING Zscore:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/eeb7aa8a-bf01-4adb-a006-1dc03d62a4ba)


### OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/351e4ac1-2cf7-4337-bf64-d4ead18e11e3)


### newdata2.shape:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/7c4942f0-790a-4c31-8598-14c1f3e0f277)


### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/1072384a-1a71-433a-9e42-7f85b19ce6bb)


### height_weight.csv:
![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/ecb29af0-431b-47eb-851f-b7077cf87a1c)



### dataset.describe():

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/ccfbb8c8-4d32-4675-b262-b0e3a55a0646)


### dataset.info():

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/38b54621-2ece-4173-9890-3db996485361)


### BOXPLOT BEFORE REMOVING OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/f626ac48-6406-4a0a-826e-e8b778df4ef5)


### HEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/5f331c6f-e430-4e04-87b0-fc3ca062a05e)


### DATASET AFTER REMOVING HEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/3d59c731-0ec1-4399-b3c9-a3e483500985)


### BOXPLOT AFTER REMOVING HEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/dba8e315-2415-4073-bdef-890bfc498118)


### WEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/00247720-6ee9-4f6f-983b-24915eb87157)


### DATASET AFTER REMOVING WEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/f333ce9b-b87f-48dd-8ce1-d8f7c3c04f8e)


### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:

![image](https://github.com/harini1006/ODD2023---Datascience---Ex-02/assets/113497405/df46dd8c-9283-4c29-b876-afed4c0ddb7f)


## RESULT:

The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
