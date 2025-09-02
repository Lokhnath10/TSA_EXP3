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
import matplotlib.pyplot as plt

import numpy as np

file_path = "/content/BMW_Car_Sales_Classification.csv"  # update path if needed
df = pd.read_csv(file_path)

data = df["Sales_Volume"].values

#### Define lags
lags = range(35)


#### Pre-allocate autocorrelation table
acf_values = []

#### Mean
mean_val = np.mean(data)

#### Variance
var_val = np.var(data)

#### Normalized data
normalized_data = data - mean_val

#### Go through lag components one-by-one
for lag in lags:
    if lag == 0:
        acf = 1  # Autocorrelation at lag 0 is always 1
    else:
        num = np.sum(normalized_data[:-lag] * normalized_data[lag:])
        den = np.sum(normalized_data ** 2)
        acf = num / den
    acf_values.append(acf)

#### display the graph
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, basefmt=" ")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.title("Autocorrelation Function (Sales_Volume)")
plt.grid(True)
plt.show()


### OUTPUT:
<img width="860" height="553" alt="image" src="https://github.com/user-attachments/assets/f16a236e-d965-4ac1-9e67-9a38d5920a8d" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
