## Hypothesis Testing With T-TEST

### T-TEST: Is used to compare the mean of two given samples
#### Hypothesis testing to check if alcohol contents affects wine quality using T-Test

**Import the libraries**

```
%matplotlib inline
import warnings
import numpy as np
import pandas as pd
import seaborn as sns
from scipy import stats
import researchpy as rc
import statsmodels.api as sm
from scipy.stats import levene
import matplotlib.pyplot as plt
from sklearn.preprocessing import scale
``` 
**Load and read data**


[Download data here..](https://www.kaggle.com/yasserh/wine-quality-dataset)

```
df = pd.read_csv("WineQT.csv")
``` 
**Check data head**

```
df.head()
``` 
![image 1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647304396721/FrqkJuTHm.jpg)

**Check data tail**

```
df.tail()
``` 
![image 2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647304521575/yi3gXcOiY.jpg)

**Check data shape**

```
df.shape
``` 
![image 3.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647304712413/noLJkR09h.jpg)

**Check data information**

```
df.isnull().sum()
``` 
![image 4.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647304818273/O81oJYse2.jpg)


```
df.info()
``` 
![image 5.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647304911837/amyeshn8s.jpg)

**Check the unique values in each column**

```
df.apply(lambda x : x.nunique())
``` 
![image 6.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305000481/ktGyLba96.jpg)

**Preparing data for T Test**

**Lets check the mean of wine quality with alcohol**

```
df.groupby('quality')['alcohol'].describe().T

# The mean shows that the higher the wine content the better the wine quality
``` 
![image 7.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305112580/z4nJczcLi.jpg)


```
# picking random samples from wine quality 

sample_01 = df[df['quality']== 5]
sample_02 = df[df['quality']== 6]
``` 

```
print(sample_01.shape,sample_02.shape)
``` 
![image 8.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305197354/J03zrhv1j.jpg)

**Assumptions for T-Test
The variances of the 2 samples are equal (we will use levene's test to check the assumption
the distribution of the residuals between the two groups should follow the normal distribution**


```
sample_01 = sample_01.sample(462)
print(sample_01.shape,sample_02.shape)
``` 
![image 9.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305280263/81cSfxCc9.jpg)

**Levene's Test**

```
alpha = 0.05
stats,Pvalue = stats.levene(sample_01['alcohol'], sample_01['alcohol'])
print(f' Test statistics : {stats} \n Alpha : {alpha} \n P-value : {Pvalue}')

if Pvalue > alpha:
    print('Variances are same accept null hypothesis')
else:
    print('Variances are not same reject null hypothesis')
``` 
![image 10.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305342651/UC-xp1SLf.jpg)

**Checking the normality of the residuals**

```
# plotting and scaling of the difference between sample 1 and sample 2
# diagram looks like normal distribution


diff = scale((np.array(sample_01['alcohol']) - np.array(sample_02['alcohol'])))
              
plt.figure(figsize=(12,6))
plt.hist(diff)
plt.show()
``` 
![image 11.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305452472/VEsvxFanr.jpg)


```
# My Observation
# Wines with alcohol content  between 9 - 12%  are the most quality wines

plt.figure(figsize=(12,6))
sns.kdeplot(sample_01['alcohol'], shade=True)
sns.kdeplot(sample_02['alcohol'], shade=True)
plt.legend(['sample_01','sample_02'], fontsize=14)
plt.vlines(x=sample_01['alcohol'].mean(), ymin=0,ymax=0.25,color='blue',linestyle='--')
plt.vlines(x=sample_02['alcohol'].mean(), ymin=0,ymax=0.25,color='blue',linestyle='--')
plt.show()
``` 
![image 12.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305506568/UgsTfGiIK.jpg)

**Q-Q PLOT Generates the probability of sample data against the quantiles of theoretical distributions**

```
# The residual is normally distributed because it closely follows the red lines

plt.figure(figsize=(12,6))
stats.probplot(diff,plot=plt,dist='norm')
plt.show()
``` 
![image 13.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305579173/RJBeqp5CS.jpg)

**Normality test

H0: Normally distributed

H1: Not Normally Distributed**


```
# shapiro wilk's test shows residual is not normally distributed
alpha = 0.05
statistic, p_value = stats.shapiro(diff)
if p_value > alpha:
    print(f'Accept Null Hypothesis p-value: {p_value}')
else:
    print(f'Reject Null Hypothesis p-value: {p_value}')
``` 
![image 14.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305647695/2gGVJFzJw.jpg)

**Independent sample t-test

H0: There is no difference in mean (wine quality doesn't depend on alcohol %)

H1: There is a difference in mean(wine quality depends on alcohol %)**

```
alpha = 0.05
statistic, p_value = stats.ttest_ind(sample_01['alcohol'], sample_02['alcohol'])
if p_value > alpha:
    print(f'Fail To Reject Null Hypothesis p-value: {p_value}')
else:
    print(f'Reject Null Hypothesis')
``` 
![image 15.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1647305716912/_5Mej9K6u.jpg)

**Conclusion**

**Alcohol content % has an effect on wine quality**

[**`References`**](https://github.com/Dataebook/Ebook/blob/master/HypothesisTesting.pdf)







