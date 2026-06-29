# GemHunter – TradingView Trend Detection Tool (Free)

**GemHunter** is a free Pine Script **v6** indicator for TradingView that classifies the market into **bullish**, **bearish**, and **neutral** regimes. It combines **EMA alignment**, **MACD momentum**, and **RSI strength**, adds an optional **ADX/DMI trend-strength filter**, and confirms everything against a **higher timeframe** — so you spend less time staring at chop and more time on charts that are actually trending.

It ships with a companion oscillator, **MACD Integration (“MACD+”)**, for momentum, multi-timeframe confirmation, and divergence.

> Educational tool, not financial advice. It gives you **trend context and alerts** — not guaranteed entries. Always confirm with price action and your own risk management.

---

## What GemHunter Does

- **Tints the chart background** by regime: green (bullish), red (bearish), gray (neutral).
- **Marks regime flips** on the chart with ▲ *Bull* / ▼ *Bear* triangles so reversals are easy to spot.
- **Shows three compact tables**: higher-timeframe vs chart status + live ADX, average up/down trend durations, and the current regime with its bar count.
- **Filters noise** with EMA-separation (ATR), slow-EMA slope, RSI hysteresis, MACD-histogram strength, a debounce, and a minimum hold time — all tunable.
- **Confirms against a higher timeframe** without repainting (values update only when the HTF bar closes).
- **Fires alerts** on regime flips and on chart/HTF bull-bear transitions, so you can screen a whole watchlist instead of watching one chart.

---

## Quick Start

