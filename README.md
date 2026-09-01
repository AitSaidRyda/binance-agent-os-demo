# Binance Market Sentiment AI Agent
import requests
import json

def fetch_binance_market_data():
    # Fetching 24hr ticker price change statistics from Binance API
    url = "https://api.binance.com/api/v3/ticker/24hr?symbol=BTCUSDT"
    response = requests.get(url)
    data = response.json()
    
    price = float(data.get("lastPrice", 0))
    price_change = float(data.get("priceChangePercent", 0))
    
    print(f"--- Binance AI Agent Report ---")
    print(f"Token: BTC/USDT")
    print(f"Current Price: ${price:.2f}")
    print(f"24h Change: {price_change:.2f}%")
    
    if price_change > 0:
        print("Market Sentiment: Bullish 🚀")
    else:
        print("Market Sentiment: Bearish 📉")

if __name__ == "__main__":
    fetch_binance_market_data()
