# FTSE 250 Value Screen

A ranked value screen of 119 non-financial FTSE 250 companies, built in Excel on
Compustat Global data from WRDS. Investment theses and 12-month price targets
for the top three are in progress.

Prices as at 30 September 2026. Constituents as at the 9 October 2026 review.

## Top 10

Factor columns show each company's rank out of 119 (1 = best). Lower composite
is better (weighted average of the five factor ranks).

| Rank | Company | Ticker | Sector | EV/EBIT | FCF yield | Cash conv. | Leverage | Growth | Composite |
|---:|---|---|---|---:|---:|---:|---:|---:|---:|
| 1 | Princes Group | PRN | Consumer Staples | 17 | 29 | 3 | 7 | 76 | 21.60 |
| 2 | Rank Group | RNK | Consumer Discretionary | 9 | 15 | 18 | 58 | 44 | 23.15 |
| 3 | Trainline | TRN | Consumer Discretionary | 13 | 22 | 22 | 62 | 24 | 25.50 |
| 4 | Galliford Try | GFRD | Industrials | 33 | 38 | 31 | 3 | 23 | 28.35 |
| 5 | AO World | AO | Consumer Discretionary | 29 | 20 | 17 | 28 | 71 | 28.40 |
| 6 | Hunting | HTG | Energy | 37 | 35 | 21 | 26 | 20 | 29.95 |
| 7 | Kier Group | KIE | Industrials | 46 | 26 | 11 | 25 | 37 | 29.95 |
| 8 | Young's | YNGA | Consumer Discretionary | 24 | 14 | 16 | 91 | 25 | 30.05 |
| 9 | Vistry Group | VTY | Consumer Discretionary | 2 | 12 | 87 | 45 | 34 | 31.15 |
| 10 | Morgan Sindall Group | MGNS | Industrials | 14 | 51 | 59 | 5 | 21 | 31.60 |

Full ranking: [output/screen_2026-09-30.csv](output/screen_2026-09-30.csv)

## Method

### Universe

FTSE 250 constituents after the 9 October 2026 review, matched to Compustat by
ISIN. ICB Financials and Real Estate are excluded (banks, insurers, investment
trusts, REITs), because EV/EBIT and cash conversion don't describe
balance-sheet businesses. Amaroq and Meridian Mining are excluded for lack of
Compustat accounts; other manual overrides are listed in the Universe sheet.

### Factors

| Factor | Definition | Better | Weight |
|---|---|---|---:|
| EV/EBIT | (market cap + net debt + minority interest) / EBIT, latest FY | Lower | 30% |
| FCF yield | (operating cash flow - capex) / market cap, latest FY | Higher | 25% |
| Cash conversion | 3-year FCF / 3-year net income | Higher | 20% |
| Leverage | Net debt / EBITDA, latest FY | Lower | 15% |
| Revenue growth | 3-year revenue CAGR | Higher | 10% |

Each company is ranked 1 to 119 on each factor, with missing or not-meaningful
values ranked last. The composite is the weighted sum of the five ranks.

### Data

Compustat Global via WRDS: Fundamentals Annual (FY2020 to FY2026) and Security
Daily (LSE listing, 30 September 2026). Non-sterling figures converted at Bank
of England spot rates on 30 September 2026. Under the data licence only ranks
are published here; [the template workbook](screener/FTSE250_Value_Screener_template.xlsx)
holds every formula with the data removed.

This is a point-in-time screen, not a live feed. Fundamentals come from each
company's latest reported fiscal year, which can be up to 18 months older than
the price date, so refreshing prices alone would imply a currency the underlying
data doesn't have.

### Known limitations

- Princes Group ranks 3rd on cash conversion because its net income is small
  after its recent IPO, which inflates the ratio and lifts its composite.
- Compustat's GICS sector disagrees with ICB for Eurowag, IWG and Saga; ICB is
  used throughout.

---

Wharton Research Data Services (WRDS) was used in preparing this analysis.
Personal academic research, not investment advice.

[Josua Edginton-Jefford](https://www.linkedin.com/in/josuaej) · BSc Finance, Durham University
