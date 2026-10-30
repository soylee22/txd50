# Lodestar TXD50

Transatlantic Quality Dividend 50 ETF tracker and dashboard: https://soylee22.github.io/txd50/

## Overview

Lodestar TXD50 is a rules-based, point-in-time dividend strategy engineered from the Dow Jones U.S. Dividend 100 methodology. It runs across a combined universe of the FTSE 350, STOXX Europe 600, and S&P 500, adapted for execution as a 50-stock Trading 212 pie.

The strategy allocates 50% to United States dividend compounders and 50% to European and British dividend compounders (25 stocks per regional sleeve), rebalancing caps quarterly and reconstituting annually on the third Friday of March.

## The 5-Step Funnel

1. **Universe and exclusions:** Screen all constituents of FTSE 350, STOXX Europe 600, and S&P 500. Exclude REITs, MLPs, investment trusts, and convertibles.
2. **Dividend persistence:** Require 10 consecutive years of dividend distributions without a dividend cut.
3. **Median yield chop:** Rank survivors by dividend yield within each regional basket. Eliminate the bottom 50% lowest-yielding companies to eliminate low-yielding growth names.
4. **Composite quality score:** Rank the top half survivors on four fundamental factors:
   - Cash Flow to Total Debt (free cash flow divided by total debt)
   - Return on Equity (net income divided by shareholders equity)
   - Indicated Dividend Yield
   - Five-Year Dividend Growth Rate
   Equal-weight the factor ranks to generate a composite score. Select the top 25 United States and top 25 European/UK stocks.
5. **Capped market cap weighting:** Weight constituents by float-adjusted market capitalisation within each sleeve. Enforce a 4.0% single-stock cap and a 25.0% sector cap at each quarterly rebalance.

## Point-In-Time Performance (2010 to 2026)

Point-in-time backtesting reconstructs the exact portfolio each March without look-ahead survivorship bias.

| Metric | Lodestar TXD50 | VUSA (S&P 500) | SCHD (US Div 100) | VUKG (FTSE 100) | VWRL (All-World) |
|---|---|---|---|---|---|
| Annualised Return (CAGR) | 15.75% | 14.33% | 13.36% | 12.33% | 11.56% |
| Annualised Volatility | 12.68% | 14.85% | 14.12% | 13.90% | 13.45% |
| Sharpe Ratio (Rf=3.5%) | 0.97 | 0.78 | 0.61 | 0.71 | 0.64 |
| Maximum Drawdown | -13.12% | -20.94% | -18.03% | -16.45% | -19.20% |
| Indicative Dividend Yield | 5.33% | 1.45% | 3.42% | 3.85% | 1.95% |
| 5Y Dividend Growth (CAGR) | +12.62% | +5.80% | +9.20% | +4.10% | +6.20% |

Returns in British Pounds (£), gross of dividend withholding tax, with quarterly cap drift adjustments.

## Trading 212 Configuration

The portfolio matches Trading 212 pie constraints (50 stocks maximum):
- 25 United States stocks (50.0% regional weight)
- 25 European and United Kingdom stocks (50.0% regional weight)
- Single stock maximum cap: 4.0%

Export configurations are provided in `data/t212_pie_config.csv` and via the one-click copy button on the dashboard.
