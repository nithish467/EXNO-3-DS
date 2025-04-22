## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
Name:NITHISHKUMAR S
Reg no: 212223240109
```
import pandas as pd
from scipy import stats
import numpy as np
```
```
df=pd.read_csv("/content/Encoding Data (2).csv")
```
```
df
```
![image](https://github.com/user-attachments/assets/5bb600fb-cad5-49f5-81e5-68dee66fca7a)
```
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
```
```
pm=['Hot','Warm','Cold']
```
```
e1=OrdinalEncoder(categories=[pm])
```
```
e1.fit_transform(df[["ord_2"]])
```
![image](https://github.com/user-attachments/assets/0e210836-045e-40c4-85a4-f6dacaf95555)
```
df
```
![image](https://github.com/user-attachments/assets/758ac55e-2340-499b-a50e-811f233e9674)
```
le=LabelEncoder()
```
```
dfc=df.copy()
```
```
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
```
```
dfc
```
![image](https://github.com/user-attachments/assets/52c96202-cce1-417d-8748-41edac996f68)
```
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
```
```
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
```
```
df2=pd.concat([df2,enc],axis=1)
```
```
df2
```
![image](https://github.com/user-attachments/assets/3161af97-30be-4943-a28d-9deeeb25051f)
```

pd.get_dummies(df2,columns=["nom_0"])
```
![image](https://github.com/user-attachments/assets/872e59b2-b202-4e92-aee2-65b9d7f8d286)
```
!pip install category_encoders
from category_encoders import BinaryEncoder
```
![image](https://github.com/user-attachments/assets/40f8294a-935e-4532-b01f-06065b6c7ae1)
```
from category_encoders import BinaryEncoder
```
```
df=pd.read_csv("/content/data (2).csv")
```
```
df
```
![image](https://github.com/user-attachments/assets/8c40dd33-d458-4c15-80fa-310095d82cf5)

```
be=BinaryEncoder()
```
```
nd=be.fit_transform(['Ord_2'])
```
```
dfb=pd.concat([df,nd],axis=1)
```
```
dfb1=df.copy()
```
```
dfb
```
![image](https://github.com/user-attachments/assets/4b5eef95-ca52-4eb4-92f9-04a1dec257ba)
```
from category_encoders import TargetEncoder
```
```
te =TargetEncoder()
```
```
cc=df.copy()
```
```
new=te.fit_transform(cc['City'],cc['Target'])
```
```
cc=pd.concat([cc,new],axis=1)
```
```
cc
```
![image](https://github.com/user-attachments/assets/776ac0a4-1bb7-41ee-9857-ce32b4ee146b)
```
import pandas as pd
from scipy import stats
import numpy as np
```
```
df=pd.read_csv("/content/Data_to_Transform (1).csv")
```
```
df
```
![image](https://github.com/user-attachments/assets/d18668a7-0ef3-457c-baa6-f1a4eb6a9b7f)
```
df.skew()
```
![image](https://github.com/user-attachments/assets/e2e0bc67-d050-4d60-9611-c1da20bc6c55)

```
import pandas as pd
from scipy import stats
import numpy as np
df = pd.read_csv("/content/Data_to_Transform (1).csv")
print(df.columns)
np.log(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/31a6a116-cff1-4663-91bb-f9a9cc271b3b)
```
np.reciprocal(df['Moderate Positive Skew'])
```
![image](https://github.com/user-attachments/assets/f6e78e20-dfb0-44a3-a7df-290abb393fc2)
```
np.sqrt(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/940847df-48a5-4448-95a8-7555431cc4b8)
```
np.square(df["Highly Positive Skew"])
```
![image](https://github.com/user-attachments/assets/34d04df6-5385-4386-abef-645ad5fa9e7f)
```
df["Highly Positive Skew_boxcox"] = stats.boxcox(df["Highly Positive Skew"])[0]
```
```
df
```
![image](https://github.com/user-attachments/assets/884e0da4-2e51-4c11-8d3b-0895ac3e4e5c)
```
df["Moderate Positive Skew_yeojohnson"],parameters = stats.yeojohnson(df["Moderate Positive Skew"])
```
```
df
```
![image](https://github.com/user-attachments/assets/046fdaeb-31df-4e66-bbc7-6cd63a3ab9ed)
```
df.skew()
```
![image](https://github.com/user-attachments/assets/99abe093-9f8c-4465-aeb6-736695e7c970)
```
from sklearn.preprocessing import QuantileTransformer
```
```
qt=QuantileTransformer(output_distribution='normal')
```
```
df["Moderate Positive Skew_1"]=qt.fit_transform(df[["Moderate Positive Skew"]])
```
```
df
```
![image](https://github.com/user-attachments/assets/296f4bcd-4a3d-4261-bf4f-84dd57247aa0)
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
from statsmodels.graphics.gofplots import qqplot
sm_ = qqplot(df["Moderate Negative Skew"], line='45') # Use a different variable name to avoid conflicts
plt.show()
```
![image](https://github.com/user-attachments/assets/f9f0493a-3b31-4620-a01a-13853b8dcc2d)
```
sm=qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/47bbd135-cfb7-463b-97cf-fbc26db3f3c4)
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
```
```
df["Moderate Negative Skew_transformed"] = qt.fit_transform(df[["Moderate Negative Skew"]])
```
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
from statsmodels.graphics.gofplots import qqplot
sm_ = qqplot(df["Moderate Negative Skew"], line='45')
plt.show()
sm_transformed = qqplot(df["Moderate Negative Skew_transformed"], line='45')
plt.show()
```
![image](https://github.com/user-attachments/assets/184edb43-4a99-43d8-be9f-df431942d44f)
![image](https://github.com/user-attachments/assets/3d5c7871-3926-41db-ac91-6ac3748bd7aa)
![image](https://github.com/user-attachments/assets/827681ca-81c0-4f46-8365-08a3ac8aa248)

```
```
df=pd.read_csv("/content/titanic_dataset (2).csv")
```
```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
```
```
df["Age_1"]=qt.fit_transform(df[["Age"]])
```
```
sm.qqplot(df["Age_1"],line='45')
plt.show()
```
```
![image](https://github.com/user-attachments/assets/48124423-1095-4c8f-86bb-3f23f6986714)
```
# RESULT:
      Thus, we have read the given data and performed Feature Encoding and Transformation process and saved the data to the file.
      

       
