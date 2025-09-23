# Quantitative Financial Analysis Repository

This repository contains a collection of Python notebooks focused on quantitative analysis, algorithmic trading strategies, and financial data modeling. Each project leverages modern data science libraries to explore relationships between market data, sentiment, and price movements.

---

## 📈 Projects

### 1. Sentiment-Based Trading Strategy for Tesla (TSLA)

**File:** `sentiment_trading_strategy.ipynb`

This project investigates the correlation between the public sentiment expressed in Elon Musk's tweets and the daily stock returns of Tesla (TSLA).

#### Methodology:
1.  **Data Collection:**
    * **Stock Data:** Daily historical price data for TSLA is downloaded for 2023 using the `yfinance` library.
    * **Sentiment Data:** A CSV file containing Elon Musk's tweets is loaded.
2.  **Sentiment Analysis:**
    * Each tweet's text is analyzed using `TextBlob` to calculate a **sentiment polarity score** (ranging from -1.0 for negative to +1.0 for positive).
    * Tweets are grouped by day, and an average daily sentiment score is calculated.
3.  **Data Merging & Analysis:**
    * The daily stock returns are merged with the calculated daily sentiment scores.
    * The **Pearson correlation coefficient** is computed to measure the linear relationship between sentiment and returns.
4.  **Visualization:**
    * **Time Series Plot:** Compares daily returns against daily sentiment over time.
    * **Scatter Plot:** Visualizes the direct relationship between sentiment scores and stock returns.
    * **7-Day Rolling Average:** Smooths the data to identify underlying trends.
    * **Correlation Heatmap:** Shows the correlation between returns, sentiment, closing price, and volume.
    * **Bar Chart:** Compares the average daily returns on days with overall positive sentiment versus days with negative sentiment.

#### Key Findings:
The analysis reveals a **weak positive correlation (0.1383)** between the daily average sentiment of Elon Musk's tweets and TSLA's daily returns for the period studied. While not strong enough to be a standalone trading signal, it suggests that overwhelmingly positive sentiment may have a slight positive influence on price action.


---

### 2. Time-Series Forecasting of TSLA Daily Returns

**File:** `TSLA_daily_returns_1000shares.ipynb`

This project implements a machine learning model to predict the daily return of Tesla (TSLA) stock using a wide range of market indicators as features. The model is a **Random Forest Regressor**, chosen for its robustness in handling complex, non-linear relationships in financial data.

#### Methodology:
1.  **Feature Engineering:**
    * **Market Data:** Daily closing prices for over 1500 NASDAQ stocks and key market indices (`^GSPC`, `^IXIC`, `^VIX`, `^TNX`), commodities (`CL=F`), and cryptocurrencies (`BTC-USD`) are downloaded.
    * **Technical Indicators:** Custom-calculated indicators for TSLA are created:
        * 50-Day Simple Moving Average (SMA)
        * Bollinger Bands (Upper and Lower)
        * Relative Strength Index (RSI)
    * **Lagged Features:** All market returns and technical indicators are lagged by one day to ensure the model only uses past information to predict future returns.
2.  **Model Training:**
    * A **Random Forest Regressor** from `scikit-learn` is trained on 5 years of historical data.
    * The target variable is the next-day's return for TSLA.
    * The features are the lagged daily returns of all assets and the lagged technical indicators.
3.  **Single-Day Backtest:**
    * The model is trained on data up to September 17, 2025.
    * It then uses the data from September 18, 2025, to predict the return for **September 19, 2025**.
    * The prediction is compared against the actual, known return for that day to evaluate performance.

#### Backtest Result (for 2025-09-19):
* **Predicted Return:** `+1.3174%`
* **Actual Return:** `+2.2118%`

This result demonstrates the model's ability to correctly predict the direction of the price movement for the tested day, although the magnitude was underestimated.


---

## 🛠️ How to Use

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/diejo57Quant-Analysis.git](https://github.com/diejo57/Quant-Analysis.git)
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd Quant-Analysis
    ```
3.  **Open the notebooks:**
    * Open `sentiment_trading_strategy.ipynb` or `TSLA_daily_returns_1000shares.ipynb` in a Jupyter environment like Jupyter Lab or Google Colab.
4.  **Run the cells:**
    * Execute the cells in order to download the data, perform the analysis, and generate the visualizations.
