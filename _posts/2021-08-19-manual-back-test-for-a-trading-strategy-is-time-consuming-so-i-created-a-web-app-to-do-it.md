---
layout: post
title: Manual back test for a trading strategy is time consuming, so I created a web app to do it.
tags: data_science
cover: 
excerpt: Note - this post is not a financial advice or a detailed guide on how to code in Python.
---

![](/images/blog/streamlit_intro/1.gif)

*Back testing web app that I built with Streamlit*

Recently I discovered about Streamlit Python library. It makes building a data science Python app much more convenient!

You can watch an excellent video on how to create a web app using Streamlit on the following video. FreeCodeCamp has a wide variety of useful videos, for free! So support them by subscribing to the channel!

<iframe src="https://www.youtube.com/embed/JwSS70SZdyM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## The problem
I wanted to perform back testing to a trading strategy that I have. However, testing manually on a long period of historical data is too tedious and time consuming.

I used to stare at TradingView’s charts and identify buying/selling points manually for each time frame. For each tick, I will spot a buy or sell signal based on my trading strategy. And for each position, I need to adjust the stop loss and take profit manually to achieve my target risk to reward ratio (RR).

It was extremely tedious.

## There has to be a better way
After finding out about Streamlit, it occurred to me that I need to create a back testing web app to automate the process. This is especially useful when I want to test over a long period of time and try multiple values for RR, stop loss distance, etc.

Streamlit makes it easy to create web elements without tinkering with html and css. Using the library is just one line import away. We can just type the following to get something similar with h1 in html (similar to Markdown):

```py
import streamlit as st
st.write("""
# Simple MACD Backtesting App
---
"""
)
```
It is also trivial to output python variables with its ‘magic command’. So you just need to type the variable name and nothing else, it will appear on the web app (similar to Jupyter notebook).

You can learn in more details about Streamlit on the YouTube video pasted above.

## The trading strategy
Here is the MACD trading strategy that I want to test:

- Only go long when the price is above 200 exponential moving average (EMA) and there is a bullish MACD crossing.
- Only go short when the price is below 200 EMA and there is a bearish MACD crossing.
In this case, I use 200 EMA to see the long term trend to filter for valid MACD crossing. I want to trade in the direction of long term trend.

## Building the web app
I need to calculate MACD, 200 EMA and Average True Range (ATR) to determine stop loss and finally use those data to simulate my trading strategy.

Streamlit makes it convenient to get input from users with its handy sidebar.

```py
ticker_symbol = st.sidebar.text_input(
"Please enter the currency pair or stock symbol", 'MSFT'
)
data_period = st.sidebar.text_input("Period","10d")
data_interval = st.sidebar.radio('Interval',['15m','30m','1h','1d','5d'])
atr_mult_str = st.sidebar.text_input(
"Stop Loss ATR Multiplier", 2
)
RR_str = st.sidebar.text_input(
"Risk/Reward Ratio", 1.5
)
```

Using the web app, I can adjust the parameters easily, as shown below. It enables me to test on much longer period and try different combination of parameters to get the desired results without having to rerun the python script manually.

![](/images/blog/streamlit_intro/2.gif)

From the testing, I figured out long term expectation for the strategy’s return. Even though results from the past may not be the same in the future, at least it is better than blindly using a trading strategy. I can trade without fear when I know the strategy is profitable in the long run. Taking a loss is expected. The most important skill is to have the discipline to stick to the strategy.

From what I learned so far, trading is more about psychology and money management. But that is another topic entirely :)

> Streamlit is extremely useful in building prototype quickly. 

It provides user-friendly UI component that can change its state when users update its value. We can focus on building the logic instead of spending time adjusting how much margin is needed for a chart.

However, if we need more customization in production environment, Streamlit might not be suitable in many cases.

GLHF!