# Data Sources

The project is designed to work with evidence-backed official or public datasets.

## Intended Data Owners

| Data | Preferred source |
|---|---|
| GDP level and real GDP growth | Philippine Statistics Authority or World Bank fallback |
| Inflation / CPI | Philippine Statistics Authority |
| National budget and expenditure | Department of Budget and Management |
| Revenue program and tax collections | Department of Finance / Bureau of Internal Revenue / Bureau of the Treasury |
| National government debt | Bureau of the Treasury |
| OFW cash remittances | Bangko Sentral ng Pilipinas |

## Row-Level Evidence Metadata

CSV imports should include row-level metadata columns such as:

```text
source_owner
source_dataset
source_url
release_date
vintage_date
retrieved_at
unit_basis
frequency
row_status
source_tag
transform_note
```

Row-level metadata is useful, but it is not enough when one row combines GDP, revenue, debt, remittances, and inflation from different agencies.

## Optional Per-Variable Source Metadata

For evidence-grade work, include optional per-variable provenance fields:

```text
gdp_source_owner, gdp_source_url
growth_source_owner, growth_source_url
revenue_source_owner, revenue_source_url
expenditure_source_owner, expenditure_source_url
debt_source_owner, debt_source_url
remittances_source_owner, remittances_source_url
inflation_source_owner, inflation_source_url
```

The app accepts these fields and reports variable-source coverage in the Evidence Ledger.

## Important Rule

Do not mix complete annual data with partial-year, YTD, quarterly, or projected data unless the row is clearly marked.

Recommended row statuses:

```text
complete_official
complete_demo
partial_anchor
projection
estimate
```

Only complete official rows should be used for serious backtesting.
