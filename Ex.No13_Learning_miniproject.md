# Ex.No: 10 Learning – Use Supervised Learning  
### DATE: 10.10.2024                                                                           
### REGISTER NUMBER : 212222220027
### AIM: 
To develop a machine learning model that accurately detects fraudulent online payment transactions.
###  Algorithm:
## Step 1: Import the necessary libaries
## Step 2 : Import the dataset
## Step 3: preprocess the Dataset,remove all the null values and replace it with mean
## Step 4: split the training and testing dataset
## Step 5: Train the model with DesicionTree Classifier
## Step 6: Find out the accuracy and increase it if possibleby increasing the number of decisiontree

### Program:
```
import pandas as pd
import numpy as np
import plotly.express as px
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
data = pd.read_csv("../input/online-payment-fraud-detection/onlinefraud.csv")
print(data.head())
data.shape
print(data.isnull().sum())
print(data.type.value_counts())
type = data["type"].value_counts()
transactions = type.index
quantity = type.values
figure = px.pie(data, values=quantity, names=transactions, hole = 0.5, title="Distribution of Transaction Type")
figure.show()

# Now let’s have a look at the correlation between the features of the data with the isFraud column
# Checking correlation

correlation = data.corr()
print(correlation["isFraud"].sort_values(ascending=False))
# Now let’s transform the categorical features into numerical. Here we will also transform the values of the isFraud column into 
# No Fraud and Fraud labels to have a better understanding of the output
# Changing CASH_OUT to 1, PAYMENT to 2, CASH_IN to 3, TRANSFER to 4 and DEBIT to 5 

data["type"] = data["type"].map({"CASH_OUT": 1, "PAYMENT": 2, "CASH_IN": 3, "TRANSFER": 4, "DEBIT": 5})
data["isFraud"] = data["isFraud"].map({0: "No Fraud", 1: "Fraud"})
print(data.head())
# splitting the data

x = np.array(data[["type", "amount", "oldbalanceOrg", "newbalanceOrig"]])
y = np.array(data[["isFraud"]])
# training a machine learning model

xtrain, xtest, ytrain, ytest = train_test_split(x, y, test_size=0.10, random_state=42)
model = DecisionTreeClassifier()
model.fit(xtrain, ytrain)
print(model.score(xtest, ytest))
# prediction
#features = [type, amount, oldbalanceOrg, newbalanceOrig]

features = np.array([[1, 8900.2, 8990.2, 0.0]])
print(model.predict(features))
```

### Output:

![Screenshot 2024-11-11 160117](https://github.com/user-attachments/assets/34e40d8f-8823-44cf-b819-24bcae566342)
![Screenshot 2024-11-11 155706](https://github.com/user-attachments/assets/a066bad4-bb79-490f-b3a8-46795eb4eb94)
![Screenshot 2024-11-11 160132](https://github.com/user-attachments/assets/cce89510-983f-43da-a7b2-f5f6f05e2f9e)
![Screenshot 2024-11-11 160145](https://github.com/user-attachments/assets/8de6ff44-9213-4904-9969-0a8f7e3cfc9b)
![Screenshot 2024-11-11 160200](https://github.com/user-attachments/assets/45204d8a-7b30-4601-bfe1-4173967464a6)
![Screenshot 2024-11-11 160217](https://github.com/user-attachments/assets/d558703a-cab5-44a3-ad46-2c931b8319d1)
![Screenshot 2024-11-11 160231](https://github.com/user-attachments/assets/b4365c9c-da25-414c-9d58-240b6087dcca)
![Screenshot 2024-11-11 160247](https://github.com/user-attachments/assets/52a63151-71b9-46cb-b6b5-4f429c296fc8)
![Screenshot 2024-11-11 160256](https://github.com/user-attachments/assets/3087d1f1-a032-4b78-82f1-e430b5e5e993)





### Result:
Thus the system was trained successfully and the prediction was carried out.
