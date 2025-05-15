Enhanced Stock Dataset Documentation
Overview
This dataset contains stock price data for 5 different stocks along with major market indices (Dow Jones, NASDAQ, and S&P 500). The data has been enhanced with various technical indicators and features commonly used in financial analysis and algorithmic trading.

Dataset Statistics
Number of rows: 2569
Number of columns: 221
Date range: 2015-01-05 to 2025-03-21
Number of stocks: 5
Number of market indices: 3
Feature Naming Conventions
Features ending with numbers (e.g., return_1, close_2) refer to specific stocks (1-5)
Features with X_Y format (e.g., ma10_3, beta_2_nasdaq_20) have the following pattern:
First number/name refers to the parameter or stock
Second number/name refers to the stock or index
Third number (if present) refers to the time window
Correlation features (e.g., corr_1_2) show correlation between two stocks (stock 1 and stock 2)
Feature Categories
Basic Price Data
Date: Trading date in YYYY-MM-DD format
return_X: Daily return (percentage price change) for stock X (where X is 1-5)
open_X: Opening price for stock X
high_X: Highest price during the trading day for stock X
low_X: Lowest price during the trading day for stock X
close_X: Closing price for stock X
adjusted_X: Adjusted closing price for stock X (accounts for dividends and splits)
volume_X: Trading volume (number of shares traded) for stock X
Market Index Data
returns_dj: Daily return for Dow Jones Industrial Average
close_dj: Closing price for Dow Jones Industrial Average
returns_nasdaq: Daily return for NASDAQ Composite Index
close_nasdaq: Closing price for NASDAQ Composite Index
returns_SP500: Daily return for S&P 500 Index
close_SP500: Closing price for S&P 500 Index
Moving Averages and Trend Indicators
maX_Y: X-day simple moving average of closing price for stock Y
emaX_Y: X-day exponential moving average of closing price for stock Y
envelope_upper_X: Upper price envelope (5% above MA10) for stock X
envelope_lower_X: Lower price envelope (5% below MA10) for stock X
Momentum and Volatility Indicators
rocX_Y: X-day Rate of Change (percentage) for stock Y
volatility_X: 20-day rolling standard deviation of returns for stock X
rsi_X: 14-day Relative Strength Index for stock X (momentum indicator, 0-100)
macd_X: Moving Average Convergence Divergence for stock X (ema12 - ema26)
macd_signal_X: 9-day EMA of MACD for stock X
macd_hist_X: MACD histogram for stock X (macd - macd_signal)
Volume Indicators
volume_ma10_X: 10-day moving average of trading volume for stock X
volume_ratio_X: Ratio of current volume to 10-day volume MA for stock X
Price Ratio Indicators
high_low_ratio_X: Ratio of high price to low price for stock X (daily range)
close_open_ratio_X: Ratio of close price to open price for stock X (intraday movement)
Correlation and Beta Indicators
beta_X_Y_Z: Z-day rolling beta of stock X to index Y (measure of volatility relative to market)
corr_X_Y: 20-day rolling correlation between returns of stock X and stock Y (ranges from -1 to 1)
Example Usage
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv('enhanced_stock_dataset.csv')
df['Date'] = pd.to_datetime(df['Date'])

# Plot closing prices for all stocks
plt.figure(figsize=(12, 6))
for i in range(1, 6):
    plt.plot(df['Date'], df[f'close_{i}'], label=f'Stock {i}')
plt.title('Stock Closing Prices')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.grid(True)
plt.show()
Notes
This dataset contains engineered features that can be directly used for machine learning models
All NaN values have been filled using forward and backward filling methods
The correlation features (corr_X_Y) show the relationship between different stocks
Beta values show the relationship between each stock and the market indices
