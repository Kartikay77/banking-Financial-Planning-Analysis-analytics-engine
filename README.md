# Banking FP&A Analytics Engine

End-to-end FP&A workflow that ingests public company financials via **yfinance**, engineers bank-style KPIs, produces **time-series forecasts** (XGBoost), and exports a stakeholder-ready **Excel FP&A pack** with charts and an executive summary.

> Demo/education only. Yahoo! Finance data can be delayed or incomplete.

---

## ✨ Highlights

- **Ingest** quarterly IS/BS/CF (default: AAPL, MSFT, NVDA)
- **Standardize** messy Yahoo column names → canonical (`REV`, `OPINC`, `NET`, `ASSET`, …)
- **KPIs**: Revenue Growth, Operating/Profit/FCF Margin, Current Ratio, Debt-to-Equity, Interest Coverage
- **Banking cadence**: **Biweekly Opex** with **YoY** (quarter ≈ 13 weeks)
- **Headcount & productivity**: Revenue/Opex per Employee, basic risk flags
- **Forecast** next-quarter revenue per ticker (log-XGB + TimeSeriesSplit CV)
- **Deliverable**: `Axos_FP&A_Pack.xlsx` (Exec Summary, Scenarios template, Biweekly forecasts)

---

## 🚀 Quick Start

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -U yfinance pandas scikit-learn xgboost matplotlib xlsxwriter
python financial_analyst-3.py
```

--- 

## 🧰 Tech Stack
Python, pandas, yfinance, scikit-learn, xgboost, matplotlib, xlsxwriter.

---
# Result
![All_companies_prediction_table](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/All_companies_prediction_table.png)

![APPLE_OPEX_Biweekly](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/APPLE_OPEX_Biweekly.png) 

![Apple_NIR_VS_TIME](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Apple_NIR_VS_TIME.png) 

![Apple_quaterly_trend](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Apple_quaterly_trend.png)

![Apple_waterfall_graph](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Apple_waterfall_graph.png)

![Current_Ratio](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Current_Ratio.png)

![Debt_to_equity_chart](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Debt_to_equity_chart.png)

![FCF_Margin_graph](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/FCF_Margin_graph.png)

![Final_result](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Final_result.png)

![MICROSOFT_QUATERLY_TREND](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/MICROSOFT_QUATERLY_TREND.png)

![Microsoft_Non_Interest_trend](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Microsoft_Non_Interest_trend.png)

![Microsoft_biweekly_opex_vs_time](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/Microsoft_biweekly_opex_vs_time.png)

![NVIDIA_NEXT_Q_PREDICTION](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/NVIDIA_NEXT_Q_PREDICTION.png)


![NVIDIA_NIR_VS_TIME](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/NVIDIA_NIR_VS_TIME.png)

![NVIDIA_OPEX_PER_BIWEEKLY](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/NVIDIA_OPEX_PER_BIWEEKLY.png)


![all_companies_predicted_growth_next_quater](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/all_companies_predicted_growth_next_quater.png)

![all_values_companies](https://github.com/Kartikay77/banking-Financial-Planning-Analysis-analytics-engine/blob/main/all_values_companies.png)

Executive Summary (final)
Apple (AAPL)
Quarterly revenue trend + next-Q prediction
Non-Interest Income trend (demo)
Biweekly Opex trend
Revenue waterfall (QoQ demo)
Microsoft (MSFT)
Quarterly revenue trend + next-Q prediction
Non-Interest Income trend (demo)
Biweekly Opex trend
NVIDIA (NVDA)
Quarterly revenue trend + next-Q prediction
Non-Interest Income trend (demo)
Biweekly Opex trend
Cross-company ratios
Current Ratio
Debt to Equity
FCF Margin
Comparison tables
Next-quarter predictions table
Predicted growth next quarter (bars)
Feature/metric snapshot
If any filename differs in your repo, update the image path above (they are referenced via relative paths).


---

Budgeting & Forecasting: Builds simple budget baseline (e.g., +5%), forecasts next-Q revenue, and computes variance vs budget
Full financial analysis: Derives Operating/Profit/FCF margins; liquidity & solvency ratios; employee productivity
Biweekly cadence: Converts quarterly opex ≈ 13-week cadence with YoY tracking
Risk flags: Budget miss, low coverage, efficiency drag, opex pressure
Pack-ready output: Axos_FP&A_Pack.xlsx for exec review

---

# ⚠️ Troubleshooting
ModuleNotFoundError: xlsxwriter → pip install xlsxwriter
Yahoo column drift (KeyError) → keep the pick()/rename block intact
Index alignment errors → ensure df is sorted by Ticker, Period before assigning groupby results
