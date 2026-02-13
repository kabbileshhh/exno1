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
import numpy as np
import pandas as pd
data=pd.read_csv("/content/SAMPLEIDS.csv")
data
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/590378c3-ada6-474d-a4be-f6569d35ee32" />

```
data.head(4)
```
<img width="1253" height="321" alt="image" src="https://github.com/user-attachments/assets/98a4d9f5-6368-44d6-b1d7-e551389d0b9d" />
```
data.tail(7)
```
<img width="1266" height="401" alt="image" src="https://github.com/user-attachments/assets/4dbfc9ec-ba65-4a84-bf6f-e526e57dc749" />
```
data.isnull()
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/c326b182-d315-4d63-8778-655982a786a5" />

```
data.notnull()
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/ccf29e9a-5e73-4e9b-8d44-e8b4cbb9fd3f" />
```
data.isnull().sum()
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/81d670be-affb-4bb1-ad2e-4d25fc686a1f" />
```
data.dropna(axis=1)
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/8e1110b2-84d0-41d1-a95d-e3b805b2202f" />
```
data.dropna(axis=0)
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/d24c7969-9aee-4821-989e-7de7a1edee17" />
```
data.fillna(0)
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/09bb32f2-fdd4-4f34-9392-4bb8c0df6013" />
```
data.fillna(method="ffill")
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/6ca441f2-a0ce-4e99-899d-e04d5cc6ad57" />
```
data.bfill()
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/34f8a59a-cefe-4025-ac08-c90d7d5fca91" />

```
ir=pd.read_csv("/content/iris.csv")
ir
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/9f42431b-7c86-4aa4-bda7-57059a84cb78" />

```
ir.describe()
```
<img width="878" height="453" alt="image" src="https://github.com/user-attachments/assets/e4f1abab-e9b2-4e28-ba21-97b3a1d98976" />

```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/d7d130fa-3216-49b6-abca-0d0e2a00f830" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
0.5
```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
```

<img width="635" height="315" alt="image" src="https://github.com/user-attachments/assets/db8e10e6-e86e-471a-a277-5d0adace9b3e" />
```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/fd465cf7-4f4e-4e25-a9a5-3a225309cc79" />
```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a0a43de7-355b-4da8-8d8b-3f473b42ded4" />
```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2d530930-7934-4e47-9c86-72346866f9f7" />

            
# Result
Thus the programs are executed successfully.
