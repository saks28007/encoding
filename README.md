# EXP 3 : Categorical Data Encoding Techniques
This repository demonstrates various categorical data encoding techniques used in machine learning, including Label Encoding, One-Hot Encoding, Ordinal Encoding, Target Encoding, Binary Encoding, and Frequency Encoding. Each method is explained with examples to help users convert categorical variables into numerical formats for model training.

# Experiment Overview
# Steps:
**1. Label Encoding :** *Converts categorical labels into numerical values.*
<br>
**2. One-Hot Encoding :** *Converts categorical variables into a format where each category gets its own column with binary values (0 or 1).*
<br>
**3. Ordinal Encoding :** *Encodes categorical variables that have an inherent order (e.g., low, medium, high).*
<br>
**4. Target Encoding :** *Encodes categorical variables based on the target variable (the value of the target is used to compute the encoding).*
<br>
**5. Binary Encoding :** *Combines the benefits of both one-hot encoding and label encoding to reduce dimensionality.*
<br>
**6. Frequency Encoding :** *Encodes categorical variables based on the frequency of each category in the dataset.*

# Key Concepts Applied:
**-Label Encoding :** _Transforming categorical labels into numerical format using LabelEncoder._
<br>
**-One-Hot Encoding :** _Creating binary columns for each category using pd.get_dummies()_
<br>
**-Ordinal Encoding :** _Assigning a specific numerical value to each category based on a defined order using OrdinalEncoder._
<br>
**-Target Encoding :** _Encoding categorical variables based on their relationship with the target variable using the TargetEncoder from the category_encoders library._
<br>
**-Binary Encoding :** _Reducing dimensionality while encoding categories into binary values using BinaryEncoder from category_encoders._
<br>
**-Frequency Encoding :** _Replacing each category with its frequency (count of occurrences) using pandas' value_counts()._

# Action Plan
**1. Get started with Google Colab :**

 *~Launch Google Colab.*
 <br>
 *~Start a fresh notebook.*

 **2. Set up the Environment :**

 *~Import necessary libraries for encoding and data manipulation.*
 
 _# Import LabelEncoder from sklearn.preprocessing for label encoding._
 
 _# Import pandas for data handling and category_encoders for target and binary encoding._
 
_# Install the category_encoders library if not already installed (!pip install category_encoders)._

**3. Label Encoding :**

*~Create a list of categorical data (e.g., ['Low','High','Medium','High','Medium']).*

*~Apply LabelEncoder() to convert these categories into numerical values.*

*~Print the encoded data for verification.*
```
from sklearn.preprocessing import LabelEncoder
data=['Low','High','Medium','High','Medium']

encoder= LabelEncoder()
encoded_data=encoder.fit_transform(data)
print(f"Label encoded data:\n{encoded_data}")
```

**4. One-Hot Encoding :**

*~Create a list of categorical data (e.g., ['Red','Blue','Green','Blue','Red']).*

*~Use pandas.get_dummies() to create one-hot encoded columns from the data.*

*~Print the one-hot encoded DataFrame for verification.**
```
import pandas as pd
data=['Red','Blue','Green','Blue','Red']
df= pd.DataFrame(data,columns=['Color'])

one_hot_encoded=pd.get_dummies(df['Color'])
print("\nOne hot encoded:")
print(one_hot_encoded)
```

**5. Ordinal Encoding :**

*~Create a list of ordered categorical data (e.g., [['Low'], ['High'], ['Medium']]).*

*~Define a specific order for the categories using the OrdinalEncoder() and apply it.*

*~Print the ordinal encoded data for verification.*
```
from sklearn.preprocessing import OrdinalEncoder
data=[['Low'],['High'],['Medium'],['High'],['Medium']]

encoder=OrdinalEncoder(categories=[['Low','Medium','High']])
encoded_data=encoder.fit_transform(data)
print(f"\nOrdinal Encoded Data:\n{encoded_data}")
```

**6. Target Encoding :**

*~Create a DataFrame with both categorical data (Color) and the target variable (Target).*

*~Convert the Target column to integer type.*

*~Use TargetEncoder from category_encoders to encode the Color column based on the target variable.*

*~Print the target encoded data for verification.*
```
!pip install category_encoders
import pandas as pd
import category_encoders as ce

data={'Color':['Red','Blue','Green','Blue','Red','Blue','Green','Green','Green','Blue'],'Target':['1','0','0','1','1','1','0','1','0','1']}
df=pd.DataFrame(data)

df['Target'] = df['Target'].astype(int)
encoder= ce.TargetEncoder(cols=['Color'])

encoded_data=encoder.fit_transform(df['Color'],df['Target'])
print(f"\nTarget encoded:\n{encoded_data}")
```

**7. Binary Encoding :**

*~Create a list of categorical data (e.g., ['Red','Green','Blue','Blue','Grey']).*

*~Use BinaryEncoder from category_encoders to apply binary encoding on the data.*

*~Print the binary encoded DataFrame for verification.*
```
import category_encoders as ce
data=['Red','Green','Blue','Blue','Grey']

encoder = ce.BinaryEncoder(cols=['Color'])

encoded_data=encoder.fit_transform(pd.DataFrame(data,columns=['Color']))

print("\nbinary encoded:")
print(encoded_data)
```

**8. Frequency Encoding :**

*~Create a list of categorical data (e.g., ['Red','Green','Blue','Red','Red']).*

*~Use value_counts() from pandas to calculate the frequency of each category.*

*~Encode the data by replacing each category with its frequency.*

*~Print the frequency encoded data for verification.*
```
import pandas as pd
data=['Red','Green','Blue','Red','Red']

series_data= pd.Series(data)
frequency_encoding=series_data.value_counts()
series_data.value_counts()

encoded_data= [frequency_encoding[x] for x in data]

print("\nFrequency encoded:\n")
print("Encoded data:",encoded_data)
```

**9. End the Experiment :**

*~The experiment is complete once all encoding methods are executed and results are displayed.*



