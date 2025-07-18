
# Data Cleaning Documentation

## bjective
The goal of the data cleaning phase is to prepare the uncleaned dataset (6 lakh rows) for time series modeling by handling:
- Timestamp inconsistencies,
- Duplicate records,
- Missing (null) values,
- Outliers in numerical columns,
- Ensuring overall data quality before model training.

## Dataset Used
- **Uncleaned Dataset:** `uncleaned_power_data_600k.csv`
- **Cleaned Dataset Output:** `cleaned_power_data_500k.csv`

## Cleaning Steps Breakdown

### 1. Timestamp Conversion and Sorting
- Converted the `Datetime` column to datetime format using `pd.to_datetime()`.
- Sorted the dataset in chronological order.
- **Purpose:** To ensure proper time-series alignment and enable chronological analysis.

```python
df['Datetime'] = pd.to_datetime(df['Datetime'], errors='coerce')
df.sort_values('Datetime', inplace=True)
```

### 2. Removing Timestamp Duplicates
- Removed duplicate rows based on the `Datetime` column.
- **Purpose:** Avoid duplicate time-stamps which can mislead time-series analysis.

```python
df.drop_duplicates(subset=['Datetime'], inplace=True)
```

### 3. Fixing Timestamp Gaps (Reindexing)
- Reindexed timestamps to ensure **equal time intervals** (1-minute frequency).
- Filled missing timestamps and corresponding rows with NaNs.
- **Purpose:** Maintain continuous time intervals without irregular gaps.

```python
full_range = pd.date_range(start=df['Datetime'].min(), end=df['Datetime'].max(), freq='1min')
df = df.set_index('Datetime').reindex(full_range).reset_index().rename(columns={'index': 'Datetime'})
```

### 4. Handling Missing Values
- **Checked null values** using `.isnull().sum()`.
- Handled nulls using **forward-fill method (ffill)**.
- **Purpose:** Ensure no missing consumption values in the cleaned dataset.

```python
df.fillna(method='ffill', inplace=True)
```

### 5. Outlier Removal (IQR Method)
- Applied Interquartile Range (IQR) method to remove outliers from:
  - `Global_active_power`, `Global_reactive_power`, `Voltage`, `Global_intensity`.
- **Purpose:** Remove extreme values to stabilize model performance.

```python
for col in ['Global_active_power', 'Global_reactive_power', 'Voltage', 'Global_intensity']:
    Q1 = df[col].quantile(0.25)
    Q3 = df[col].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    df = df[(df[col] >= lower) & (df[col] <= upper)]
```

### 6. Saving Cleaned Dataset
- Final cleaned dataset saved as `cleaned_power_data_500k.csv` containing approximately **5 lakh rows**.

```python
df.to_csv('cleaned_power_data_500k.csv', index=False)
```

## Results Summary
| Step | Rows Remaining |
|------|----------------|
| Initial Uncleaned Data | 600,000 |
| After Duplicate Removal | ~570,000 |
| After Null & Outlier Cleaning | ~500,000 |

## Conclusion
The cleaned dataset is now:
- Free from duplicates,
- Consistent in timestamps,
- Null-free after proper handling,
- Outlier-free for major features.

This dataset is ready for **Exploratory Data Analysis (EDA)** and **LSTM modeling**.
