---
layout: post
title: Bikin Aplikasi Web Untuk Monitor Harga Saham Dan Forex Dengan Python Dan Streamlit
tags: data_science
cover:
excerpt: In this article we are going to create a web app with Python and Streamlit to help us easily display forex and stock price from Yahoo Finance. This post is in Bahasa Indonesia so you might want to use Google Translate :) 
---

![Hasil akhir aplikasi web dengan python dan streamlit](/images/blog/streamlit_intro/price-monitoring.png)

Objektif kita kali ini adalah bikin aplikasi web dengan Python dan Streamlit dengan fitur:
- User input untuk saham atau forex
- Pilihan periode dan interval
- Menampilkan tabel harga OHLCV
- Menampilkan candle stick chart

![not bad](https://media1.giphy.com/media/1URYTNvDM2LJoMIdxE/200.webp?cid=ecf05e47qr0tc38dhwn198vn8cnju8aegygn1ntlbsun1thz&rid=200.webp&ct=g) *ok not bad...*

### Setup Streamlit
Streamlit adalah sebuah library Python yang punya banyak komponen untuk membuat aplikasi web data science.

Tanpa Streamlit, kita akan perlu banyak persiapan untuk setup web server, bikin user input dll. 

Install Streamlit dengan mengikuti [dokumentasi ini](https://docs.streamlit.io/library/get-started/installation).

### Saatnya koding!

> Berikut adalah beberapa komponen penting di dalam kodingan aplikasi ini. Full code dan video tutorial bisa dilihat di bagian akhir artikel.

#### Import library yang diperlukan.

```py
import streamlit as st
import plotly.graph_objs as go
import plotly.express as px
import yfinance as yf
```

Kita akan pakai plotly untuk bikin candle stick chart dan yfinance untuk akses harga aset. 

[Dokumentasi Plotly](https://plotly.com/python/getting-started/)

[Dokumentasi Yfinance](https://pypi.org/project/yfinance/)

#### Menampilkan user input di sidebar

```py
ticker_symbol = st.sidebar.text_input(
    "Please enter the stock symbol", 'MSFT'
    )
```
Contoh di atas adalah untuk mendapatkan user input untuk ticker symbol. Di dalam `text_input()`, parameter pertama adalah text yang ingin ditampilkan di atas form input dan parameter kedua adalah default value.

#### Akses ticker data Yahoo Finance

{% highlight python linenos %}
def get_ticker_data(ticker_symbol, data_period, data_interval):
    ticker_data = yf.download(tickers=ticker_symbol, period=data_period, interval=data_interval)
    if len(ticker_data) == 0:
        st.write('Could not find the ticker data. Modify ticker symbol or reduce the Period value.')
    else:
        ticker_data.index = ticker_data.index.strftime("%d-%m-%Y %H:%M")
    return ticker_data
{% endhighlight %}

Library yfinance bisa kita pakai untuk mendapatkan harga aset tertentu. Di line 2, kita bisa tentukan ticker symbol, periode dan interval data sesuai input dari sidebar.

Satu hal yang penting adalah untuk menghilangkan *gap* karena market tutup saat weekend. Salah satu caranya dengan merubah format index dataframe di line 7.

#### Visualisasi data
Salah satu aspek penting dalam data science adalah visualisasi data. Di kasus ini, ada beberapa pilihan untuk visualisasi data seperti line chart atau candlestick chart. Candlestick chart akan dipakai di aplikasi ini karena lebih memudahkan untuk melihat *gain* (hijau) dan *loss* (merah) di suatu periode. Candlestick chart juga berguna untuk menentukan candlestick pattern seperti *bullish engulfing*.

```py
def plot_candle_chart(ticker_data):
    candle_fig = go.Figure()
    candle_fig.add_trace(
        go.Candlestick(
        x=ticker_data.index,
        open=ticker_data['Open'],
        close=ticker_data['Close'],
        low=ticker_data['Low'],
        high=ticker_data['High'],
        name='Market Data'
        )
    )
    candle_fig.update_layout(
        height=800,
    )
    st.write(candle_fig)
```

Function di atas akan menampilkan candle stick chart dengan data yang didapat dari yfinance di parameter (`ticker_data`)

Setelah semua kodingan selesai, aplikasi Streamlit bisa dimulai dengan `streamlit run <nama_file.py>`. Hasilnya akan seperti berikut:

![Hasil akhir aplikasi web dengan python dan streamlit](/images/blog/streamlit_intro/price-monitoring.png)

#### Penjelasan dengan video bahasa Indonesia

<iframe src="https://www.youtube.com/embed/RolOuKEjOKw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Kode lengkap bisa dilihat di [sini](https://gist.github.com/Rakademi/167d7457c56180affffc4a85708e9930) dan [sini](https://gist.github.com/Rakademi/928bacf3001ff102e946b970c6353230).

Selamat bereksperimen!