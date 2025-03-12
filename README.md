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
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2025-03-12 135420](https://github.com/user-attachments/assets/fe03bd44-edf2-4adc-b5f3-b755433dd3b8)
![image](https://github.com/user-attachments/assets/f17f97b3-124f-46cd-a0bd-a428c997e760)
```
df.head()
```
![image](https://github.com/user-attachments/assets/68a9659f-4065-4a0b-943e-9f8978fd88b8)
```
df.tail()
```

![image](https://github.com/user-attachments/assets/412c3362-310c-4ed7-9430-378d7ba01ed3)
```
df.info()
```

![image](https://github.com/user-attachments/assets/d5a1a24a-ac67-4154-a006-b8192d7dcdea)
```
df.describe()
```

![image](https://github.com/user-attachments/assets/a678c74f-6609-4912-94e1-80f00f9886f1)
```
df.isnull().sum()
```

![image](https://github.com/user-attachments/assets/358ec22d-becb-4d50-a332-af0cee7250e2)
```
df.isnull().any()
```

![image](https://github.com/user-attachments/assets/1ddcf4f1-2e91-46bf-b34f-45378ba21f13)
```
df.dropna()
```

![image](https://github.com/user-attachments/assets/7403dc65-2551-4d03-abe3-481b487a7916)
```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/2da7ab37-3f63-44a2-a054-52c3070313de)
```
df.fillna(method='ffill')
```


![image](https://github.com/user-attachments/assets/a3f90f86-7ab7-48db-b40e-951c0412f470)
```
df.fillna(method='bfill')
```

![image](https://github.com/user-attachments/assets/c0cde5e3-d724-4324-9519-2f15f358b94d)
```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/d887f02c-492c-407b-9845-094dca6cbd9f)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

![image](https://github.com/user-attachments/assets/1901161c-b857-4941-bf50-7046cbc1dc68)
```
df_dropped = df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/c85b5c65-0e2d-4712-9c89-313ab663a33e)
```
ir=pd.read_csv("/content/iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/7761d93e-70ff-4360-8c73-266b9cfd694b)
```
ir.describe()
```

![image](https://github.com/user-attachments/assets/30581a2f-1ff6-4a30-a53b-39e261d69bf0)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/35c9a0de-050c-40f9-951d-3b84f7f129fb)
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```

![image](https://github.com/user-attachments/assets/69b79527-610f-496d-9a2f-476d91e5ee5d)
```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/abac68b3-3ef7-460c-8965-883de35b41b0)
```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/98021d80-27b1-40f6-9001-91cfa45f4eb2)
```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/d5ff1f43-e38c-44bd-8022-02368729269a)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/9c7c5d16-da17-481a-bd4f-8f03e6a74340)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3 - q1
iqr
```

![image](https://github.com/user-attachments/assets/9db44a88-1add-47ec-a73f-2b35a8bfb87e)
```
low = q1- 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/4e5ed17e-8ffd-42dc-99e6-7a5e690b271e)
```
high = q3 + 1.5*iqr
high
```


![image](https://github.com/user-attachments/assets/cfb89c2f-18cf-4586-a7db-54dcb2a1ae19)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/50271b16-7bd9-4c4d-b520-adf79630d7d1)
```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/a18b8615-94bf-497b-972a-5aa5c17ed155)
```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/ecd5bd2a-3914-4b70-bd52-29c61561b352)


# Result
          Thus the given data successfully performed data cleaning and saved the cleaned data to a file.




