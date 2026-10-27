# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 13/10/2026

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

df = df = pd.read_csv("Electric_Production.csv")
x = pd.to_datetime(df['DATE'])
y = df['PRODUCTION']

#Regular Differencing
df["y_diff"] = np.ones(y.shape[0])
for i in range(len(y)-1, 0, -1):
    df["y_diff"][i] = y[i] - y[i-1]
df["y_diff"][0] = np.nan
plt.plot(x, df['y_diff'], color="Red")
plt.xlabel("Date")
plt.ylabel("Electric Production")
plt.title("Regular Differencing Technique applied on Electric Production in the United States")
plt.show()

#Seasonal Transformation
from statsmodels.tsa.seasonal import seasonal_decompose
result = seasonal_decompose(y, model='additive', period=12)
df['y_sea_diff']=result.resid
plt.plot(x, df['y_sea_diff'], color="Green")
plt.xlabel("Date")
plt.ylabel("Electric Production")
plt.title("Seasonal Differencing applied on Electric Production in the United States")
plt.show()

#Log Transformation
df['y_log'] = np.log(y)
df['y_log_diff']= df['y_log']-df['y_log'].shift(1)
plt.plot(x, df['y_log'], color="Green")
plt.xlabel("Date")
plt.ylabel("Electric Production")
plt.title("Log applied on Electric Production in the United States")
plt.show()
```

### OUTPUT:


REGULAR DIFFERENCING:<br>
<img width="702" height="455" alt="image" src="https://github.com/user-attachments/assets/1058634a-0886-48a1-9405-d651c9956f9a" />


SEASONAL ADJUSTMENT:<br>
<img width="624" height="455" alt="image" src="https://github.com/user-attachments/assets/7fa97c64-0dfc-4683-9cb6-4215f849b94c" />


LOG TRANSFORMATION:<br>

<img width="567" height="455" alt="image" src="https://github.com/user-attachments/assets/637d1ea4-88e7-40bd-8c6e-948bcf50646f" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
