# 📈 Volatility-Inverse Weighted Crypto Rebalancer (Upbit + Python + AWS)

This project is an **automated cryptocurrency portfolio rebalancing bot** that uses the **inverse volatility weighting strategy**. It runs daily using historical price data from the **Upbit API**, with all states and trades logged and versioned. Perfect for maintaining a data-driven, diversified crypto portfolio.

---

## 🧠 Strategy Overview

- **Inverse Volatility Weighting**: Assets with lower 20-day historical volatility receive higher portfolio weights.
- **Daily Rebalancing**: At each run, the bot:
  - Fetches the latest prices & 20-day rolling standard deviation
  - Computes new target weights
  - Calculates the required buy/sell actions
  - Logs the changes and updates the internal state

---

## ⚙️ Tech Stack

- **Python 3.9+**
- **Upbit API** (`pyupbit`)
- **AWS EC2 / cron (or Lambda)** for automation
- **Git**: Tracks rebalancing logs and portfolio state over time
- **.env** secrets management using `python-dotenv`

---

## 📁 Directory Structure

```
trading/
├── state.json             # Portfolio positions and cash
├── rebalancing_log.csv    # Historical trades and rebalancing actions
├── rebalancer.py          # Main logic script
├── .env                   # API keys
```

---

## 🔐 .env File (Never Commit This)

```
UPBIT_ACCESS_KEY=your_upbit_access_key
UPBIT_SECRET_KEY=your_upbit_secret_key
```

---

## 🚀 How to Run

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Add your `.env` file with Upbit API keys.

3. Run the script:
   ```bash
   python rebalancer.py
   ```

4. (Optional) Set up a cron job or AWS Lambda function for daily execution.

---

## 📊 Sample Assets

Currently supports:
- `KRW-BTC`
- `KRW-XRP`
- `KRW-MANA`

You can modify the `TICKERS` list to include other KRW pairs.

---

## 📝 Features

- ✅ Volatility-based weight allocation
- ✅ Automatic portfolio rebalancing
- ✅ Logging with timestamped records
- ✅ Git-integrated history tracking (optional)
- ✅ Timezone-aware (Asia/Seoul)

---

## 🧾 Example Log Output

```
[2025-05-03 09:00:01] Rebalance Start — PV: 10,000,000 KRW  Cash: 500,000 KRW
  KRW-BTC: BUY 0.002350 units @ 42,540,000 KRW
  KRW-XRP: SELL 152.240000 units @ 698 KRW
  KRW-MANA: HOLD 0.000000 units @ 910 KRW
[2025-05-03 09:00:03] Rebalance Done — New Cash: 488,200 KRW
```

---

## 💡 Future Improvements

- API order placement (real trading)
- Portfolio performance dashboard
- Email/Telegram notifications
- Integration with other exchanges (e.g., Binance)

---

## ⚠️ Disclaimer

This project is **for educational and personal use only**. Investing and trading cryptocurrencies involves substantial risk. Always do your own research (DYOR) and consult with a financial advisor before deploying trading bots with real capital.


