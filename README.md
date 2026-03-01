import pandas as pd
import numpy as np
import ta
import cv2
import pytesseract
from binance.client import Client

class DataEngine:
    def __init__(self, api_key=None, api_secret=None):
        self.client = Client(api_key, api_secret)

    def get_crypto_data(self, symbol="BTCUSDT", interval="1h", limit=500):
        klines = self.client.get_klines(symbol=symbol, interval=interval, limit=limit)
        df = pd.DataFrame(klines, columns=[
            'time','open','high','low','close','volume',
            '_','_','_','_','_','_'
        ])
        df['close'] = df['close'].astype(float)
        df['high'] = df['high'].astype(float)
        df['low'] = df['low'].astype(float)
        return dfclass MarketStructure:
    def __init__(self, df):
        self.df = df

    def add_indicators(self):
        self.df['EMA50'] = ta.trend.ema_indicator(self.df['close'], window=50)
        self.df['EMA200'] = ta.trend.ema_indicator(self.df['close'], window=200)
        self.df['RSI'] = ta.momentum.rsi(self.df['close'], window=14)
        self.df['ATR'] = ta.volatility.average_true_range(
            self.df['high'], self.df['low'], self.df['close'], window=14)

    def trend_direction(self):
        if self.df['EMA50'].iloc[-1] > self.df['EMA200'].iloc[-1]:
            return "Bullish"
        elif self.df['EMA50'].iloc[-1] < self.df['EMA200'].iloc[-1]:
            return "Bearish"
        else:
            return "Sideways"
            class StrategyEngine:
    def __init__(self, df):
        self.df = df

    def generate_signal(self):
        last = self.df.iloc[-1]

        if (
            last['EMA50'] > last['EMA200'] and
            last['RSI'] > 50
        ):
            return "BUY"

        elif (
            last['EMA50'] < last['EMA200'] and
            last['RSI'] < 50
        ):
            return "SELL"

        else:
            return "WAIT"
            class RiskEngine:
    def __init__(self, df, account_size=100, risk_percent=0.01):
        self.df = df
        self.account_size = account_size
        self.risk_percent = risk_percent

    def calculate_levels(self, signal):
        last = self.df.iloc[-1]
        atr = last['ATR']
        entry = last['close']

        if signal == "BUY":
            stop_loss = entry - (atr * 1.5)
            take_profit = entry + (atr * 3)
        elif signal == "SELL":
            stop_loss = entry + (atr * 1.5)
            take_profit = entry - (atr * 3)
        else:
            return None

        risk_amount = self.account_size * self.risk_percent
        position_size = risk_amount / abs(entry - stop_loss)

        return {
            "Entry": entry,
            "StopLoss": stop_loss,
            "TakeProfit": take_profit,
            "PositionSize": position_size
        }
        class ImageAnalyzer:
    def __init__(self):
        pass

    def analyze_chart(self, image_path):
        img = cv2.imread(image_path)
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

        # Basic edge detection
        edges = cv2.Canny(gray, 50, 150)

        return {
            "Message": "Chart processed. Structure detection model needed for advanced mapping."
        }
