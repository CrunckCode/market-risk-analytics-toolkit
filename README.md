# Market Risk Analytics Toolkit

Deliverables from a 13-session Market Risk Management course taught by industry practitioners (Spring 2026, graded A). All work is mine, solo. The assignments mirror the daily tasks of a bank market-risk analyst or market-risk model validator. Exams, session decks and the Bloomberg data exports behind the notebooks are not included, so some notebooks need their market data supplied to re-run; saved outputs are kept in the notebooks.

## Python assignments (Jupyter)
- **Assignment 1, SOFR curve construction:** bootstraps USD SOFR discount-factor curves from swap par rates for five valuation dates (Dec-24, Mar/Jun/Sep/Dec-25) using `DF_N = (1 - rate * A) / (1 + rate * tau_N)`, ACT/360, annual fixed leg and log-linear DF interpolation. Prices a 20Y pay-fixed 4.50% swap on each date with a full cash-flow table (PV fixed, PV float, NPV) and plots the zero and DF curves.
- **Assignment 2 Q1, Black-Scholes value, delta and vega:** reads an SPX volatility surface (299 strike and expiry points), backs out `r` from the discount factor, and computes call and put value, delta and vega at each point. Put-call parity holds to about 1e-13 and vega positivity is checked.
- **Assignment 2 Q2, delta ladder:** PV01 ladder for a 20Y pay-fixed 4.50% SOFR swap on 10mm notional. Base NPV is -451,725; each of 13 par-rate tenors is bumped 1 bp, re-bootstrapped and revalued. Total PV01 is about 14,349, largest at the 20Y tenor (15,148 per bp).
- **Assignment 2 Q3, CDS bootstrap and valuation:** strips a survival and hazard-rate curve from IG spreads (6M to 20Y) by bisection on the fair-CDS condition (premium leg equals protection leg) with 40% recovery, then values a CDS by comparing premium and default leg PVs.
- **Assignment 3, risk factors (PDF):** VaR risk-factor identification and Risks-Not-in-VaR (RNiV) classification for a long American option on the S&P 500 and a European option on CDX.NA.IG Series 40, with a historical-simulation full-revaluation engine, 97.5% Expected Shortfall (FRTB-aligned) and stress overlays.

## Excel homework
| File | Task |
|---|---|
| `HW_MultiFactor_VaR_(RF_CreditSpread_SP500_EURUSD).xlsx` | Per-risk-factor P&L series and aggregated multi-factor VaR |
| `HW_Data_Quality_detection_remediation.xlsx` | Market-data quality: stale, outlier and missing detection, remediation, assumptions log |
| `HW_FO_vs_Finance_PnL_reconciliation.xlsx` | Front-office versus Finance P&L reconciliation and break explanation |
| `HW_VaR_Mapping_PnL_vectors_risk_report.xlsx` | Position to risk-factor mapping, P&L vectors, risk report |
| `HW_VaR_and_Limit_management_desk_report.xlsx` | Position to desk P&L, VaR versus limits, risk drivers |
| `HW_FRTB_SA_capital_calculation.xlsx` | FRTB Standardised Approach capital: sensitivities, risk weights, correlated aggregation |
| `Consolidated_Bootstrap_RiskLadder_CDS.xlsx` | Curve bootstrap, swap cash flows, risk ladder, CDS bootstrap and valuation |

## Topics covered across the course
SOFR/OIS curve bootstrapping, IRS and CDS valuation, volatility surfaces and Heston, Black-Scholes Greeks, PV01 and delta ladders, VaR (parametric, historical, full revaluation, multi-factor), VaR backtesting (Basel Traffic Light, Kupiec), P&L Attribution Test, VaR mapping and limit management, FRTB SA, RNiV governance, data quality, Volcker-style P&L reconciliation, Euler-Maruyama and Brownian bridge simulation.
