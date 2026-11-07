# Stock Strategy Backtesting & Risk Analysis

Backtest of a 20/50-day moving average crossover strategy on 5 Nifty 50 stocks
(RELIANCE, TCS, HDFCBANK, INFY, ITC), compared against buy-and-hold on return,
max drawdown and Sharpe ratio.

## Data & Method
- 5 years of daily prices from Yahoo Finance (yfinance)
- Signal: hold when 20-day average > 50-day average, else stay in cash
- Signal applied with a 1-day lag (avoids look-ahead bias)
- 0.1% transaction cost per buy/sell; long-only; no slippage or tax
- Sharpe ratio computed without a risk-free rate

## Results (after 0.1% cost)
| Stock | Buy & Hold | Strategy | Max DD (B&H -> Strat) |
|---|---|---|---|
| RELIANCE | 14.8% | -1.7% | -27.2% -> -23.2% |
| TCS | -27.3% | -33.7% | -53.4% -> -33.4% |
| HDFCBANK | 9.0% | -32.7% | -31.7% -> -37.9% |
| INFY | -28.7% | -22.0% | -48.2% -> -38.2% |
| ITC | 61.5% | 81.3% | -45.0% -> -16.9% |

## Findings
- Strategy beat buy-and-hold in only 2 of 5 stocks after costs
- It reduced max drawdown in 4 of 5 stocks, but gave up return in trending periods
- Win rate alone is misleading: RELIANCE won 31% of trades yet had positive
  expected value; TCS won 37.5% yet had negative expected value
- TCS and INFY are highly correlated (0.74); other pairs 0.18-0.36
- ITC's outperformance came mostly from staying in cash during the 2025-26 fall

## Limitations
- One parameter setting (20/50), 5 stocks, one 5-year window
- ITC result rests on only 7 trades; not statistically meaningful
- Past performance is not a prediction. This is not investment advice.
