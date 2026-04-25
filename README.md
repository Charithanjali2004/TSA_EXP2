# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date:25/04/26
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:
A - LINEAR TREND ESTIMATION
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
data=pd.read_csv('DailyDelhiClimateTest.csv')
data.head()
data['date'] = pd.to_datetime(data['date'])
data = data.sort_values('date')
data['date'] = data['date'].apply(lambda x: x.toordinal())
X = data['date'].values.reshape(-1, 1)
y = data['meanpressure'].values
linear_model = LinearRegression()
linear_model.fit(X, y)
data['Linear_Trend'] = linear_model.predict(X)
plt.figure(figsize=(10,6))
plt.plot(data['date'], data['meanpressure'],label='Original Data')
plt.plot(data['date'], data['Linear_Trend'], color='red', label='Linear Trend')
plt.title('Linear Trend Estimation')
plt.xlabel('date')
plt.ylabel('meanpressure')
plt.legend()
plt.grid(True)
plt.show()
```
B- POLYNOMIAL TREND ESTIMATION
```
poly_features = PolynomialFeatures(degree=2)
X_poly = poly_features.fit_transform(X)
poly_model = LinearRegression()
poly_model.fit(X_poly, y)
data['meanpressure'] = poly_model.predict(X_poly)
plt.figure(figsize=(10,6))
plt.bar(data['date'], data['meanpressure'], label='Original Data', alpha=0.6)
plt.plot(data['date'], data['meanpressure'],color='yellow', label='Poly Trend(Degree 2)')
plt.title('Polynomial Trend Estimation')
plt.xlabel('date')
plt.ylabel('meanpressure')
plt.legend()
plt.grid(True)
plt.show()
```
### OUTPUT
A - LINEAR TREND ESTIMATION

<img width="1212" height="632" alt="image" src="https://github.com/user-attachments/assets/5d284f7f-fa8f-45a0-8a5f-9041c52c17af" />

B- POLYNOMIAL TREND ESTIMATION

<img width="1176" height="627" alt="image" src="https://github.com/user-attachments/assets/2fa19e18-1e36-4de2-968a-2aac52158e98" />

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
