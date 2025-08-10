# DON'T PREDICT STOCK RETURN USING LSTM

## Overview

This project demonstrates the limitations of using LSTM (Long Short-Term Memory) neural networks for predicting stock prices and returns. Despite the popularity of deep learning in financial forecasting, this notebook shows—through practical experiments—why such models often fail to generalize or provide meaningful predictions in real-world stock markets.

---

## Why This Project?

- Many online resources claim LSTM models can predict stock prices.
- Few, if any, authors actually use these models with their own money in real markets.
- If LSTM models could reliably predict prices, everyone would be rich.
- This project aims to correct the misconception that deep learning can "magically" forecast stock prices using only historical data.

---

## Data

- **Source:** Starbucks (SBUX) daily stock prices from 2013 to 2018.
- **Features:** `date`, `open`, `high`, `low`, `close`, `volume`
- **Target:** Stock price or return

---

## Experiments

### MODEL 1: Predicting Stock Price Directly

- **Approach:** Use LSTM to predict the next day's closing price from previous prices.
- **Result:** Appears to work in "one-step" forecasting (using true previous values), but fails in realistic "multistep" forecasting where the model must use its own predictions as input.

### MODEL 2: Predicting Stock Return

- **Approach:** Predict the next day's return (percentage change) using LSTM.
- **Result:** Model fails to generalize, with validation loss increasing and predictions no better than random.

### MODEL 3: Classification (Up/Down Prediction)

- **Approach:** Use all five features to predict whether the next day's return will be positive (up) or negative (down).
- **Result:** Model accuracy hovers around 50%, equivalent to random guessing.

---

## Key Insights

- **One-step forecasting** is misleading because it uses true historical values, which are not available in real trading.
- **Multistep forecasting** is more realistic and reveals the model's inability to generalize.
- **Stock returns are noisy and close to random**, making them very hard to predict with past prices alone.
- **Classification models** (predicting up/down) also fail, showing no edge over random guessing.
- **Overfitting** is common: training loss drops, but validation loss rises.
- **Real-world events, news, and sentiment** drive stock prices—these are not captured by historical price data alone.

---

## Visualizations

- **Loss and accuracy curves** for each model
- **Predicted vs. actual values** for both regression and classification tasks

---

## Conclusion

- LSTM and similar deep learning models cannot reliably predict stock prices or returns using only historical price data.
- Be skeptical of any resource that claims otherwise without robust, out-of-sample, and real-world validation.
- Predicting stock direction or value is not a "simple" task—financial markets are complex, efficient, and influenced by countless external factors.

---

## Requirements

- Python 3.x
- TensorFlow / Keras
- NumPy
- Pandas
- Matplotlib
- Seaborn
- scikit-learn

---

## How to Run

1. Place the Starbucks stock CSV (`sbux.csv`) in the project directory.
2. Open and run the notebook `stock_return_prediction.ipynb` in Jupyter or VS Code.
3. Review the outputs, plots, and markdown explanations.

---

## Disclaimer

This project is for educational purposes only and does **not** constitute financial advice or  trading recomandation.
