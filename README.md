# Algorithmic trading Project

Litvinova Olga

m: litvinova2404@gmail.com

## Overview

The goal of the project is to practice:
* data collection and management,
* financial data analysis,
* risk management and reporting, 
* robust software design.

To achieve my goal, I aim to implement 3 algorithmic trading strategies, conduct back-testing for each of them and live paper-trading for 2
### Back-testing (See BackTest.ipunb)
I conducted the back-testing using historical data to assess its performance. The model is evaluated based on the Bitcoin Perpetual market, utilising minute-level data retrieved and trading executed through the Deribit Test API (deribit.com). It covers the time period from July 4th, 2023, at 7:00 AM to July 7th, 2023, at 7:00 PM. For the code please see BackTest.ipynb 
1. Swing Trading Strategy

   The code defines a class named MyBacktest, which includes a function strategy. It firstly set a logic of my main strategy based on historical price data from a CSV file named "ohlc_data.csv." That I downloaded in data.py The strategy involves calculating various technical indicators like stochastic oscillators (K and D), exponential moving averages (EMAs), and average true range (ATR). The script identifies potential buying signals based on specific conditions, including bullish crossovers, moving average relationships, and volume confirmation. The backtest simulates trades and calculates the returns based on the identified signals and defined take-profit (tp) and stop-loss (sl) levels. The trade results, including buy and sell dates, prices, and reasons for selling, are stored in a pandas DataFrame and printed to the console. Additionally, the script generates a three-panel plot using matplotlib to visualize the price data, EMAs, ATR, and stochastic indicators.
2. Simple Moving Average crossover 

   The next code sets logic of strategy #2 and run backtesting, using my historical data The code implements a Simple Moving Average (SMA) crossover strategy by computing short-term and long-term moving averages. The strategy identifies 'buy' signals when the short-term moving average crosses above the long-term moving average, and 'sell' signals when it crosses below. The code visualizes the closing price, short-term SMA, and long-term SMA with 'buy' and 'sell' signals on two subplots using matplotlib.
3. High/Low rolling Strategy
  
   Here the last alternative strategy is backtested: It calculates the rolling maximum and minimum values over the last 10 minutes for the 'high' and 'low' columns, respectively. The average between the rolling maximum and minimum is computed and stored in the 'mid' column. The code defines 'buy' and 'sell' conditions based on specific criteria related to the closing price, rolling high, and mid values. Buy and sell signals are identified, and the corresponding dates and prices are stored in separate lists. The OHLC data along with buy and sell signals are plotted using matplotlib.
The project uses Bitcoin Perpetual market, utilising minute-level data retrieved and trading executed through the Deribit Test API. 

 ### Live-testing (See livetesting.ipynb)
I run live trading for 6 hours. For that I firstly download all needed me data - historical and current price separately:
The code fetches the current market price for the "BTC-PERPETUAL" instrument using the get_market() function. Historical minute data for the "BTC-PERPETUAL" instrument is obtained using the get_minute_data() function. Then after downloading data I am ready to define all needed variables:

Technical indicators such as Stochastic K and D, exponential moving averages (EMA), and the average true range (ATR) are calculated using the define_variable() function. Buy signals are identified when specific conditions are met, including volume confirmation, Stochastic K-D crossover, and the order of EMAs. Sell signals are not explicitly defined in the provided code. It appears that sell trades are executed based on predefined take-profit (TP) and stop-loss (SL) levels in relation to the current market price.

Buy orders are executed using the buy() function, and the corresponding trade details are stored in buydates and buyprices lists. The code also defines a sell() function for executing sell orders, but the specific conditions for selling are not explicitly provided in the code. Take-profit (TP) and stop-loss (SL) levels are calculated based on the ATR and current market price. When the market price reaches TP or SL, the sell() function is called to execute the sell order.

The code records the trade data into a CSV file named "data_trading.csv" using the pandas DataFrame df.

