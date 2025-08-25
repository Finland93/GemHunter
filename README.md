# **GemHunter – TradingView Trend Detection Tool (Free)**

**GemHunter** is a free Pine Script indicator for TradingView that helps you visually and systematically identify **bullish**, **bearish**, and **neutral market conditions**. It combines **EMA alignment**, **MACD momentum**, and **RSI strength** with optional **higher timeframe confirmation** to filter out noise and highlight actionable trends.

---

## **What Does GemHunter Do?**

- Dynamically tints your chart background:
  - **Green:** Confirmed bullish trend.
  - **Red:** Confirmed bearish trend.
  - **Gray:** Sideways / neutral zone.
- Displays **trend tables** showing:
  - Short-term vs. long-term trend status.
  - Average length of up and down trends.
  - Current regime (uptrend/downtrend/neutral) and bar count.
- Uses **multi-timeframe (MTF) logic** so you can confirm shorter-term setups against higher timeframe trends.
- Provides **noise filters** (EMA slope, ATR separation, hysteresis) to reduce false flips in choppy markets.

---

## **Complete Setup Guide for TradingView**

Follow these steps to add GemHunter and configure it correctly:

### **1) Add GemHunter to Your Chart**
1. Open [TradingView](https://www.tradingview.com/).
2. Choose the asset and timeframe you want to analyze.
3. Open the **Pine Editor** at the bottom panel.
4. Paste the [GemHunter script code](https://github.com/Finland93/GemHunter/blob/main/GemHunter/gemhunter.pine) into the editor.
5. Click **Add to Chart**.
6. Save it to your TradingView account for easy reuse.

### **2) Configure Indicator Inputs**
Open the **Settings (⚙)** on the GemHunter indicator and review the inputs:
- **EMA Settings:**
  - *EMA Fast:* Default 50-period (adjust for asset volatility).
  - *EMA Slow:* Default 200-period (adjust for longer-term bias).
- **RSI Settings:**
  - RSI length (default 14).
  - Bull & Bear thresholds (default 55/45).
- **MACD Settings:**
  - Fast EMA: 12, Slow EMA: 26, Signal: 9 (classic MACD).
- **Noise Filters:**
  - ATR separation multiplier (how far apart EMAs must be to confirm a trend).
  - EMA slope lookback & minimum ROC (filters sideways chop).
  - RSI hysteresis & MACD strength multiplier (filters weak signals).
- **Higher Timeframe (HTF) Options:**
  - Enable/disable HTF confirmation.
  - Choose HTF timeframe (e.g., if you trade 1H charts, select 4H).
  - Mode:
    - *Display Only*: Show HTF status but don’t filter LTF signals.
    - *Filter*: Block LTF bullish if HTF bearish (and vice versa).
    - *Strict*: Require full alignment between LTF and HTF.
- **Background & Visuals:**
  - Choose background source (LTF, HTF, or gated combo).
  - Enable/disable EMAs and MACD dots.

### **3) Adjust to Your Market & Style**
- For **crypto / volatile assets:** Consider slightly shorter EMAs and wider ATR separation to avoid false flips.
- For **stocks / forex:** Default 50/200 EMAs and 14-RSI often work well.
- Backtest and optimize parameters for your asset and timeframe.

### **4) Optional: Add Alerts**
- In TradingView, go to **Alerts** → **Create Alert**.
- Select the GemHunter indicator and choose conditions like:
  - Trend regime flips (Uptrend → Downtrend).
  - Background color changes.
- This allows you to be notified instantly when trend conditions shift.

---

## **How to Use GemHunter for Trend Spotting**

Once set up, follow this process:

### **Step 1: Read the Background Color**
- **Green:** Trend bias is bullish. Favor long setups.
- **Red:** Trend bias is bearish. Favor shorts or hedging.
- **Gray:** No clear bias. Stay cautious or wait for confirmation.

### **Step 2: Confirm with Tables**
- **Top-right table:** Shows short-term vs. long-term trend strength.
- **Bottom-left:** Average up/down trend durations over recent history (helps estimate how long trends might last).
- **Bottom-right:** Current regime & number of bars since it began.

### **Step 3: Align with HTF (Optional)**
- If using HTF confirmation:
  - Only trade when **both LTF & HTF agree** (e.g., 1H background green + 4H bullish status).
  - Strict mode helps avoid false counter-trend trades.

### **Step 4: Combine with Price Action**
GemHunter gives trend context, but entries/exits are stronger with confluence:
- Look for support/resistance breaks.
- Confirm with candlestick patterns or volume.
- Manage trades based on average trend durations.

### **Step 5: Use Noise Filters to Avoid Chop**
- If you see too many flips in sideways markets, increase:
  - Confirm Bars.
  - ATR separation multiplier.
  - Minimum Hold Bars.

---

## **Optional MACD Integration – Advanced Momentum Layer**

GemHunter already uses MACD internally, but for deeper analysis you can pair it with the **[MACD Integration script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/MACD-integration.pine)**.

### **What MACD Integration Adds:**
- **TEMA-smoothed MACD**: Triple EMA smoothing for cleaner crossovers.
- **Volume-weighted MACD (optional)**: Filters low-volume moves.
- **Multi-timeframe MACD display**: View higher timeframe MACD on your current chart.
- **Divergence detection**: Automatic bullish/bearish divergence markers.
- **Visual customization**: Histogram, zero-line, crossover dots.
- **Trend status label**: Instant "Uptrend/Downtrend/Neutral" tag.

### **How to Use with GemHunter:**
1. Add MACD Integration alongside GemHunter.
2. Match MACD parameters with GemHunter’s settings for consistency.
3. Watch for:
   - MACD crossover confirming GemHunter’s background flips.
   - Divergence warnings before trend reversals.
4. Combine volume-weighted MACD for stronger conviction.
5. Use multi-timeframe MACD to spot larger trend context while trading lower timeframes.
6. Set alerts for MACD crossover with MTF confirmation (built into the script).

**Pro Tip:**  
Strongest setups often occur when:
- GemHunter background is **green/red**.
- MACD Integration crossover aligns in the same direction.
- No opposing divergence is present.

---

## **Educational References**

- [MACD – Investopedia](https://www.investopedia.com/terms/m/macd.asp)  
- [RSI – Investopedia](https://www.investopedia.com/terms/r/rsi.asp)  
- [EMA – Investopedia](https://www.investopedia.com/terms/e/ema.asp)  
- [Support & Resistance](https://www.investopedia.com/terms/s/support.asp)  
- [Divergence Trading](https://www.investopedia.com/terms/d/divergence.asp)

---

## **Disclaimer**

> GemHunter and MACD Integration are **educational tools**, not financial advice.  
> Trading and investing involve risk. You are responsible for your decisions.  
> Backtest and adjust settings for your strategy. Seek professional advice if needed.

---

### **Bottom Line**
GemHunter provides **clarity and context** for market trends.  
Use the **background tint + trend tables** for bias, confirm with price action, and optionally enhance with **MACD Integration** for momentum and divergence insights.
