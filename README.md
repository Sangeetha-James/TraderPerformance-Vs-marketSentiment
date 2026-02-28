# Trader Performance vs Market Sentiment

## Overview
This project analyzes trader behavior and performance on the Hyperliquid platform, with the goal of understanding how trading activity, risk exposure, and profitability behave at a daily level. The original objective was to relate trader performance to market sentiment (Fear vs Greed), while also uncovering behavioral patterns that could inform better trading strategies.

---

## Datasets Used

### 1. Bitcoin Market Sentiment (Fear/Greed Index)
- Columns: `date`, `classification`
- Classification indicates whether the market sentiment was **Fear** or **Greed** on a given day.

### 2. Historical Trader Data (Hyperliquid)
- Includes trade-level data such as:
  - Account
  - Trade size
  - Side (BUY/SELL)
  - Timestamp
  - Closed PnL

---

## Methodology

### Data Preparation
- Loaded and inspected both datasets for missing values and duplicates.
- Cleaned and standardized column names.
- Parsed trade timestamps using mixed-format datetime handling to account for:
  - Epoch millisecond timestamps
  - Formatted datetime strings
- Aggregated trade-level data to **daily trader-level metrics**, including:
  - Daily PnL
  - Number of trades per day
  - Win rate
  - Total exposure
  - Long/short ratio

### Feature Engineering
Key metrics created for analysis:
- `daily_pnl`: Sum of closed PnL per trader per day
- `number_of_trades`: Count of trades per trader per day
- `win_rate`: Fraction of profitable trades
- `total_exposure`: Sum of absolute trade sizes per day
- `long_ratio`: Proportion of long (BUY) trades

---

## Data Limitation: Sentiment Alignment

After aligning timestamps and aggregating data at a daily level, it was found that the historical trader activity dates **do not overlap** with the provided Fear/Greed sentiment dates.

As a result:
- Sentiment-based comparisons (Fear vs Greed) could not be computed reliably.
- This limitation was identified through explicit date range and overlap checks.
- No sentiment labels were inferred or imputed artificially.

The analysis therefore focuses on trader behavior and performance metrics **independent of sentiment**, while clearly documenting this limitation.

---

## Analysis Performed

Despite the sentiment limitation, meaningful behavioral insights were extracted, including:
- Distribution of daily trade frequency
- Distribution of daily PnL
- Exposure (risk) distribution
- Relationship between trade frequency and win rate

Visualizations were created using histograms, scatter plots, and summary statistics to support these findings.

---

## Key Insights

- Trader activity varies significantly day to day, with most traders executing a small number of trades per day.
- Daily PnL exhibits a heavy-tailed distribution, indicating occasional large gains or losses.
- Higher trade frequency does not consistently lead to higher win rates, suggesting diminishing returns from overtrading.
- Risk exposure varies widely across traders, emphasizing the importance of exposure management.

---

## Strategy Recommendations

- Avoid excessive trade frequency, as increased activity does not guarantee improved outcomes.
- Monitor and control exposure due to the heavy-tailed nature of PnL distributions.
- Future sentiment-based strategies should ensure proper temporal alignment between market signals and trading activity.

---

## How to Run

1. Clone the repository:
   ```bash
   git clone <my-repo-link>
2.Install dependencies:
pip install pandas numpy matplotlib seaborn
3.Open the notebook:
jupyter notebook Trader_Performance_Vs_MarketSentiment.ipynb
4.Run cells sequentially.

Conclusion

This project demonstrates a structured approach to analyzing real-world trading data, handling messy timestamps, identifying data limitations, and extracting actionable behavioral insights. While sentiment-based analysis was constrained by data availability, the analysis remains robust, transparent, and reproducible.

Author

Sangeetha


   
