# **GemHunter – TradingView Trend Detection Tool (Free)**

**GemHunter** is a TradingView Pine Script designed to help traders clearly identify **uptrends**, **downtrends**, and **neutral market phases** with minimal noise. It combines **EMA**, **MACD**, and **RSI** signals with higher timeframe confirmation to give you a reliable trend framework.

---

## **What Does GemHunter Do?**

- Colors your chart **background** dynamically:
  - **Green**: Confirmed bullish trend
  - **Red**: Confirmed bearish trend
  - **Gray**: Neutral or indecisive market
- Displays:
  - **Short-term and Long-term trend status**
  - **Average uptrend/downtrend durations**
  - **Current regime and bar count**
- Uses **multi-timeframe (MTF) analysis** to confirm signals and reduce false flags.
- Supports customizable noise filters and minimum-hold bars to avoid whipsaws.

---

## **How to Add GemHunter to TradingView**

1. Open **TradingView**.
2. Go to **Pine Editor** (bottom panel).
3. Copy-paste the [GemHunter Pine Script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/gemhunter.pine).
4. Click **Add to Chart**.
5. Adjust settings in the **indicator inputs** panel:
   - EMA lengths, RSI thresholds, MACD parameters.
   - Enable/disable higher timeframe confirmation.
   - Set your preferred background and filter options.

---

## **How to Spot Trends with GemHunter**

### **1) Confirm Trend Direction**
GemHunter defines trends using **EMA alignment + MACD + RSI**:
- Bullish: Price above EMAs, MACD and RSI confirm strength.
- Bearish: Price below EMAs, MACD and RSI confirm weakness.
- Neutral: No clear confirmation.

The **background color** helps you visually confirm this instantly.

### **2) Watch Multi-Timeframe Alignment**
For more reliable entries:
- Enable **HTF mode** (e.g., analyze a 1H chart with 4H confirmation).
- When **short-term and higher timeframe agree**, trend conviction is stronger.

### **3) Check Average Trend Durations**
The bottom-left panel shows:
- **Avg Uptrend Bars:** How long uptrends typically last.
- **Avg Downtrend Bars:** How long downtrends typically last.

Use this to set realistic trade holding periods and manage expectations.

### **4) Identify Current Market Regime**
The bottom-right panel displays:
- **Uptrend**, **Downtrend**, or **Neutral**.
- **Bars in Trend:** How long the current regime has lasted.

Combine this with background color for quick trend validation.

### **5) Adjust Filters to Reduce Noise**
- **Confirm Bars:** Require multiple bars to confirm a trend.
- **EMA separation & slope filters:** Prevent signals in sideways chop.
- **Minimum Hold Bars:** Avoid rapid flip-flops by forcing a minimum trend duration.

---

## **Best Practices for Traders**

- **Combine with price action:** Use background as a trend bias, not a trade signal by itself.
- **Look for confluence:** Align GemHunter’s bias with support/resistance levels, breakouts, or candlestick patterns.
- **Use alerts:** Configure TradingView alerts when regime flips (Uptrend → Downtrend) for timely notifications.
- **Backtest your settings:** Adjust EMA/RSI/MACD parameters per asset (crypto, stocks, forex) and timeframe.

---

## **Optional MACD Integration**

Pair GemHunter with the [MACD Integration script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/MACD-integration.pine) for:
- **Advanced MACD smoothing** (TEMA)
- **Volume-weighted MACD**
- **Divergence detection**
- **Multi-timeframe MACD confirmation**

This helps you validate GemHunter’s background signals with an additional momentum layer.

---

## **Educational Resources**

- [MACD – Investopedia](https://www.investopedia.com/terms/m/macd.asp)
- [RSI – Investopedia](https://www.investopedia.com/terms/r/rsi.asp)
- [EMA – Investopedia](https://www.investopedia.com/terms/e/ema.asp)
- [Support & Resistance](https://www.investopedia.com/terms/s/support.asp)

---

## **Disclaimer**

> **GemHunter is for educational purposes only.**  
> This is **not financial advice**. Markets are risky, and you are fully responsible for your trading decisions. Backtest thoroughly and consult a financial professional before making investment decisions.

---

### **Bottom Line:**
GemHunter gives you **clarity**. No more guessing trend direction—use its **background tint + regime tables** to align trades with dominant market bias and avoid sideways traps.
