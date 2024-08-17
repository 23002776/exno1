# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
# Data cleaning
```import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![11](https://github.com/user-attachments/assets/556cc343-ae3b-4fb5-bc69-e4d4cb3c1f29)
```
df.isnull().sum()
```
![12](https://github.com/user-attachments/assets/50264d6f-73cb-4ed7-aac9-c6a8af123d90)
```
df.isnull().any()
```
![13](https://github.com/user-attachments/assets/4e0da0b3-87b3-4bd9-a933-edd1169ffcd5)
```
df.dropna()
```
![14](https://github.com/user-attachments/assets/dae011e3-2925-458e-80ec-f7e1f5f8b76b)
```
df.fillna(0)
```
![15](https://github.com/user-attachments/assets/94ab9e33-ee8d-4b29-8ebd-05f96b45e980)
```
df.fillna(method = 'ffill')
```
![16](https://github.com/user-attachments/assets/5b435dba-6d44-4295-b7a0-5f0cec736f8f)
```
df.fillna(method='bfill')
```
![17](https://github.com/user-attachments/assets/304f4531-3770-4403-9727-95d426d9cc13)
```
df_dropped = df.dropna()
df_dropped
```
![18](https://github.com/user-attachments/assets/f72931f3-8af1-4d7c-ba21-f51c132650d0)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![19](https://github.com/user-attachments/assets/5722ae4d-c7c8-4cea-bf69-e578c70c1c9f)

# IOR(inter Quartile range)
```
import pandas as pd
ir=pd.read_csv('/content/iris.csv')
ir
```
![Screenshot 2024-08-17 110028](https://github.com/user-attachments/assets/ac799d22-7ad8-4750-ab87-31de0beb06d2)
```
ir.describe()
```
![Screenshot 2024-08-17 110124](https://github.com/user-attachments/assets/40afc9e4-d187-4884-825a-2acae276dd12)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2024-08-17 110254](https://github.com/user-attachments/assets/8a125cb7-e5d1-4cea-a4c7-a4b4fdec2b88)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![Screenshot 2024-08-17 110400](https://github.com/user-attachments/assets/9c914c1b-89b7-4e1b-ab7f-de2abff884d0)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2024-08-17 110457](https://github.com/user-attachments/assets/41e24899-6c8e-4245-a04b-7e717f3e01b4)
```
delib=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![Screenshot 2024-08-17 110922](https://github.com/user-attachments/assets/03b594bb-bce0-4598-9e37-e47ab68fb3c2)
```
sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2024-08-17 111003](https://github.com/user-attachments/assets/2da1c91f-6591-4f42-a122-25896b2efe16)

 # Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![Screenshot 2024-08-17 111127](https://github.com/user-attachments/assets/c6bd0159-18b7-477e-8681-d5083538ed22)
```
df=pd.read_csv("heights.csv")
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2024-08-17 111235](https://github.com/user-attachments/assets/32e2039a-fafa-45e6-bd5b-96e9662366c1)
```
low=q1=1.5*iqr
low
```
![Screenshot 2024-08-17 111314](https://github.com/user-attachments/assets/fc85b3f4-8f43-498e-95cf-c5e4b9378d60)
```
high=q3+1.5*iqr
high
```
![Screenshot 2024-08-17 111314](https://github.com/user-attachments/assets/7ec7adb7-7310-4a76-a6f5-c8af3e7c759c)
```
df1=df[((df['height']>=low)&(df['height']<=high))]
df1
```
![Screenshot 2024-08-17 111420](https://github.com/user-attachments/assets/085944b0-7210-43e2-a56d-05edcbc75041)
```
z=np.abs(stats.zscore(df['height']))
z
```
![Screenshot 2024-08-17 111451](https://github.com/user-attachments/assets/396a400e-2ed8-406b-9294-65a301f359c5)
```
df1=df[z<3]
df1
```
![Screenshot 2024-08-17 111528](https://github.com/user-attachments/assets/a0e1890c-ccaf-4159-b23d-c6030f1e4f39)

# Result
thus we have cleaned the data and remove the outliers by detection using IQR and Z-score method.
