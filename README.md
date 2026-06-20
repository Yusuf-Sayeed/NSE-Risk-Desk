# PortfolioRisk-Pro | Portfolio Market Risk System

A production-style market risk system built in Python for a 5-stock NSE equity portfolio. Covers the full risk analyst workflow — from raw price data to a regulatory-aligned Excel dashboard.

---

## Portfolio

| Stock | Ticker | Weight |
|-------|--------|--------|
| Reliance Industries | RELIANCE.NS | 20% |
| Tata Consultancy Services | TCS.NS | 20% |
| HDFC Bank | HDFCBANK.NS | 20% |
| Infosys | INFY.NS | 20% |
| ITC | ITC.NS | 20% |

**Period:** January 2018 – December 2024 (~1,726 trading days)
**Confidence Level:** 99% (VaR & ES) | 97.5% ES per FRTB

---

## Modules

### Module 1 | Data & Portfolio Construction
- Pulls adjusted close prices via `yfinance`
- Computes daily log returns `rₜ = ln(Pₜ/Pₜ₋₁)`
- Constructs weighted portfolio return series

### Module 2 | VaR Engine
Three methods implemented and compared:
- **Historical Simulation** — non-parametric, uses actual return distribution
- **Parametric** — normal distribution assumption, closed-form z-score formula
- **Monte Carlo** — 10,000 simulations using Student's t-distribution (df=6) for fat tails

| Method | VaR (99%, 1-Day) | ES (99%) |
|--------|-----------------|----------|
| Historical Simulation | 3.08% | 4.88% |
| Parametric | 2.52% | 2.89% |
| Monte Carlo (t, df=6) | 3.39% | 4.16% |

### Module 3 | Expected Shortfall (CVaR)
- ES computed for all three methods
- Parametric ES uses closed-form FRM formula
- Aligned with Basel III / FRTB 97.5% ES standard

### Module 4 | Backtesting — Basel II Traffic Light
- 250-day rolling exception count
- All three models: 🟢 Green zone

### Module 5 | Risk Decomposition
- Marginal VaR, Component VaR, % contribution per stock
- Covariance matrix approach
- Reliance (23.0%) and Infosys (22.5%) are largest risk contributors despite equal weights

### Module 6 | Stress Testing
Historical scenarios: COVID-19 crash (−24.34%), 2022 Rate shock (+5.71%)
Hypothetical scenarios: Nifty −10% shock, IT sector selloff −15%, Banking crisis −20%

### Module 7 | Excel Dashboard
Auto-generated via `openpyxl` — summary, risk decomposition, stress testing, backtesting in one file.

---

## Tech Stack
- **Python:** `pandas`, `numpy`, `scipy`, `yfinance`, `matplotlib`, `seaborn`, `openpyxl`
- **Environment:** Jupyter Notebook (Anaconda)
- **Output:** Excel dashboard (`outputs/risk_dashboard.xlsx`)

---

## Repository Structure

PortfolioRisk-Pro/

├── Current_Project.ipynb

├── data/

│   └── prices.csv

├── outputs/

│   └── risk_dashboard.xlsx

└── reports/

└── Methodology_Report.docx

---

## Methodology
Full model documentation including assumptions, limitations, and Basel III/FRTB alignment:
📄 [`reports/Methodology_Report.docx`](reports/Methodology_Report.docx)

---

## Author
**Yusuf Sayeed**
FRM Part I (Q1 Ranking across all four subjects) | FMVA
Jamia Millia Islamia (2026)
🔗 [LinkedIn](https://linkedin.com/in/your-profile) | [GitHub](https://github.com/Yusuf-Sayeed)
