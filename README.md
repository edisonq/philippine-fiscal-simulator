# Philippine Fiscal Simulator

**Philippine Fiscal Simulator** is an experimental web-based policy simulator for exploring how taxes, public spending, borrowing, debt, remittances, private capital, and shocks may affect the Philippine economy and everyday households.

It is designed for **education, scenario exploration, civic discussion, and future game development**.

> **Important:** This is not official government software, legal advice, tax advice, financial advice, investment advice, or a certified economic forecast. Read [`DISCLAIMER.md`](DISCLAIMER.md), [`ACCEPTABLE_USE.md`](ACCEPTABLE_USE.md), and [`docs/limitations.md`](docs/limitations.md) before using or sharing outputs.

Current app version: **V10.6.3**

---

## Quick Start

Open `index.html` in a browser.

No build step is required. The current demo uses vanilla JavaScript and Tailwind loaded from CDN. For production or offline deployments, see [`docs/deployment.md`](docs/deployment.md).

---

## What It Does

Users can adjust policy levers such as:

- elite / tycoon tax
- middle-class income tax
- corporate income tax
- VAT / consumption tax
- social, education, and health spending
- infrastructure spending
- private capital recycling
- rice, energy, and recession shocks

The app visualizes possible effects through:

- a custom SVG Sankey-style economic flow chart
- Household Reality indicators: rice, electricity, ER wait time, class size, and estimated aid
- Synthetic Inequality / Lorenz curve
- KPI cards for revenue, borrowing, debt, growth, and calibration error
- scenario save/load/compare/export tools
- evidence-data import, backtesting, and forecast bands

---

## Simple Explanation

Think of the country like a household:

- **Income** = taxes, fees, and other revenue
- **Spending** = schools, hospitals, roads, aid, and operations
- **Borrowing** = money borrowed when spending is higher than income
- **Debt** = money that must be paid back later
- **Private capital** = money kept by businesses and wealthy households, which may be reinvested, spent, stored in assets, or partly taxed later

The simulator helps users ask: **“What trade-offs happen if policy changes?”**

---

## Core Model Summary

The simplified model routes GDP and OFW remittances through households, corporations, private capital, Treasury, and public spending.

```text
GDP + OFW remittances
→ households and corporate sector
→ taxes, VAT, private capital, and Treasury
→ social services, infrastructure, debt/admin, and household indicators
```

Private capital is no longer a dead-end. It is routed into:

```text
Tycoon Equity
├── Private Investment
├── Luxury Consumption
├── Assets / Offshore / Idle Wealth
└── Capital Tax Capture → Treasury
```

See:

- [`docs/formulas.md`](docs/formulas.md) for formulas
- [`docs/model-explanation.md`](docs/model-explanation.md) for function/module explanations
- [`docs/data-sources.md`](docs/data-sources.md) for evidence-data guidance

---

## Repo Structure

```text
philippine-fiscal-simulator/
├── index.html
├── README.md
├── LICENSE
├── DISCLAIMER.md
├── ACCEPTABLE_USE.md
├── CONTRIBUTING.md
├── assets/
├── docs/
│   ├── model-explanation.md
│   ├── formulas.md
│   ├── data-sources.md
│   ├── deployment.md
│   ├── limitations.md
│   └── game-roadmap.md
├── data/
│   ├── evidence-template.csv
│   └── sample-starter-data.csv
└── tests/
```

---

## Evidence Data

The built-in and sample datasets are for demonstration and UI testing only. Serious analysis should import cleaned official annual data with provenance metadata.

Required core columns:

```text
year, gdp_nominal_php_b, real_gdp_growth_pct, revenue_php_b,
expenditure_php_b, debt_php_b, remittances_php_b, inflation_pct
```

Recommended evidence metadata includes both row-level and optional per-variable source columns. This matters because GDP, revenue, debt, remittances, and inflation usually come from different agencies.

See [`data/evidence-template.csv`](data/evidence-template.csv).

---

## Responsible Use

Do not present simulator outputs as official government data, guaranteed forecasts, legal/tax/financial advice, or the sole basis for real-world decisions.

If you publish results, clearly state:

1. the version used,
2. the data sources used,
3. assumptions changed,
4. model limitations,
5. that outputs are scenario estimates, not official predictions.

The MIT License controls the software license. [`ACCEPTABLE_USE.md`](ACCEPTABLE_USE.md) explains intended responsible use and community expectations.

---

## Future Plans

The long-term vision is to evolve this into a full fiscal-policy learning platform and strategy game.

Planned directions:

- full game mode with election cycles, public trust, shocks, and scorecards
- citizen/simple mode for ordinary users
- advanced policy mode for researchers
- evidence-grade data pipeline with per-variable provenance
- multiplayer/classroom mode
- story campaigns such as rice crisis, debt repair, recession recovery, and infrastructure push
- regional/provincial modules
- Filipino, Cebuano, and other Philippine-language localization

See [`docs/game-roadmap.md`](docs/game-roadmap.md).

---

## Suggested GitHub Topics

```text
philippines economics fiscal-policy public-finance simulation data-visualization policy-simulator javascript tailwindcss sankey education forecasting open-source
```

---

## Disclaimer

This project is for education, scenario exploration, and public understanding.

It should not be used as official government forecasting, investment advice, tax advice, legal advice, policy certification, or the sole basis for serious real-world decisions without verified official datasets, professional review, and independent validation.


## V10.6.3 Calibration Context Update

Historical administration presets now use rough era-specific growth anchors when advancing years. The 2026 calibration panel is disabled for older presets to avoid misleading comparisons between historical-era scenarios and current fiscal anchors.
