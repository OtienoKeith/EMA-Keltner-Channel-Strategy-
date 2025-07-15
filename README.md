# 📈 EMA + Keltner Channel Strategy (Fixed Stop Loss at Entry)

This Pine Script strategy combines a **100-period EMA** and a **Keltner Channel** to trade with trend confirmation and volatility-based exits. The **stop loss is locked at entry**, using the Keltner Band value at the moment of trade execution, ensuring consistent and realistic backtesting.

---

## ✅ Strategy Overview

- **Trend Filter**: EMA 100
- **Volatility Bands**: Keltner Channel (EMA-based, ATR-derived width)
- **Trade Type**: Reversal Pullback with Trend Confirmation
- **Stop Loss**: Keltner Band value at entry candle
- **Take Profit**: 0.66 × stop loss distance
- **Capital & Risk**: Custom initial capital and % risk per trade

---

## 🔁 Entry Conditions

### 🟢 Long Entry
- Price is **above** the 100 EMA
- Price is **above** the Keltner Channel middle line
- Entry is at the **next candle open**

### 🔴 Short Entry
- Price is **below** the 100 EMA
- Price is **below** the Keltner Channel middle line
- Entry is at the **next candle open**

---

## 📉 Stop Loss & 📈 Take Profit

### Stop Loss
- **Long Trade**: Set at the **lower Keltner Band** at the entry candle
- **Short Trade**: Set at the **upper Keltner Band** at the entry candle
- The stop loss is **frozen at entry** and does not update afterward

### Take Profit
- TP = Entry Price ± (0.66 × Stop Loss Distance)
- Ensures a **reward-to-risk ratio of 0.66**

---

## 💰 Position Sizing

- Custom **Initial Capital** (default: $10,000)
- **Risk Per Trade** (default: 2%)
- Position size = `risk capital ÷ stop loss distance`
- Ensures risk is dynamically managed regardless of volatility

---

## 🔒 Trade Management

- **No pyramiding** (only one trade at a time)
- **Trade lock-in**: New trade allowed only after the previous one closes
- Clean and strict execution logic for realistic backtesting

---

## 📊 Recommended Settings

| Setting        | Default Value |
|----------------|---------------|
| EMA Length     | 100           |
| Keltner Length | 20            |
| Keltner Mult   | 1.5           |
| TP Multiplier  | 0.66          |
| Risk %         | 2%            |
| Capital        | $10,000       |

---

## 📎 Notes

- This strategy is ideal for trending markets (1H–4H or Daily).
- Works best on liquid FX pairs like EURUSD or GBPUSD.
- You can further improve results by:
  - Adding a time/session filter (e.g. London open)
  - Optimizing Keltner and EMA parameters
  - Adding a higher timeframe confluence filter

---

## ✅ Backtesting

Make sure to match your **Strategy Tester > Properties**:
- Initial Capital = same as the script input (e.g., $10,000)
- Order size: use `Percent of Equity`, set to `100%` (strategy calculates size internally)

---

## 🧠 Summary

This strategy enforces discipline, clear logic, and risk management:
- Enters only in strong trending conditions
- Uses volatility bands for realistic stop placement
- Locks trades one at a time for cleaner results
