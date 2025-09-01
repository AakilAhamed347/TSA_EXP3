# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Date: 01.09.25

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
~~~
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.graphics.tsaplots import plot_acf

# Load the dataset

data = pd.read_csv("housing_price_dataset.csv.zip")

# Inspect the dataset structure
print("Dataset columns:", data.columns)
print(data.head())

# Convert 'Date' to datetime if it exists
if 'Date' in data.columns:
    data['Date'] = pd.to_datetime(data['Date'], errors='coerce')
    data.set_index('Date', inplace=True)

# Choose the price column (adjust based on dataset)
# Example: if the column is 'AveragePrice' or 'Housing_Price', replace below
price_column = 'Price'  # <-- change this if column name differs
price_data = data[price_column]

# Compute and plot ACF for the first 35 lags
plt.figure(figsize=(10, 6))
plot_acf(price_data, lags=35, alpha=0.05)
plt.title('AutoCorrelation Function (ACF) for Housing Price')
plt.xlabel('Lags')
plt.ylabel('ACF Value')
plt.grid(True)
plt.show()
~~~
### OUTPUT:
<img width="865" height="570" alt="image" src="https://github.com/user-attachments/assets/641a8d6d-4d2c-43a7-b59d-13a371be40e7" />

### RESULT:
Thus we have successfully implemented the auto correlation function in python.
