# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import pandas and matplotlib.pyplot libraries.

2.Read the CSV file Mall_Customers.csv using pd.read_csv().

3.Display the first few rows using data.head(), and check data info and missing values using data.info() and data.isnull().sum().

4.Select relevant features for clustering using data.iloc[:, 3:].

5.Initialize an empty list wcss = [] to store Within-Cluster Sum of Squares.

6.Loop from i = 1 to 10: create and fit a KMeans model with i clusters, and append inertia_ to wcss.

7.Plot wcss vs number of clusters to apply the Elbow Method and determine optimal number of clusters.

8.Create a KMeans model with n_clusters = 5, fit it on the selected features, and predict cluster labels.

9.Store the predicted cluster labels in a new column data["cluster"].

10.Split data into separate DataFrames based on cluster labels and plot them using plt.scatter() with different colors.


## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: DIVYA R
RegisterNumber:  212222040040
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]

for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init="k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of. clusters")
plt.ylabel("wcss")
plt.title("Elbow method")

km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")


```

## Output:

## data.head()
![image](https://github.com/user-attachments/assets/9dcc89c6-65fd-4728-9000-137163c0bfc9)

## data.info()
![image](https://github.com/user-attachments/assets/93ca24d1-add1-4c84-8642-ccea061bb707)

## data.isnull().sum()
![image](https://github.com/user-attachments/assets/d876991d-4133-480a-aacf-0d5c9b437496)

## Elbow Method
![image](https://github.com/user-attachments/assets/3c4f7b0e-158b-41b2-8b0a-0e5e247c648f)

## KMeans
![image](https://github.com/user-attachments/assets/6c3bdcda-4232-41b5-a227-c73adcf931e5)

## y_pred
![image](https://github.com/user-attachments/assets/8944c522-22dc-435a-bdfb-9c9a539b7149)

## Customer Segments
![image](https://github.com/user-attachments/assets/f347ed2f-fce2-4366-b0d2-5489d5099329)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
