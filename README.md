# Risk–Return Analysis of EABL (Nairobi Securities Exchange)

This repository contains a beginner-friendly time series and forecasting project that analyzes the risk–return relationship of East African Breweries Ltd (EABL) using daily stock price data from the Nairobi Securities Exchange (NSE).

It demonstrates:

* How to compute log returns

* How to measure volatility (risk)

* Why OLS can fail for financial time series

* How Maximum Likelihood Estimation (MLE) and GARCH models fix these problems

## Project Motivation

Financial return series often violate the assumptions of Ordinary Least Squares (OLS), such as:

* Normality of errors

* Constant variance (homoskedasticity)

* No autocorrelation

This project shows why OLS is not appropriate for modeling daily stock returns and demonstrates how MLE with a GARCH(1,1) model provides a better framework for risk modeling.

## Data Description

* Security: East African Breweries Ltd (EABL)

* Exchange: Nairobi Securities Exchange (NSE)

* Frequency: Daily

* Observations: 200+ trading days

* Source: https://stockanalysis.com/quote/nase/EABL/

## Variables Used

* Adj. Close – used to compute returns

* Date – trading date

* Volume, Open, High, Low – included for completeness

## Methodology Overview
### Log Returns
Daily log returns are computed as:

r<sub>t</sub> = ln(P<sub>t</sub> / P<sub>t−1</sub>)

Log returns are preferred because they are time-additive and standard in financial analysis.

### Volatility (Risk)
Risk is measured using a 20-day rolling standard deviation of log returns:

σ<sub>t</sub> = √(1/19 · ∑ (r<sub>t−i</sub> − r̄)²)

This captures short-term volatility and market uncertainty.

### OLS Risk–Return Model
An initial risk–return model is estimated using OLS:

r<sub>t</sub> = α + βσ<sub>t</sub> + ε<sub>t</sub>

### OLS Diagnostic Tests

To validate OLS assumptions, the following tests are conducted:

* Jarque–Bera Test → normality of residuals

* Breusch–Pagan Test → homoskedasticity

* Ljung–Box Test → autocorrelation

📌 Results show strong violations of OLS assumptions.

### MLE with GARCH(1,1)
Because OLS assumptions fail, a GARCH(1,1) model is estimated using Maximum Likelihood Estimation (MLE):

r<sub>t</sub> = α + βσ<sub>t</sub> + ε<sub>t</sub>  
h<sub>t</sub> = ω + α<sub>1</sub>ε<sub>t−1</sub><sup>2</sup> + β<sub>1</sub>h<sub>t−1</sub>

This model captures volatility clustering, a key feature of financial returns.

## Key Findings

* OLS is not valid for daily EABL returns due to:

  * Non-normal residuals

  * Heteroskedasticity

  * Autocorrelation

* GARCH(1,1) successfully models time-varying volatility

* The daily risk–return relationship is weak, which is common in high-frequency data

* Volatility shows strong persistence (volatility clustering)

## Tools & Libraries
* Python3
* pandas
* numpy
* statsmodels
* arch
* scipy
