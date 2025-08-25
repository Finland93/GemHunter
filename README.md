# **GemHunter – TradingView Trend Detection Tool (Free)**

**GemHunter** is a TradingView Pine Script designed to help traders clearly identify **uptrends**, **downtrends**, and **neutral phases** with minimal noise. It combines **EMA**, **MACD**, and **RSI** signals with optional higher timeframe confirmation to give you a reliable framework for trading in any market.

---

## **What Does GemHunter Do?**

- **Dynamic background tint**: 
  - **Green** = confirmed bullish trend  
  - **Red** = confirmed bearish trend  
  - **Gray** = neutral / chop  
- **Multi-timeframe confirmation**: Avoid false flags by confirming trends against a higher timeframe.
- **Trend tables**:
  - **Short vs Long-term trend status** (top-right)
  - **Average trend durations** (bottom-left)
  - **Current regime & bar count** (bottom-right)
- **Noise filters**: ATR-based EMA separation, slope filters, and minimum-hold bars to reduce whipsaws.

---

## **How to Add GemHunter to TradingView**

1. Open **TradingView**.
2. Navigate to **Pine Editor** (bottom panel).
3. Copy-paste the [GemHunter Pine Script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/gemhunter.pine).
4. Click **Add to Chart**.
5. Adjust indicator settings to match your trading style:
   - EMA lengths (fast/slow)
   - RSI thresholds
   - MACD parameters
   - HTF confirmation options (Filter / Strict)
   - Background mode (LTF-only, HTF-only, or gated combo)

---

## **How to Spot Trends with GemHunter**

### **1) Confirm Trend Direction**
GemHunter’s background and tables use **EMA + MACD + RSI** logic:
- **Bullish:** Price above EMAs and at least MACD or RSI confirm strength.
- **Bearish:** Price below EMAs and at least MACD or RSI confirm weakness.
- **Neutral:** No clear confirmation; stay defensive.

### **2) Watch Multi-Timeframe Alignment**
Enable **HTF confirmation** for stronger conviction:
- E.g., On a 1H chart, set HTF to 4H.
- Only trade in the direction where LTF and HTF align (optional “Strict” mode).

### **3) Check Average Trend Durations**
Bottom-left table shows typical uptrend/downtrend lengths (in bars).  
Use this for **holding period expectations** and **trade timing**.

### **4) Use Minimum Hold & Filters**
- **Confirm Bars:** Require multiple bars for confirmation to avoid false flips.
- **ATR-based EMA separation & slope filters:** Prevent signals in sideways chop.
- **Minimum Hold Bars:** Ensures trends persist before flipping.

### **5) Combine with Price Action**
The background tint is your **bias**, not a standalone entry signal.  
Look for confluence with:
- Support/resistance levels
- Breakouts/pullbacks
- Candlestick patterns

---

## **Optional MACD Integration – Advanced Momentum Layer**

To enhance GemHunter’s signal reliability, add the [MACD Integration script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/MACD-integration.pine) to your chart.  

This optional tool adds **advanced momentum analysis**, including:

### **Features:**
- **TEMA-smoothed MACD:**  
  - Triple EMA smoothing reduces lag and gives cleaner MACD/signal crossovers.
- **Volume-weighted MACD (optional):**  
  - Accounts for trading volume to filter weak crossovers.
- **Multi-timeframe MACD:**  
  - View MACD from a higher timeframe on your current chart.
- **Divergence detection:**  
  - Automatic bullish/bearish divergence markers when price & MACD disagree.
- **Customizable visuals:**  
  - Histogram, zero line, and crossover circles for clear signal interpretation.
- **Trend status label:**  
  - Shows **Uptrend**, **Downtrend**, or **Neutral** directly on your chart.

### **How to Use MACD Integration with GemHunter:**
1. Add both **GemHunter** and **MACD Integration** indicators to the same chart.
2. Match MACD parameters with GemHunter’s MACD settings for consistency.
3. Use MACD Integration to confirm:
   - Crossovers aligning with GemHunter background flips.
   - Divergences warning of potential reversals before GemHunter flips.
4. For added precision:
   - Turn on **volume-weighted MACD** to filter low-participation crossovers.
   - Use **multi-timeframe MACD** (e.g., view 4H MACD while trading on 1H).
5. Optional: Set TradingView alerts for MACD crossover with MTF confirmation (built into the script).

**Pro Tip:**  
When GemHunter’s background turns **green/red** AND MACD Integration confirms with a **same-direction crossover + no bearish/bullish divergence**, the probability of a strong trend continuation is higher.

---

## **Educational Resources**

- [MACD – Investopedia](https://www.investopedia.com/terms/m/macd.asp)
- [RSI – Investopedia](https://www.investopedia.com/terms/r/rsi.asp)
- [EMA – Investopedia](https://www.investopedia.com/terms/e/ema.asp)
- [Support & Resistance](https://www.investopedia.com/terms/s/support.asp)
- [Divergence Trading](https://www.investopedia.com/terms/d/divergence.asp)

---

## **Disclaimer**

> **GemHunter and MACD Integration are for educational purposes only.**  
> This is **not financial advice**. Trading is risky and you are solely responsible for your decisions.  
> Always backtest and consult a financial professional before committing capital.

---

### **Bottom Line:**
- **GemHunter = Trend bias engine (EMA + MACD + RSI + HTF).**  
- **MACD Integration = Momentum confirmation & divergence spotting.**  
Together they form a **robust system** for trading any market or timeframe.
