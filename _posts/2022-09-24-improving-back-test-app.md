---
layout: post
title: Improving Trading Back Test Tool
tags: data_science
cover:
excerpt: Backtest(R) Pro has better charts, important metrics e.g. Sharpe ratio and more!
---

![](/images/blog/backtestr/backtestr-pro.gif)

> Update: the app is renamed into Data Driven Trader and can be accessed [here](https://data-driven-trader.onrender.com/)

I realized there are useful metrics that I would like to add to the back testing app called Backtest(R) that I wrote in [this article]({% post_url 2021-08-19-manual-back-test-for-a-trading-strategy-is-time-consuming-so-i-created-a-web-app-to-do-it %}). As can be seen on the gif above, the app still has the original options to specify trade configuration such as indicator parameters, stop loss, and EMA filter. 'Commission' configuration is a new option. It is useful to simulate commission per trade as most brokers charge it.   

Then I found this useful library called [backtesting.py](https://kernc.github.io/backtesting.py/). It performs most of the heavy lifting. I leveraged the awesome library to create Backtest(R) Pro! 🚀

While basic back testing is clearly explained in the documentation, one has to find a way to add custom indicators such as MACD and Bollinger Bands. In addition, I wanted to combine backtesting.py with Streamlit as UI, so the challenge is to connect these two tools. Streamlit allows caching thus it is blazing fast when we test the same data and only changing the trade strategy parameters.

Back test results produced by the backtesting.py library is comprehensive. I only displayed Sharpe ratio, win rate and max drawdown but there are many more e.g. return, buy and hold return and volatility.

With this improved version, we can see more clearly how most trading strategies are not profitable 💸