# Optiver Trading at the Close - Kaggle Challenge

Welcome to my repository for the [Optiver - Trading at the Close](https://www.kaggle.com/competitions/optiver-trading-at-the-close) Kaggle challenge. This repository contains my code, experiments, and documentation for the competition.

## Overview

The challenge is to predict the price movements in the last 10 minutes of the trading day, which is crucial for many trading strategies. The objective is to develop models that can accurately predict these movements to maximize returns.

## Dataset

The dataset provided by the competition includes high-frequency trading data from the last 10 minutes of trading across multiple stocks. Key components of the dataset include:

- **Book Data (`book_*.parquet`)**: Contains order book data for each stock at different time intervals. This data includes information such as bid prices, ask prices, bid sizes, and ask sizes.
- **Trade Data (`trade_*.parquet`)**: Contains trade data, including the executed trade prices, sizes, and the time of trades.
- **Target (`train.csv`)**: The target file includes the realized volatility of the stock prices in the last 10 minutes of the trading day, which is the primary metric to predict.

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

