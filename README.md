# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student

## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Import the required libraries which are used for the program.
2.Load the dataset.

3.Check for null data values and duplicate data values in the dataframe.

4.Apply logistic regression and predict the y output.

5.Calculate the confusion,accuracy and classification of the dataset. 

## Program:
```
/*
Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by: NITHYAA SRI S S
RegisterNumber: 212222230100 
*/

import pandas as pd
data=pd.read_csv("/content/Placement_Data.csv")
data.head()
data1=data.copy()
data1.head()
data1=data1.drop(['sl_no','salary'],axis=1)
data1.isnull().sum()
data1.duplicated().sum()
data1

from sklearn.preprocessing import LabelEncoder
le=LabelEncoder()
data1["gender"]=le.fit_transform(data["gender"])
data1["ssc_b"]=le.fit_transform(data["ssc_b"])
data1["hsc_b"]=le.fit_transform(data["hsc_b"])
data1["hsc_s"]=le.fit_transform(data["hsc_s"])
data1["degree_t"]=le.fit_transform(data["degree_t"])
data1["workex"]=le.fit_transform(data["workex"])
data1["specialisation"]=le.fit_transform(data["specialisation"])
data1["status"]=le.fit_transform(data["status"])
data1

x=data1.iloc[:,:-1]
x
y=data1["status"]
y
from sklearn.model_selection import train_test_split
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.2,random_state=0)

from sklearn.linear_model import LogisticRegression
model=LogisticRegression(solver="liblinear")
model.fit(x_train,y_train)
y_pred=model.predict(x_test)
from sklearn.metrics import accuracy_score,confusion_matrix,classification_report
accuracy =accuracy_score(y_test,y_pred)
confusion=confusion_matrix(y_test,y_pred)
cr=classification_report(y_test,y_pred)
print("Accuracy score:",accuracy)
print("\nConfusion Matrix:\n",confusion)
print("\nClassificatin Report:\n",cr)
from sklearn import metrics
cm_display=metrics.ConfusionMatrixDisplay(confusion_matrix=confusion,display_labels=[True,False])
cm_display.plot()
```

## Output:
![the Logistic Regression Model to Predict the Placement Status of Student](sam.png)




![image](https://github.com/ssnithyaasri/Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student/assets/119122478/77aa657a-e4f4-4ef5-9586-59aa39c537bc)






![image](https://github.com/ssnithyaasri/Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student/assets/119122478/59b31d35-06cb-49a2-aedd-d1fde23824e7)



## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
