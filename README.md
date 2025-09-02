# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

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
```
import matplotlib.pyplot as plt

import numpy as np

import pandas as pd

file_path = 'clothes_price_prediction_data.csv'  
data_df = pd.read_csv(file_path)

display(data_df.head())

data_to_analyze = data_df['Price']

data_to_analyze = data_to_analyze.to_numpy()
lags = range(35)
autocorr_values = []
mean_data = np.mean(data_to_analyze)
variance_data = np.var(data_to_analyze)
normalized_data = (data_to_analyze - mean_data) / np.sqrt(variance_data)
N = len(data_to_analyze)
for lag in lags:
  if lag == 0:
    autocorr_values.append(1)
  else:
    auto_cov = np.sum((data_to_analyze[:-lag] - mean_data) * (data_to_analyze[lag:] - mean_data)) / N  
    autocorr_values.append(auto_cov / variance_data) 

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Price Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="846" height="547" alt="image" src="https://github.com/user-attachments/assets/2c453a3e-1b07-4350-804f-6199ab16bb65" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
