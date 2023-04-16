# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
```
import pandas as pd
df=pd.read_csv("data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()


df1["City"] = ohe.fit_transform(df1[["City"]])

temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])

edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5


Encoading.draw:


import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df

#feature generation
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf

ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2

df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()

df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])

df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4


Titanic.csv:

import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df

#removing unwanted data
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)

#data cleaning
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])

df.isnull().sum()

df

#feature encoding

from category_encoders import BinaryEncoder
be=BinaryEncoder()
df["Sex"]=be.fit_transform(df[["Sex"]])
ndf=be.fit_transform(df["Sex"])
ndf

df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df2

from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df3

from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df4

from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['Passenger','Survived','Pclass','Sex','Age','SibSp','Parch','Fare','Embarked'])
df5
```
# OUPUT
![o1](https://user-images.githubusercontent.com/119559844/232316518-3aa2ebef-a048-43c4-8132-3931217ca84b.png)
![o2 ](https://user-images.githubusercontent.com/119559844/232316524-c63c8442-3908-475c-9cb3-332a14a0b827.png)
![o3 ](https://user-images.githubusercontent.com/119559844/232316527-cdae8514-e916-4168-b6c7-08b2751cffab.png)
![o4 ](https://user-images.githubusercontent.com/119559844/232316534-33577f82-aa02-4e41-a9e3-968f095ba5d4.png)
![o5 ](https://user-images.githubusercontent.com/119559844/232316542-d9587606-b331-451e-b561-021a9c271816.png)
![o6](https://user-images.githubusercontent.com/119559844/232316546-9824e330-4cfb-47a7-a81d-bce1b3673492.png)
![o7 ](https://user-images.githubusercontent.com/119559844/232316549-8f5c1e29-5106-4282-ae78-6d953a563f84.png)
![o8](https://user-images.githubusercontent.com/119559844/232316550-5924ff77-2f69-4ff9-8874-51a558b279d9.png)
![o9](https://user-images.githubusercontent.com/119559844/232316555-d57ab9e8-e58f-4143-a2fb-bf476e3dd9c6.png)
![o10](https://user-images.githubusercontent.com/119559844/232316564-bf0d875f-ad46-44c9-a325-039d49b95676.png)
![o11](https://user-images.githubusercontent.com/119559844/232316571-fc77ed91-ea9a-45d2-b485-add5fd32981d.png)
![o12](https://user-images.githubusercontent.com/119559844/232316576-648bd6ac-6948-4662-954f-345eafc7cfd2.png)
![o13](https://user-images.githubusercontent.com/119559844/232316584-6da77f92-4d41-42e4-a0b4-623a348c001e.png)
![o14](https://user-images.githubusercontent.com/119559844/232316590-7390473f-297f-4a6d-830d-82bb50bcab9c.png)
![o15](https://user-images.githubusercontent.com/119559844/232316594-31e2a68e-95ac-4430-a9ef-f61f803f8656.png)
![o16](https://user-images.githubusercontent.com/119559844/232316598-d9f8f526-b768-4e52-bb35-dc55b57b03e1.png)
![o17](https://user-images.githubusercontent.com/119559844/232316604-bfbced08-7794-4541-ba01-bf0ba2e1cfaf.png)
![o18](https://user-images.githubusercontent.com/119559844/232316610-56f6ba55-1e1d-4792-8a0b-8c48e7900366.png)
![o19](https://user-images.githubusercontent.com/119559844/232316618-a69927f6-f11d-4efb-b92b-0e3388f7b155.png)

RESULT :
Feature Generation process and Feature Scaling process is applied to the given data frames sucessfully
