# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 13/05/2026


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

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv(
    "Customer_Transactions.csv",
    parse_dates=['last_purchase_date']
)

data.set_index('last_purchase_date', inplace=True)

monthly_data = data['avg_purchase_value'].resample('M').mean()

decomposition = seasonal_decompose(
    monthly_data,
    model='additive',
    period=12
)

plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(monthly_data, label='Average Purchase Value')
plt.legend(loc='upper left')
plt.title('Average Purchase Value')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend')
plt.legend(loc='upper left')
plt.title('Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()


```

















### OUTPUT:
<img width="925" height="554" alt="image" src="https://github.com/user-attachments/assets/ba9f9fc7-a6ca-486c-ad43-b173c35749df" />

<img width="911" height="552" alt="image" src="https://github.com/user-attachments/assets/c025f7dd-c786-4c2e-a3d1-5431a40c6c4d" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
