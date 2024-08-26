# Optiver Trading at the Close - Kaggle Challenge

Welcome to my repository for the [Optiver - Trading at the Close](https://www.kaggle.com/competitions/optiver-trading-at-the-close) Kaggle challenge. This repository contains my code, experiments, and documentation for the competition.

## Overview

The challenge is to predict the price movements in the last 10 minutes of the trading day, which is crucial for many trading strategies. The objective is to develop models that can accurately predict these movements to maximize returns.

## Dataset
### stock_id - A unique identifier for the stock. Not all stock IDs exist in every time bucket.
### date_id - A unique identifier for the date. Date IDs are sequential & consistent across all stocks.
### imbalance_size - The amount unmatched at the current reference price (in USD).
### imbalance_buy_sell_flag - An indicator reflecting the direction of auction imbalance.
buy-side imbalance; 1
sell-side imbalance; -1
no imbalance; 0
### reference_price - The price at which paired shares are maximized, the imbalance is minimized and the distance from the bid-ask midpoint is minimized, in that order. Can also be thought of as being equal to the near price bounded between the best bid and ask price.
### matched_size - The amount that can be matched at the current reference price (in USD).
### far_price - The crossing price that will maximize the number of shares matched based on auction interest only. This calculation excludes continuous market orders.
### near_price - The crossing price that will maximize the number of shares matched based auction and continuous market orders.
### [bid/ask]_price - Price of the most competitive buy/sell level in the non-auction book.
### [bid/ask]_size - The dollar notional amount on the most competitive buy/sell level in the non-auction book.
### wap - The weighted average price in the non-auction book.
BidPrice∗AskSize+AskPrice∗BidSizeBidSize+AskSize
### seconds_in_bucket - The number of seconds elapsed since the beginning of the day's closing auction, always starting from 0.
### target - The 60 second future move in the wap of the stock, less the 60 second future move of the synthetic index. Only provided for the train set.
The synthetic index is a custom weighted index of Nasdaq-listed stocks constructed by Optiver for this competition.
The unit of the target is basis points, which is a common unit of measurement in financial markets. A 1 basis point price move is equivalent to a 0.01% price move.
Where t is the time at the current observation, we can define the target:
### Target=(StockWAPt+60StockWAPt−IndexWAPt+60IndexWAPt)∗10000

### Data Fields

- **Time ID**: The timestamp of the data point, representing the last 10 minutes of the trading day.
- **Stock ID**: The identifier for each stock in the dataset.
- **Log Return**: The log returns calculated from the order book and trade data.
- **Realized Volatility**: The square root of the sum of squared log returns over the last 10 minutes of the trading day.

The dataset is structured to provide rich information for modeling, allowing for the exploration of both price movements and the underlying volatility. Feature engineering is crucial in this challenge to extract meaningful insights from this high-frequency data.

### Data Processing

To work with this data:

1. **Preprocessing**: The raw data is preprocessed to handle missing values, normalize features, and create additional derived features such as moving averages, volatility indicators, and lagged variables.
2. **Feature Engineering**: This step involves creating new features from the book and trade data to capture the dynamics of the market in the last 10 minutes. Examples include:
   - Bid-ask spread
   - Volume-weighted average price (VWAP)
   - Order imbalance
   - Rolling window statistics

