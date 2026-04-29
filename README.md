# Exno:1 Data Cleaning Process


## Name: KIRUTIKA K R
## Reg No: 212224230128



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
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="935" height="717" alt="image" src="https://github.com/user-attachments/assets/f72528d8-ce14-46e4-811c-c594be5bdb40" />

```
df.head()
```
<img width="891" height="212" alt="image" src="https://github.com/user-attachments/assets/dcca856b-b383-4aa3-bcb3-a0e2c2c6873a" />

```
df.tail()
```
<img width="947" height="207" alt="image" src="https://github.com/user-attachments/assets/7708db3c-22c0-410a-882a-b320fbd8f0cb" />

```
df.isnull()
```
<img width="839" height="727" alt="image" src="https://github.com/user-attachments/assets/d2ed50a8-1aa8-4136-a164-dc4695319a59" />

```
df.isnull().sum()
```
<img width="216" height="286" alt="image" src="https://github.com/user-attachments/assets/721960eb-f28e-4f4f-afce-45b8e5d25b65" />

```
df.isnull().any()
```
<img width="225" height="294" alt="image" src="https://github.com/user-attachments/assets/9e4ff34a-269d-4d0a-a06a-d16d92e881d5" />

```
df.dropna(axis=0)
```
<img width="936" height="461" alt="image" src="https://github.com/user-attachments/assets/ab864f56-18ff-48c3-bd0e-f6a5b047ce6f" />

```
df.dropna(axis=1)
```
<img width="315" height="716" alt="image" src="https://github.com/user-attachments/assets/e8421928-ea18-4770-b752-eb388238b75a" />

```
df.fillna("empty")
```
<img width="958" height="719" alt="image" src="https://github.com/user-attachments/assets/f9a65758-849a-4547-8227-a1313b615fee" />

```
df.fillna(method='ffill')
```
<img width="927" height="720" alt="image" src="https://github.com/user-attachments/assets/d8fd96bc-086f-410c-8ecb-f3fd5127e060" />

```
df.fillna(method='bfill')
```
<img width="939" height="717" alt="image" src="https://github.com/user-attachments/assets/001e3422-23f5-4b81-ad7d-ffba76309831" />

```
df.fillna({'NAME':'RIYA','GENDER':'FEMALE','ADDRESS':'CHENNAI','M1':90,'M2':90,'M3':89,'M4':87})
```
<img width="925" height="712" alt="image" src="https://github.com/user-attachments/assets/05554633-afb2-4140-996c-124e8764a635" />

```
import numpy as np
from scipy import stats
ir=pd.read_csv("iris.csv")
ir
```
<img width="573" height="431" alt="image" src="https://github.com/user-attachments/assets/d1e2a19b-bea7-4069-8d23-2ab067220510" />

```
ir.describe()
```
<img width="555" height="305" alt="image" src="https://github.com/user-attachments/assets/bc5cbef1-87b6-41e8-9ca7-1d718aea50a1" />

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
<img width="750" height="579" alt="image" src="https://github.com/user-attachments/assets/78136a64-3bd9-48a5-b122-cf4c92134a86" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="592" height="39" alt="image" src="https://github.com/user-attachments/assets/a95158cd-2a04-4a91-80c5-27390adc4588" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="385" height="116" alt="image" src="https://github.com/user-attachments/assets/3ac2b09f-9645-4416-bdd4-2effd337664e" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
delid
```
<img width="611" height="428" alt="image" src="https://github.com/user-attachments/assets/fcd7568a-fc57-4afa-bf55-6c586c3f7702" />

```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="728" height="576" alt="image" src="https://github.com/user-attachments/assets/b35d3d9a-b97e-476b-96e7-0cf622094749" />

```
z=np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="472" height="267" alt="image" src="https://github.com/user-attachments/assets/72541e4e-4090-41fc-a8e6-f9b7afa6b723" />

```
ir1=ir[z<3]
ir1
```
<img width="547" height="432" alt="image" src="https://github.com/user-attachments/assets/9771cf3b-6fb2-48e2-b093-3c2ae9ca2ed4" />

           
# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
