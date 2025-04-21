To conduct a thorough analysis of evironmental factors in the Manesar area.

Summary :
Load and clean data to read excel and fix dates.
Describe and inspect to understand the structure and missing values.
Visualise trends : Time series plots to see changes over time.
correlation analysis : Find realtionship between variables. 
Rolling trends : Smooth out data to find underlying patterns.

Python code

import pandas as pd
df = pd.read_excel("Manesar_Environmental_Daily_Data.xlsx")
df.head()
df['Date] = pd.to_datetime(df['Date'])
df.info()
df.describe()
df.isnull().sum()
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 5))
plt.plot(df['Date'], df['Temperature (°C)'], label='Temperature (°C)', color='orange')
plt.title("Daily Temperature Trend")
plt.xlabel("Date")
plt.ylabel("Temperature (°C)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

import seaborn as sns
import numpy as np

num_cols = df.select_dtypes(include=[np.number]).columns
corr = df[num_cols].corr()

plt.figure(figsize=(14, 10))
sns.heatmap(corr, annot=True, cmap='coolwarm', fmt=".2f", square=True)
plt.title("Correlation Heatmap")
plt.tight_layout()
