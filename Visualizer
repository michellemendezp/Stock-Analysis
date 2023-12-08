import yfinance as yf

# Fetch historical data for Anterix
ticker = 'ATEX'
stock_data = yf.download(ticker, start="2020-01-01", end="2023-11-16")
import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt

# Fetch historical data for Anterix
ticker = 'ATEX'
stock_data = yf.download(ticker, start="2020-01-01", end="2023-11-16")

# Basic Data Cleaning
stock_data.fillna(method='ffill', inplace=True)

# Adding a Simple Moving Average (SMA) for 7 days
stock_data['7_day_SMA'] = stock_data['Close'].rolling(window=7).mean()

# Basic Exploratory Data Analysis: Plotting the Closing Price and SMA
plt.figure(figsize=(12,6))
plt.title(f'Closing Price and 7-day SMA of {ticker}')
plt.plot(stock_data['Close'], label='Close Price', color='blue')
plt.plot(stock_data['7_day_SMA'], label='7-day SMA', color='orange')
plt.xlabel('Date')
plt.ylabel('Price (USD)')
plt.legend()
plt.show()

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
import time

# URL for Anterix (ATEX) on Yahoo Finance
url = 'https://finance.yahoo.com/quote/ATEX?p=ATEX&.tsrc=fin-srch'

# Set up the Selenium WebDriver
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))

# Open the web page
driver.get(url)

# Wait for the page to load
time.sleep(5)

# Scrape the current stock price
try:
    price_element = driver.find_element(By.CSS_SELECTOR, '[data-field="regularMarketPrice"]')
    current_price = price_element.text
    print(f'Current Price of ATEX: {current_price}')
except Exception as e:
    print("Could not find the price element.", e)

# Scrape recent news headlines
print('\nRecent News Headlines for ATEX:')
try:
    news_elements = driver.find_elements(By.CSS_SELECTOR, 'h3[class="Mb(5px)"]')
    for element in news_elements:
        print(element.text)
except Exception as e:
    print("Could not find news elements.", e)

# Close the WebDriver
driver.quit()
