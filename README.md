# Automated Stock Scanner

This project is an **Automated Stock Scanner** designed to analyze historical stock data, identify significant price levels, and evaluate opportunities for potential price appreciation. It leverages **Python**, **Pandas**, and **yFinance** for efficient data handling and stock market analysis.

---

## Key Features

1. **Stock Data Retrieval**:
   - Fetches historical stock data for a specified number of years using the `yfinance` library.

2. **Lifetime High Detection**:
   - Identifies the highest price ever recorded for a stock within the specified period.

3. **Support Level Detection**:
   - Detects if the lifetime high acts as a support level, based on price staying within a threshold percentage for consecutive trading days.

4. **Price Appreciation Analysis**:
   - Checks for significant price appreciation from the support level after the lifetime high is tested.

5. **Batch Processing**:
   - Scans multiple stocks and returns the ones meeting the predefined criteria.

6. **Results Analysis**:
   - Analyzes results to determine total instances, annual opportunities, and success rate.

---

## Prerequisites

- **Python 3.7+**
- **Required Libraries**:
  - `yfinance`
  - `pandas`

Install the required libraries using pip:
```bash
pip install yfinance pandas
```

---

## How It Works

### Functions

1. **`get_stock_data(stock_symbol, years=10)`**
   - Fetches historical stock data for the given symbol over the past `years`.

2. **`find_lifetime_high(stock_data)`**
   - Identifies the lifetime high price from the stock data.

3. **`check_support(stock_data, lifetime_high, threshold=0.02, days=5)`**
   - Checks if the lifetime high price acts as a support level by analyzing the stock’s low price over consecutive days within a specified threshold.

4. **`check_price_appreciation(stock_data, support_date, appreciation_threshold=0.10)`**
   - Verifies if the stock’s price appreciated by a defined percentage from the support level.

5. **`stock_scanner(stocks, years=10, threshold=0.02, days=5, appreciation_threshold=0.10)`**
   - Scans a list of stocks and identifies those meeting the lifetime high support and price appreciation criteria.

6. **`analyze_results(results)`**
   - Provides an analysis of the scanning results, including total instances found, annual opportunities, and success rate.

### Example Workflow

#### 1. Fetch Stock Data
```python
data = get_stock_data('AAPL', 10)
print(data.head())
```

#### 2. Scan Multiple Stocks
```python
stocks_to_scan = ['AAPL', 'MSFT', 'GOOGL']
results = stock_scanner(stocks_to_scan)
print(f'Stocks meeting criteria: {results}')
```

#### 3. Analyze Results
```python
if not results:
    print("NO Stocks Meeting the Criteria, hence can't perform analysis")
else:
    analyze_results(results)
```

---

## Output

- **Results Format**: A list of tuples, each containing the stock symbol and the date when the lifetime high was tested as support.
  ```
  [('AAPL', Timestamp('2023-06-15 00:00:00')), ('MSFT', Timestamp('2023-08-22 00:00:00'))]
  ```
- **Analysis**: Summary statistics, such as total instances, annual opportunities, and success rate.

---

## Customization

- **Parameters**:
  - `years`: Number of years of historical data to analyze (default: 10).
  - `threshold`: Percentage range for detecting support levels (default: 2%).
  - `days`: Minimum consecutive days for validating support levels (default: 5).
  - `appreciation_threshold`: Price appreciation percentage to check after support (default: 10%).

Modify these parameters in the function calls as per your requirements.

---

## Limitations

1. **Historical Data Only**:
   - Relies on historical data, which may not accurately predict future trends.

2. **Market Conditions**:
   - Does not account for market news, earnings reports, or macroeconomic factors.

3. **Static Criteria**:
   - Thresholds and days are static; advanced users can enhance the logic for dynamic thresholds.

---

## Future Enhancements

- **Visualization**:
  - Add support for plotting stock data and highlighting support levels and appreciations.
- **Backtesting**:
  - Include backtesting capabilities to simulate trading strategies based on detected patterns.
- **Real-Time Scanning**:
  - Integrate real-time data feeds for up-to-date scanning.

---

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute the code with attribution.

---

## Author

Daniyal Khan
Data Scientist and Stock Market Enthusiast

