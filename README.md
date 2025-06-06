# 🚢 Titanic Dataset Analysis - Task 2

This notebook focuses on advanced data exploration and visualization techniques using the Titanic dataset. It includes statistical plots, correlation heatmaps, and outlier removal.
---

## 📁 Dataset

The dataset used is: `Titanic-Dataset.csv`  
It contains information about passengers aboard the Titanic, including their age, gender, class, and survival status.

---

## 📌 Workflow Summary

### 1. **Library Import and Data Load**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sb
import plotly as pt

df = pd.read_csv('/content/Titanic-Dataset.csv')
```

- pandas, numpy – data wrangling
- matplotlib, seaborn, plotly – visualization

---

### 2. **Initial Exploration**

```python
df.head()
df.info()
df.describe()
```

- Explore structure, types, and summary statistics.

---

### 3. **Boxplot for Outliers in Age**

```python
sb.boxplot(df['Age'])
```

- Visual inspection of Age distribution and outliers.
- Boxplot :
- ![image](https://github.com/user-attachments/assets/c959e431-c9ac-42a7-b315-0b4ea8265af8)

---
---

### 4. **Histogram Visualizations**

```python
cols = ['Age','Pclass','Survived']
fig, axes = plt.subplots(1,3,figsize=(12, 8))

for i, col in enumerate(cols):
    sb.histplot(data=df, x=col, kde=True, ax=axes[i], color='skyblue')

```

- Distribution plots for important numerical columns using histograms with KDE.
- Histogram :
- ![image](https://github.com/user-attachments/assets/60edacfa-3b71-4b2b-ac7e-23bca8877695)

---


### 5. **Correlation Heatmap**

```python
corr = df.corr(numeric_only=True)
sb.heatmap(corr, annot=True, cmap='coolwarm', center=0)

```

- Shows relationships between numeric columns.
- Heatmap :
- ![image](https://github.com/user-attachments/assets/300cf649-50a3-4d46-a94c-2bf08269edf5)

---

### 6. **Outlier Removal using IQR**

```python
def remove_outliers_iqr(df, column):
    Q1 = df[column].quantile(0.25)
    Q3 = df[column].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    return df[(df[column] >= lower) & (df[column] <= upper)]

df = remove_outliers_iqr(df, 'Age')
df = remove_outliers_iqr(df, 'Fare')

```

- Uses Interquartile Range (IQR) to remove outliers from Age and Fare.
- Output :
- ![image](https://github.com/user-attachments/assets/72e096a1-3fc6-4516-bfa7-734972dae831)

---

## 📊 Libraries Used

- **pandas** for data manipulation
- **numpy** for numerical operations
- **seaborn** and **matplotlib** for visualization

---







