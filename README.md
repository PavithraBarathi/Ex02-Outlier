# Ex02-Outlier

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them

# code
import numpy as np

import pandas as pd

from scipy import stats

df=pd.read_csv("/content/bhp.csv")
[Expt2-Datascience.pdf](https://github.com/PavithraBarathi/Ex02-Outlier/files/11068359/Expt2-Datascience.pdf)
[Expt2-Datascience.pdf](https://github.com/PavithraBarathi/Ex02-Outlier/files/11068362/Expt2-Datascience.pdf)
[Expt2-Datascience.pdf](https://github.com/PavithraBarathi/Ex02-Outlier/files/11068363/Expt2-Datascience.pdf)

df.head(10)

q1=df['price_per_sqft'].quantile(0.25)

q3=df['price_per_sqft'].quantile(0.75)

IQR=q3-q1

df_new=df[((df['price_per_sqft']>=q1-1.5*IQR)&(df['price_per_sqft']<=q3+1.5*IQR))]

print(df_new)

from scipy import stats

z=np.abs(stats.zscore(df['price_per_sqft']))

df=df[(z<3)]

df.head()

import pandas as pd

df=pd.read_csv("/content/height_weight.csv")

df.head(10)

q1=df['weight'].quantile(0.25)

q3=df['weight'].quantile(0.75)

IQR=q3-q1

df_new=df[((df['weight']<q1-1.5*IQR)|(df['weight']>q3+1.5*IQR))]

print(df_new)

q1=df['height'].quantile(0.25)

q3=df['height'].quantile(0.75)

IQR=q3-q1

df_new=df[((df['height']<q1-1.5*IQR)|(df['height']>q3+1.5*IQR))]

print(df_new)
