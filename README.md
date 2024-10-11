# Stock Price Prediction Project

## Background

**Stock Price Prediction** involves forecasting future stock prices by analyzing historical data and other influential factors.

### Importance:
- **Informs investment strategies**: Helps investors make informed decisions.
- **Aids in managing financial risks**: Provides insights into market volatility.
- **Facilitates financial planning**: Assists in making long-term financial decisions.

### Challenges:
- **High volatility**: Stock prices can change rapidly and unpredictably.
- **Market efficiency**: Prices may already reflect all known information, making it harder to predict future movements.
- **External factors**: News, economic trends, and global events can significantly impact prices.
- **Data complexity**: Requires handling large amounts of diverse and multi-dimensional data.

## Exploratory Data Analysis (EDA) and Challenges

### Dataset Overview:
The dataset consists of **9202 rows** and **7 columns** related to stock trading data.

### Features:
- **日付け (Date)**: Stock trading date.
- **終値 (Closing Price)**: Price at market close.
- **始値 (Opening Price)**: Price at market open.
- **高値 (High Price)**: Highest price during the trading day.
- **安値 (Low Price)**: Lowest price during the trading day.
- **出来高 (Volume)**: Number of shares traded, represented as a string (e.g., `79.15M`, `173.91M`).
- **変化率 % (Change Rate %)**: Percentage change in stock price.

### Data Types:
- Most columns are numerical, except for **Date** and **Volume**. 
- The **Volume** is stored as a string with a suffix (`M` for million, `B` for billion) and needs conversion into a numerical format.
- **Change Rate %** is stored as a string and can be transformed into a numerical value for analysis.

### Key Insights:
- **Date Range**: The data spans multiple years, providing a robust time series for analysis.
- **Missing Data**: No missing values were found, but data cleaning is required for the **Volume** and **Change Rate %** columns.

### Challenges:
1. **Data Cleaning**: Standardizing volume formats and ensuring data consistency.
2. **Feature Selection**: Identifying the most relevant features for prediction.
3. **Data Normalization**: Scaling features to a common range for model input.

## Data Preprocessing

### Column Renaming:
The original column names were in Japanese, and were renamed for clarity:
- `日付け → Date`
- `終値 → Closing_Price`
- `始値 → Opening_Price`
- `高値 → High_Price`
- `安値 → Low_Price`
- `出来高 → Volume`

### Volume Conversion:
The **Volume** column was converted from strings (e.g., `79.15M`, `173.91M`) into numerical values for accurate analysis.

### Change Rate Removal:
The **Change Rate %** column was excluded to focus on stock price trends and technical indicators.

### Feature Engineering:
- **Simple Moving Average (SMA)**:
  - **SMA-20**: The average closing price over the last 20 days.
  - **SMA-50**: The average closing price over the last 50 days.
- **Relative Strength Index (RSI)**: A momentum indicator that measures the speed and change of price movements.

## Model and Architecture

### Input:
The model analyzes **500 days** of historical stock prices and trading volumes, along with calculated indicators such as:
- **20-day SMA**
- **50-day SMA**
- **RSI (Relative Strength Index)**

This extensive "window" of data helps the model capture patterns and movements in stock prices over time.

### Features:
Each **500-day sliding window** contains:
- **5 core features**: Closing Price, Opening Price, High Price, Low Price, and Volume.
- **3 engineered features**: 20-day SMA, 50-day SMA, and RSI.

### Shape of Input:
Each training example is represented as a matrix of size **(500 days, 8 features)**, with data from each of the 500 days across the 8 features.

## Conclusion:
This project aims to leverage historical stock data and technical indicators to predict future stock prices, while addressing challenges such as data cleaning and feature engineering. By using a sliding window approach, the model is trained on past price movements to capture trends and improve predictive accuracy.
