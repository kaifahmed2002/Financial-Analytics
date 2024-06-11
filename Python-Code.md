~~~ Python

import pandas as pd

# Load the dataset
dataset_path = "Financial Analytics data.csv"
df = pd.read_csv(dataset_path)

# Inspect the dataset
print(df.head())  # Display first few rows
print(df.info())  # Display dataset information
import seaborn as sns
import matplotlib.pyplot as plt

# Check column names
print(df.columns)

# Clean column names (if needed)
df.columns = df.columns.str.strip()  # Remove leading/trailing spaces
df.columns = df.columns.str.replace('–', '-')  # Replace non-standard dashes

# Summary statistics
print(df.describe())

# Distribution of Market Capitalization
plt.figure(figsize=(10, 6))
sns.histplot(df['Mar Cap - Crore'], kde=True)
plt.title('Distribution of Market Capitalization')
plt.xlabel('Market Capitalization (Crore)')
plt.ylabel('Frequency')
plt.show()

# Correlation between Market Capitalization and Quarterly Sales
plt.figure(figsize=(10, 6))
sns.scatterplot(x='Mar Cap - Crore', y='Sales Qtr - Crore', data=df)
plt.title('Market Capitalization vs Quarterly Sales')
plt.xlabel('Market Capitalization (Crore)')
plt.ylabel('Quarterly Sales (Crore)')
plt.show()

# Top Companies by Market Capitalization
top_companies = df.sort_values(by='Mar Cap - Crore', ascending=False).head(10)
plt.figure(figsize=(10, 6))
sns.barplot(x='Mar Cap - Crore', y='Name', data=top_companies)
plt.title('Top 10 Companies by Market Capitalization')
plt.xlabel('Market Capitalization (Crore)')
plt.ylabel('Company')
plt.show()
