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

## Data Cleaning
```
import pandas as pd
df = pd.read_csv("SAMPLEIDS.csv")
df
```

<img width="906" height="722" alt="image" src="https://github.com/user-attachments/assets/6c441782-71d5-4389-847f-f4fda80a4902" />

```
df.head()
```
<img width="873" height="209" alt="image" src="https://github.com/user-attachments/assets/4b3e4c77-e76f-4a82-b424-a35e8bec26cb" />

```
df.tail()
```

<img width="878" height="211" alt="image" src="https://github.com/user-attachments/assets/b28847b2-f135-4116-b474-f656d872cc06" />

```
df.info()
```

<img width="389" height="421" alt="image" src="https://github.com/user-attachments/assets/01fea102-ccc6-445e-98e7-c7d017ca3fb6" />

```
df.describe()
```

<img width="807" height="316" alt="image" src="https://github.com/user-attachments/assets/803205ec-d543-4dfe-8dfe-05158b0683cc" />

```
df.isnull().sum()
```
<img width="156" height="295" alt="image" src="https://github.com/user-attachments/assets/3d89b0f3-55ad-4b0c-826e-6be0f6460af3" />

```
df.isnull().any()
```

<img width="182" height="288" alt="image" src="https://github.com/user-attachments/assets/8a49b85f-a4a4-401c-9960-9616078ab8b1" />

```
df.dropna()
```

<img width="895" height="472" alt="image" src="https://github.com/user-attachments/assets/cc14a91d-476e-41aa-b61b-8ac3de744758" />

```
df.fillna(0)
```

<img width="901" height="720" alt="image" src="https://github.com/user-attachments/assets/ef2cc866-2d89-4426-bbdb-5af08b4d87ec" />

```
df.fillna(method='ffill')
```

<img width="894" height="709" alt="image" src="https://github.com/user-attachments/assets/2e2c0a20-38c2-4040-a76c-78f392332bae" />

```
df.fillna({'GENDER':'MALE', 'NAME':'SRI'})
```

<img width="901" height="714" alt="image" src="https://github.com/user-attachments/assets/812ff9ae-76b6-4205-816a-e4275efecb47" />

## Outlier Detection and Removal

```
ir = pd.read_csv("iris.csv")
ir
```

<img width="533" height="410" alt="image" src="https://github.com/user-attachments/assets/3457b128-4a66-4ded-8ba1-21ab773bf2c2" />

```
ir.describe()
```

<img width="504" height="296" alt="image" src="https://github.com/user-attachments/assets/64f06bb7-31c2-4bd4-a955-749dda635faf" />

```
import seaborn as sns
sns.boxplot(x='sepal_width', data=ir)
```

<img width="683" height="551" alt="image" src="https://github.com/user-attachments/assets/bf423e8e-3d33-44a7-85a1-7f15eaa47c35" />

```
Q1 = ir.sepal_width.quantile(0.25)
Q3 = ir.sepal_width.quantile(0.75)
IQR = Q3 - Q1
print(IQR)
```
<img width="96" height="34" alt="image" src="https://github.com/user-attachments/assets/28c0c5b2-4444-4e7f-8032-ecbf54514d85" />

```
ran = ir[((ir.sepal_width < (Q1 - 1.5*IQR)) | (ir.sepal_width > (Q3 + 1.5*IQR)))]
ran['sepal_width']
```

<img width="368" height="119" alt="image" src="https://github.com/user-attachments/assets/6d644ece-453f-4536-a244-5fe42dd56b03" />

```
sns.boxplot(x='sepal_width', data=ran)
```

<img width="663" height="542" alt="image" src="https://github.com/user-attachments/assets/e271d518-0f68-4543-9798-a465e1144443" />

```
import numpy as np
import scipy.stats as stats
```

```
z = np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="495" height="267" alt="image" src="https://github.com/user-attachments/assets/bd73825a-f8a6-4c63-bcf9-d77060ac18c9" />

```
ir1 = ir[z < 3]
ir1
```
<img width="548" height="394" alt="image" src="https://github.com/user-attachments/assets/734f8799-ff2d-4329-a874-3804eb216e53" />


# Result
Thus the Data Cleaning Process and Outlier Detection and Removal have been Done and executed successfully 
