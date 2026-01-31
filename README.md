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
<img width="1027" height="803" alt="image" src="https://github.com/user-attachments/assets/011b8884-e903-4c01-a213-75fff8100bd5" />

```
df.head()
```
<img width="997" height="252" alt="image" src="https://github.com/user-attachments/assets/d9340b92-19b3-4a47-aff6-6a769bbf7d75" />

```
df.tail()
```
<img width="1025" height="258" alt="image" src="https://github.com/user-attachments/assets/8e54e584-b215-4cf4-b6f7-fc4a14bfd0d7" />

```
df.info()
```
<img width="429" height="423" alt="image" src="https://github.com/user-attachments/assets/b486e9c5-1ec4-4f31-99dd-0aeda98453a6" />

```
df.describe()
```
<img width="929" height="357" alt="image" src="https://github.com/user-attachments/assets/8c4ce589-f3e5-4063-b4ca-d9a1f5c9db8f" />

```
df.isnull().sum()
```
<img width="161" height="565" alt="image" src="https://github.com/user-attachments/assets/0e26e469-e0c0-47fb-9471-ef075fedf520" />

```
df.isnull().any()
```
<img width="236" height="574" alt="image" src="https://github.com/user-attachments/assets/6a1cbee3-e826-4814-ab9e-c51688f27cda" />

```
df.dropna()
```
<img width="1034" height="563" alt="image" src="https://github.com/user-attachments/assets/22de28e8-be18-41e2-9da7-e3e01de260ac" />

```
df.fillna(0)
```
<img width="1048" height="753" alt="image" src="https://github.com/user-attachments/assets/3fc97349-927f-4da6-b939-910bc326eb38" />

```
df.fillna(method='ffill')
```
<img width="1666" height="685" alt="image" src="https://github.com/user-attachments/assets/891a87a4-40ea-4210-bc97-8d7cc9c2fe6b" />

<img width="1098" height="244" alt="image" src="https://github.com/user-attachments/assets/6f6f6245-291b-40c8-8070-d29d9a2d5e63" />

```
df.fillna({'GENDER':'MALE','NAME':'SRI'})
```
<img width="1040" height="757" alt="image" src="https://github.com/user-attachments/assets/b0cced8e-683e-4cd2-8647-dee628793e1b" />

```
ir=pd.read_csv("/content/iris.csv")
ir
```
<img width="665" height="530" alt="image" src="https://github.com/user-attachments/assets/e2e7c63f-3bc1-43b5-ab83-4e497b83ba38" />

```
ir.describe()
```
<img width="597" height="366" alt="image" src="https://github.com/user-attachments/assets/b997a3ba-0414-47ee-88c4-6cfd64729582" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="700" height="571" alt="image" src="https://github.com/user-attachments/assets/480e5704-3ca6-44b1-af90-5973c73bfe5a" />

```
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
```
<img width="140" height="40" alt="image" src="https://github.com/user-attachments/assets/7398a2e5-7660-4bed-9aad-eb19076a8994" />

```
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```
<img width="221" height="264" alt="image" src="https://github.com/user-attachments/assets/9b736e59-9d4c-44e5-89a3-c5158b4f3635" />

```
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```
<img width="298" height="571" alt="image" src="https://github.com/user-attachments/assets/e091714c-318b-46b3-83b2-0e26831e90df" />

```
sns.boxplot(x='sepal_width',data=ran)
```
<img width="688" height="574" alt="image" src="https://github.com/user-attachments/assets/387436df-0483-48ad-a889-ec42ebe809ad" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['petal_length']))
z
```
<img width="714" height="672" alt="image" src="https://github.com/user-attachments/assets/90612e77-dc6e-4a6f-89df-e96bd719c2e1" />

```
ir1=ir[z<3]
ir1
```
<img width="674" height="528" alt="image" src="https://github.com/user-attachments/assets/4adda263-9a4b-4fd6-bb10-d0721b553c8d" />


# Result
Thus the programs are executed successfully.
