---
layout: post
title: Deploying Trading Strategy Back Test Tool To Heroku
tags: data_science
cover:
excerpt: After building the back test tool, it is time to share it with others. The tool is free to use and hopefully can show that most trading strategies are not profitable.
---

![](/images/blog/streamlit_intro/deploy-heroku.png)

> You can access the tool [here](https://backtestr.herokuapp.com/). The initial loading time is quite long, but hey, it is free hosting Update: Heroku recently removed free tier hosting so the app cannot be accessed anymore :( Update 2: luckily Render provides free hosting. The app (renamed as Data Driven Trader) can be accessed [here](https://data-driven-trader.onrender.com/) :)

In my [previous article]({% post_url 2021-08-19-manual-back-test-for-a-trading-strategy-is-time-consuming-so-i-created-a-web-app-to-do-it %}), I created a back testing tool with Python and Streamlit.

It will be good to share the tool online hence I need a hosting platform. Heroku came to my mind as it provides free and easy deployment for Streamlit application.

However, the process was not without some hiccups.

The main difficulty occurred due to [TA-Lib](https://github.com/mrjbq7/ta-lib) error when deploying to Heroku. 

After several copy and paste effort from StackOverflow, the issue was resolved, thanks to [this post](https://stackoverflow.com/questions/43453953/how-to-install-python-library-in-heroku)!

Now the tool is available online and you can see that most of the trading strategies are not profitable 💸


You can change any parameters easily and there is a simple statistical summary of the trading strategy performance. 

Although it is still a very simple statistic without advanced metrics such as Sharpe ratio, we can still see clearly how most strategy fails to deliver significant profit in the long run.

It is cool to know how data science can save us potentially thousand of dollars! 🚀