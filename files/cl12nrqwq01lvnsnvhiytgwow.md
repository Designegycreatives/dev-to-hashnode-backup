## Exploratory Data Analysis With Chi Square Contingency

[Download Note Book Here](https://jovian.ai/designegycreatives/eda-personal-work)
### This Exploratory Data Analysis is my own personal learning practice in this practice i did analysis from datasets i downloaded from kaggle.com 


#### [Plotly For Visualization](https://plotly.com/python)

#### [Seaborn For Visualization](https://seaborn.pydata.org/)

#### Import Necessary Libraries

```
# Libraries for data manipulation
import pandas as pd
import numpy as np

# Libraries for visualization
import seaborn as sns
import matplotlib.pyplot as plt

# Libraries for operatingsystem
import warnings
import os
warnings.filterwarnings('ignore')
```
#### Importing Datasets

```
# Reading the dataset 
df = pd.read_csv(r'C:\Users\user\dl-course-data\abalone.csv')
```

```
df.head()
```
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/kgdc51lx3bi697btnycc.jpg)

### Checking data information

```
# Shape of dataset
df.shape
```
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ib1zh3gdo4jo7slhc7if.jpg)

```
# Checking the null value in the dataset
df.isnull().sum()
```
 
![image 1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979063617/kEG6ghyV7.jpg)


```
# Infromation about dataset
df.info()
``` 

![image 2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979132282/tXkWAwAnu.jpg)


```
# Statistical description of dataset
df.describe().T
``` 

![image 3.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979192254/NVVDCpftO.jpg)


```
# Extracting a unique values of type column
a = df['Type'].unique()
``` 

```
print(a)
``` 

![image 4.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979300612/svnI4kLM2.jpg)


```
# Finding thee counts of Type
b = df['Type'].value_counts()
``` 

```
print(b)
``` 

![image 5.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979378353/XXpgAJjVD.jpg)


```
# Computing Rings by Type

df.groupby(["Type"])["Rings"].count().reset_index(name="count")
``` 

![image 6.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979432117/ugpPpQHAp.jpg)

### Adding ID Column to dataset


```
df['id'] = range(1, len(df)+1)
``` 

```
df.head()
``` 

![image 7.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647979510513/EWJyH93r0.jpg)

### Correlation


```
# finding the correlation of datasets
correlation = df.corr()
``` 

```
# Longest Shell has the highest positive correlation value

fig = px.imshow(correlation,text_auto=True,aspect="auto")
fig.show()
``` 
![image 8.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647983977477/wcP0v-s3y.jpg)


```
# Type M has the highest number of percentage

import plotly.express as px
import pandas as pd 

fig = px.pie(df, values='id', names='Type', title='Abalone Type By Height')
fig.update_traces(hoverinfo='label+percent', textinfo='label+percent', textfont_size=20, pull=[0.1,0.1,0.1],
                  marker=dict(colors=colors, line=dict(color='#000000', width=2)))
fig.show()
``` 
![image 9.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984085848/ViszcIPgV.jpg)


```
#Type M has the highest number of counts

import plotly.express as px

fig = px.bar(df, x='Type', y='id', color='id')
fig.show()
``` 

![image 10.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984146857/wC3Vr2xq7.jpg)


```
# Include nbins= number_of_bins to specify histogram shape

px.histogram(df, x="id", color="Type")
``` 
![image 11.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984255121/I2FDhd2jT.jpg)


```
# Cross tb for Type and Rings for easy understanding

cross_tab = pd.crosstab(df["Type"],df["Rings"],margins=True)
``` 

```
cross_tab
``` 
![image 12.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984332089/8W2HqrlUC.jpg)


```
# The F type is the factor determinant for the whole parameters

sns.factorplot(df["Type"],df["Rings"],data=df)
``` 
![image 13.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984382036/DMTXH-2kE.jpg)


```
import numpy as np
import pandas as pd
from scipy.stats import chi2_contingency


alpha = 0.05

stats,p_value,degrees_of_freedom,expected = chi2_contingency(cross_tab)

if p_value > alpha:
    print(f'Accept Null Hypothesis\n p_value is {p_value}\n Ringss are independent of Types')
else:
    print(f'Reject Null Hypothesis\n p_value is {p_value}\n Rings are not independent of Types')
``` 

![image 14.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647984453417/y0rL9Wg7v.jpg)

#### [References ](https://github.com/Dataebook/Ebook/blob/master/HypothesisTesting.pdf)
