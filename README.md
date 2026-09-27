# Stock Price Prediction with LSTM

A deep learning time-series project that uses **Long Short-Term Memory (LSTM)** networks to predict stock prices for **Facebook (FB)** and **IBM**.

## Problem

Stock prices are sequential time-series data. This project uses historical observations to predict the next stock price using an **overlapping sliding window**.

- Stocks: FB and IBM
- Window size: 5
- Window shift: 1 step
- Prediction horizon: 1 step ahead

## Models

### Baseline LSTM
- LSTM: 50 units
- Activation: ReLU
- Dense output: 1
- Loss: MSE
- Optimizer: Adam

### Improved LSTM
- LSTM: 128 units, `return_sequences=True`
- Dropout: 0.2
- LSTM: 64 units
- Dense: 32, ReLU
- Dense output: 1
- ReduceLROnPlateau scheduler

The improved architecture was designed to capture more complex temporal patterns while controlling overfitting.

## Results

### Facebook (FB)

| Model | RMSE | MAE | MAPE |
|---|---:|---:|---:|
| Baseline LSTM | **5.65** | **3.92** | **2.11%** |
| Improved LSTM | 6.43 | 5.16 | 2.76% |

### IBM

| Model | RMSE | MAE | MAPE |
|---|---:|---:|---:|
| Baseline LSTM | **2.69** | **1.73** | **1.34%** |
| Improved LSTM | 4.87 | 3.36 | 2.58% |

In this experiment, the baseline LSTM achieved lower test error for both stocks.

## Key Takeaway

A deeper LSTM does not automatically produce better results. With a short five-day input window, the increased model capacity of the improved architecture did not translate into better test performance.
