# Time-Series-Model-Using-the-Craigslist-Vehicles-Dataset-
**Time-Series Model Using the Craigslist Vehicles Dataset**

**Data Preprocessing**

```python
import pandas as pd

# Load the dataset
data = pd.read_csv('craigslist_vehicles.csv')

# Handling missing values
data['price'].fillna(data['price'].median(), inplace=True)
data['year'].fillna(data['year'].median(), inplace=True)
data['odometer'].fillna(data['odometer'].median(), inplace=True)
data['manufacturer'].fillna(data['manufacturer'].mode()[0], inplace=True)
data['model'].fillna(data['model'].mode()[0], inplace=True)
data['condition'].fillna(data['condition'].mode()[0], inplace=True)
data['cylinders'].fillna(data['cylinders'].mode()[0], inplace=True)
data['fuel'].fillna(data['fuel'].mode()[0], inplace=True)
```

**Date time conversion** 

```python
# Convert 'posting_date' to datetime
data['posting_date'] = pd.to_datetime(data['posting_date'])

# Set 'posting_date' as the index
data.set_index('posting_date', inplace=True)

```

**Exploratory Data Analysis**
Explore the data using visualizations and statistical analysis techniques to understand temporal patterns, identify seasonal trends, and analyze demand-supply dynamics by region Price distribution and time series chart.

**Visualizations**
```python
import matplotlib.pyplot as plt
import seaborn as sns

#Visualizations
# Example 1: Price distribution
plt.figure(figsize=(10, 6))
sns.histplot(data['price'], kde=True)
plt.xlabel('Price')
plt.title('Price Distribution')
plt.show()

```

 **Time series chart**
```python

# Example 2: Time series chart
data['price'].resample('M').mean().plot(figsize=(12, 6))
plt.xlabel('Date')
plt.ylabel('Average Price')
plt.title('Average Price Over Time')
plt.show()

```

**Demand by region**
```python
# Example 3: Demand by region
plt.figure(figsize=(12, 6))
sns.countplot(x='region', data=data, order=data['region'].value_counts().index[:10])
plt.xticks(rotation=45)
plt.xlabel('Region')
plt.ylabel('Number of Listings')
plt.title('Top 10 Regions by Listings')
plt.show()

```
