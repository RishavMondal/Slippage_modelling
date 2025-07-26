# Slippage Modeling for Stock Order Books

This project demonstrates how to simulate and model **temporary market impact** (slippage) using synthetic or MBP-10 (Market By Price) order book data.

---

## **Overview**
When executing large market orders, the average execution price often deviates from the mid-price due to **market depth**. This deviation is called **slippage**. 

In this notebook:
1. We simulate order book data for 3 tickers.
2. We calculate slippage \( g_t(x) \) for various order sizes \( x \).
3. We fit a **quadratic model**:
   \[
   g_t(x) = c + a x + b x^2
   \]
   where:
   - **c** = baseline slippage (y-intercept),
   - **a** = linear component of slippage,
   - **b** = quadratic component representing accelerated costs.

---

## **Features**
- **Synthetic Order Book Generation:**  
  Creates randomized bid/ask prices and quantities for each ticker.
- **Slippage Simulation:**  
  Computes slippage by consuming multiple levels of the order book.
- **Quadratic Fitting:**  
  Uses least squares regression to fit \( g_t(x) \) vs. \( x \).
- **Visualization:**  
  Plots observed slippage points and the fitted curve.

---

## **Key Functions**
- `generate_order_book(ticker)` – Creates synthetic order book data for a given ticker.
- `calculate_slippage(order_book, x)` – Calculates slippage for an order of size `x`.
- `simulate_all_tickers(order_books, max_x=30000, step=500)` – Runs slippage simulation for all tickers.
- `fit_quadratic(x, g)` – Fits the quadratic model \( g_t(x) = c + a x + b x^2 \).
- `plot_slippage_fit(x_values, g_values, c, a, b, ticker_name)` – Plots slippage data and fitted curve.

---

## **Installation**
1. Clone the repository or copy the notebook and README files.
2. Install the required Python libraries:
   ```bash
   pip install numpy pandas matplotlib
