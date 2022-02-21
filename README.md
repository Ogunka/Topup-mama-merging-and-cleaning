# Topup-mama-merging-and-cleaning

# importing the required libraries

import pandas as pd

import numpy as np

# set files path to merge
NGNO = pd.read_csv('C:/Users/USER/Downloads/Nigeria Orders.csv')

NGND = pd.read_csv('C:/Users/USER/Downloads/Nigeria Deliveries.csv')

NGNC = pd.read_csv('C:/Users/USER/Downloads/Nigeria Customers.csv')

KEND = pd.read_csv('C:/Users/USER/Downloads/Kenya Deliveries.csv')

KENO = pd.read_csv('C:/Users/USER/Downloads/Kenya Orders.csv')

KENC = pd.read_csv('C:/Users/USER/Downloads/Kenya Customers.csv')



# merging the six files into one called df
df=pd.concat((NGNO,NGND,NGNC,KEND,KENO,KENC))

df.head(10)


# Checking out the columns in the dataframe
df.columns

# changing the Not A Number values to 1
df = df.astype(object).where(pd.notnull(df),1)

df


# Dropping unnamed columns
data = df.drop([ "Unnamed: 34", "Unnamed: 35"], axis=1)

data.shape

# saviing the dataframe into  csv file
data = pd.DataFrame(df)

data.to_csv('Merged_files1.csv')