1. Open [TradingView](https://www.tradingview.com/) and load the symbol and timeframe you want.
2. Open the **Pine Editor** (bottom panel).
3. Paste in the [GemHunter script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/gemhunter.pine).
4. Click **Add to Chart**, then save it to your account for reuse.
5. (Optional) Repeat with the [MACD Integration script](https://github.com/Finland93/GemHunter/blob/main/GemHunter/MACD-integration.pine) — it opens in a separate pane.

---

## Inputs Reference

### Trend Engine (EMA + MACD + RSI)
- **EMA Fast / EMA Slow** — the two trend EMAs (default 50 / 200). Fast = responsiveness, Slow = macro bias.
- **RSI Length / Bull / Bear Thresholds** — momentum band (default 14, 55 / 45).
- **MACD Fast / Slow / Signal** — classic MACD (12 / 26 / 9).
- **Votes Needed (of 3)** — how many of EMA / MACD / RSI must agree (default 2). Set to 3 for the strictest, fewest signals.
- **Bars to Confirm Regime** — a raw signal must persist this many bars before it counts (debounce, default 3).

### Noise Filters (Anti-Chop / Hysteresis)
- **Min EMA Separation (×ATR)** — EMAs must be this far apart, in ATRs, to count as trending. Higher = fewer chop flips.
- **EMA Slow Slope Lookback / Min ROC %** — the slow EMA must actually be sloping. Filters flat, sideways markets.
- **RSI Hysteresis (±)** — widens the RSI bands so price has to commit before a flip.
- **MACD Hist Strength (Window / ×StDev)** — the MACD histogram must exceed this many standard deviations to count. Filters weak momentum.
- **Require ADX Trend Strength** *(new)* — blocks signals when ADX is weak or +DI/−DI disagree with the trade side. Excellent for cutting ranges. Default **on**; turn off to revert to pure voting.
- **ADX / DI Length, ADX Smoothing, ADX Min Threshold** — DMI settings (default 14 / 14 / 18). Typical threshold 18–25; higher = only strong trends pass.

### Higher Timeframe Confirmation
- **Enable HTF Confirmation** — on by default.
- **HTF** — the higher timeframe to check (e.g. `60`, `240`, `D`, `W`).
- **HTF Mode**
  - *Display Only* — show HTF status, don’t filter.
  - *Filter* — block chart signals that fight the HTF (default).
  - *Strict* — require full chart + HTF agreement.

### Background & Signals
- **Background Uses** — drive the tint from `LTF` (chart only), `Gated` (chart after HTF gating, default), or `HTF` (higher timeframe only).
- **Min Bars to Hold Trend** — the regime can’t flip again until this many bars pass since the last flip.
- **Show Flip Markers** — the ▲/▼ regime-change triangles (default on).

### Style
- Background tint, tables, EMAs, and optional MACD zero-line dots can each be toggled.

---

## How to Read It

**1. Background colour — the headline bias.** Green favours longs, red favours shorts/hedges, gray means no clear edge.

**2. Flip markers — the moment it changed.** A green ▲ *Bull* prints when the regime turns up; a red ▼ *Bear* when it turns down. These are the events worth reacting to.

**3. Tables.**
- **Top-right** — `HTF:` (higher-timeframe status), `LTF:` (chart status after gating), and `ADX:` (live trend strength; green once it clears the threshold, orange below). *Note: these rows are **timeframes**, not buy/sell labels.*
- **Bottom-left** — `AVG UP:` / `AVG DOWN:` average durations of past up- and down-trends, to gauge how long moves tend to run on this symbol.
- **Bottom-right** — current `Trend:` and how many `Bars:` it has lasted.

**4. Align with the higher timeframe.** In *Filter* or *Strict* mode the strongest reads are when chart and HTF agree (e.g. chart background green + `HTF: Bullish`).

**5. Combine with price action.** GemHunter gives context; entries are stronger with confluence — support/resistance breaks, candle patterns, volume.

---

## Tuning Guide

**Seeing too many flips in a range?** Increase *Bars to Confirm Regime*, *Min EMA Separation*, or *Min Bars to Hold Trend*, keep *Require ADX* on, and/or raise *Votes Needed* to 3.

**Crypto / volatile assets:** consider slightly shorter EMAs, a wider ATR separation, and ADX on — volatile markets fake out narrow filters.

**Stocks / forex:** the defaults (50 / 200 EMA, RSI 14, ADX 18) are a sensible starting point.

Always backtest parameter changes on the specific symbol and timeframe you trade.

---

## Alerts

The script defines named alert conditions, so they show up directly in TradingView’s alert dialog:

1. Right-click the chart (or use the top toolbar) → **Add Alert**.
2. Under **Condition**, pick **GemHunter v4** and choose one:
   - ▲ Flip to Uptrend / ▼ Flip to Downtrend
   - LTF Bullish (gated) / LTF Bearish (gated)
   - HTF turned Bullish / HTF turned Bearish
3. Set the trigger to **Once Per Bar Close** to match the non-repainting logic, and save.

Each alert message includes the ticker and interval, so the same alert works across an entire watchlist.

---

## Companion: MACD Integration (“MACD+”)

GemHunter already uses MACD internally; **MACD+** is a separate, deeper momentum layer you can run in its own pane.

**What it adds**
- **Selectable smoothing** — EMA, DEMA, TEMA, RMA, or Ehlers **SuperSmoother** (default). SuperSmoother gives low lag with little noise; pick EMA for a textbook MACD.
- **Volume-aware MACD (optional)** — scales the MACD by relative volume and safely ignores instruments that have no volume (no division-by-zero).
- **Multi-timeframe confirmation** — require crosses to agree with a higher timeframe’s MACD.
- **Four-colour histogram** — bright when momentum is expanding, faded when it’s fading, so you can read strength at a glance.
- **Divergence detection** — optional pivot-based bullish/bearish divergence markers.
- **Trend label** — a live `Uptrend / Downtrend / Neutral` tag plus the MTF state.
- **Built-in alerts** — bullish/bearish cross and bullish/bearish divergence (under **Condition: GemHunter MACD+**).

**Using it with GemHunter**
1. Add MACD+ beneath GemHunter and match the Fast/Slow/Signal settings for consistency.
2. Treat a MACD+ cross **in the direction of GemHunter’s background** as confirmation.
3. Watch for divergence as an early heads-up before the regime itself flips.
4. Use the MTF row to keep lower-timeframe trades on the right side of the larger trend.

**Strongest setups** tend to line up: GemHunter background green/red, a MACD+ cross the same way, and no opposing divergence.

---

## Educational References

- [MACD – Investopedia](https://www.investopedia.com/terms/m/macd.asp)
- [RSI – Investopedia](https://www.investopedia.com/terms/r/rsi.asp)
- [EMA – Investopedia](https://www.investopedia.com/terms/e/ema.asp)
- [ADX / DMI – Investopedia](https://www.investopedia.com/terms/a/adx.asp)
- [Support & Resistance](https://www.investopedia.com/terms/s/support.asp)
- [Divergence Trading](https://www.investopedia.com/terms/d/divergence.asp)

---

## Disclaimer

> GemHunter and MACD Integration are **educational tools**, not financial advice.
> Trading and investing involve risk, and you are responsible for your own decisions.
> Backtest and adjust the settings for your strategy, and seek professional advice if needed.

---

### Bottom Line

GemHunter gives you **clarity and context**: a colour-coded regime, flip markers, trend-duration stats, and alerts you can run across a watchlist. Use it for bias, confirm with price action, and layer in **MACD+** for momentum and divergence.
