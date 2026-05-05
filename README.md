# Monte Carlo Simulation of VTI Portfolio Risk

##  Project Overview

This project analyzes the potential future performance of an investment in the Vanguard Total Stock Market ETF (VTI) using Monte Carlo simulation.

Instead of predicting a single outcome, the model generates thousands of possible scenarios based on historical return behavior, allowing us to estimate both expected returns and risk.

## Objective

To simulate how a portfolio might grow over time and quantify uncertainty using key financial risk metrics such as:

* Expected portfolio value
* Volatility (risk)
* Probability of loss
* Value at Risk (VaR)



##  Data Source

Historical price data is retrieved using the `yfinance` library for the VTI ETF.

* Data used: Adjusted closing prices
* Frequency: Daily
* Default range: Last 5 years



##  Methodology

### 1. Return Calculation

Daily returns are computed using percentage change:

r_t = (P_t - P_{t-1}) / P_{t-1}

From these returns:

* Mean (μ) represents expected return
* Standard deviation (σ) represents volatility


### 2. Monte Carlo Simulation

The portfolio evolves according to:

V(t+1) = V(t) * (1 + r)

Where each daily return r is randomly sampled from a normal distribution defined by the historical μ and σ.

Thousands of simulation paths are generated to model possible future outcomes.


### 3. Risk Metrics

* **Expected Value**: Average final portfolio value across all simulations
* **Volatility**: Standard deviation of outcomes
* **Probability of Loss**: Percentage of simulations where final value < initial investment
* **Value at Risk (VaR 5%)**: Worst expected outcome in the bottom 5% of scenarios


## Visualizations

The project generates:

* Histogram of final portfolio values
* Simulated portfolio paths over time
* Historical price chart of VTI



##  How to Run

1. Install dependencies:
   pip install numpy pandas matplotlib yfinance

2. Run the script:
   python main.py

3. Modify parameters in the script:

* Initial investment
* Time horizon
* Number of simulations



##  Assumptions

* Returns follow a normal distribution
* Historical data is representative of future behavior
* Market conditions remain relatively stable



##  Limitations

* Real market returns are not perfectly normally distributed
* Extreme events (crashes) may be underestimated
* Does not account for transaction costs, taxes, or external factors



##  Future Improvements

* Multi-asset portfolio simulation (e.g., stocks + bonds)
* Use log returns instead of simple returns
* Incorporate real-time data updates
* Build an interactive dashboard (e.g., Streamlit)


##  Key Takeaway

This project demonstrates how probabilistic modeling can be used to understand financial risk and uncertainty, rather than relying on single-point predictions.


