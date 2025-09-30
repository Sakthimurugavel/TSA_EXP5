# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 30/9/25


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```
# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the dataset
# Example: Monthly Sales Data CSV with columns 'Month' and 'Sales'
data = pd.read_csv("C:/Users/admin/Downloads/archive/Sales Data.csv")

# Display first five rows
print("FIRST FIVE ROWS:")
print(data.head())

# Convert 'Month' to datetime and set as index
data['Month'] = pd.to_datetime(data['Month'])
data.set_index('Month', inplace=True)

# Select the sales column
sales = data['Sales'].dropna()

# Perform seasonal decomposition (monthly data, period=12)
decomposition = seasonal_decompose(sales, model='additive', period=12)

# Plot decomposition
plt.figure(figsize=(10,12))

# Original Data
plt.subplot(411)
plt.plot(sales, label='Original Sales')
plt.legend(loc='upper left')
plt.title('Original Sales Data')

# Trend
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

# Residual
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()

# Overall representation combining original, trend, and seasonal
plt.figure(figsize=(10,5))
plt.plot(sales, label='Original Sales')
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend()
plt.title('Overall Sales Time Series Representation')
plt.show()
```















### OUTPUT:
FIRST FIVE ROWS:

<img width="657" height="365" alt="495309807-8c83e665-f96c-4e96-ae51-aa55c45d506a" src="https://github.com/user-attachments/assets/9e37e498-753b-4f01-bf09-93ec1f51c593" />


PLOTTING THE DATA:
<img width="993" height="306" alt="495311123-b7dbd316-b5d4-4eb5-b674-27a32088460c" src="https://github.com/user-attachments/assets/4df3d133-2f89-4d11-aef0-6eebe0ab7159" />

SEASONAL PLOT REPRESENTATION :


<img width="1001" height="292" alt="495310719-5232184c-9768-4993-a280-e83ce8a4cd5a" src="https://github.com/user-attachments/assets/5bc43af3-bf18-4805-a860-3e7953459c16" />

TREND PLOT REPRESENTATION :
<img width="1019" height="293" alt="495310792-327bfb7e-abee-471c-9302-d203e3eea58f" src="https://github.com/user-attachments/assets/395a12bd-f1b0-402d-91b7-82e06af29dc8" />

RESIDUAL PLOT:
<img width="999" height="302" alt="495311978-4d257430-0fd2-4154-9e60-6340103509c5" src="https://github.com/user-attachments/assets/81adcd1a-5aae-47ec-9129-ba37c22937c4" />

OVERAL REPRESENTATION:
<img width="875" height="432" alt="495310833-1ce371df-7e3c-46a9-a130-fcf23aebb5f7" src="https://github.com/user-attachments/assets/2131bad5-c1cd-4377-801c-d89c7f3ab293" />



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
