# Model Explanation

This document explains the major modules and functions used by the Philippine Fiscal Simulator.

## Utility Functions

| Function | Purpose |
|---|---|
| `clone(obj)` | Creates a deep copy of a JavaScript object so scenario state can be preserved safely. |
| `clamp(min, val, max)` | Keeps a number inside a minimum and maximum range to avoid unrealistic or broken outputs. |
| `formatPeso(value, digits)` | Formats values as Philippine peso amounts. |
| `readInputValues()` | Reads all slider values and converts percentages into decimal rates. |
| `getInputSnapshot()` | Stores the current slider state for scenario save/export/compare. |
| `getNeutralForecastVals()` | Provides a neutral policy baseline for forecasting and backtesting. |

## Core Simulation Functions

| Function | Purpose |
|---|---|
| `updateEngine()` | Main simulation engine. Reads sliders, calculates fiscal flows, household impacts, inequality, debt pressure, Sankey nodes/links, KPIs, and policy notes. |
| `calculateProjection(vals)` | Estimates next-year GDP growth, OFW growth, and price drift from current policies and shocks. |
| `advanceYear()` | Moves the simulation one year forward using projection assumptions. |
| `loadPreset(key, btn)` | Loads a historical-style administration scenario. |
| `applyOfficialCalibration()` | Aligns the scenario with built-in official-style anchors for GDP, revenue, budget, debt, and remittances. |

## Household Reality Functions

| Function | Purpose |
|---|---|
| `updateEngine(options)` | Updates the full simulation. With `options.liveOnly`, it refreshes household indicators quickly and skips expensive chart/audit redraws. |
| `updateDeltaUI()` | Shows whether household indicators improved or worsened. |
| `updateHouseholdLiveSummary(metrics, vals)` | Updates the plain-English live household summary and flashes changed household metrics. |
| `scheduleSliderUpdate()` | Fast slider handler: schedules an immediate household refresh and delays heavy panels while the user drags. |
| `commitSliderUpdate()` | Final slider handler: commits the full recalculation after the user releases/changes a slider. |

## Private Capital Functions

| Function | Purpose |
|---|---|
| `calculatePrivateCapitalFlows(privateCapitalGross)` | Splits Tycoon Equity into reinvestment, luxury consumption, assets/offshore leakage, and capital tax capture. |
| `updatePrivateCapitalPanel()` | Updates the private capital explanation UI. |
| `applyPrivateCapitalGrowthBoost(projection, privateInvestmentShare)` | Adds a bounded growth contribution from productive private reinvestment to the projection object. |
| `privateCapitalFlows.taxCapture` | Field returned by `calculatePrivateCapitalFlows()` representing private capital captured back into Treasury. |

## Fiscal and Calibration Functions

| Function | Purpose |
|---|---|
| `getOfficialTargets()` | Returns official-style benchmark values for GDP, revenue, budget, deficit, debt, remittances, and growth. |
| `getCalibrationDiagnostics(metrics)` | Compares model output against target values and calculates error. |
| `updateCalibrationPanel(metrics)` | Shows model-vs-target cards. |
| `updateKPIs(metrics)` | Updates headline indicators such as revenue take, borrowing, debt/GDP, growth, and calibration error. |
| `updateRealityAudit(metrics, vals)` | Explains whether the scenario is suitable for discussion or only for demonstration. |
| `runSensitivityAudit()` | Tests how small changes in sliders affect outputs. |

## Scenario Functions

| Function | Purpose |
|---|---|
| `saveScenario()` | Saves the current state and sliders to browser local storage. |
| `loadSavedScenario()` | Loads a saved scenario. |
| `setComparisonBaseline()` | Saves the current scenario as a comparison baseline. |
| `compareToBaseline()` | Compares current results with the saved baseline. |
| `exportScenario('json')` | Exports scenario as JSON. |
| `exportScenario('csv')` | Exports scenario as CSV. |

## Shock Functions

| Function | Purpose |
|---|---|
| `applyShock('rice')` | Increases rice-price pressure. |
| `applyShock('energy')` | Increases electricity/energy pressure. |
| `applyShock('recession')` | Applies GDP drag and recession pressure. |
| `clearShocks()` | Clears temporary shocks. |

## Policy Recipe Functions

| Function | Purpose |
|---|---|
| `applyPolicyRecipe('balanced')` | Loads a balanced policy mix. |
| `applyPolicyRecipe('growth')` | Loads infrastructure/growth-oriented settings. |
| `applyPolicyRecipe('relief')` | Loads social-support settings. |
| `applyPolicyRecipe('repair')` | Loads fiscal-repair settings. |
| `autoBalanceBudget()` | Protects the debt/admin floor by adjusting spending composition. |

## Visualization Functions

| Function | Purpose |
|---|---|
| `renderVanillaSankey(nodes, links)` | Draws the SVG flow chart. |
| `renderVanillaLorenz(data)` | Draws the Lorenz curve. |
| `renderPolicyNotes(metrics, vals)` | Creates plain-English policy diagnosis cards. |
| `renderSourceRegistry()` | Shows official data-source references. |

## Data and Forecasting Functions

| Function | Purpose |
|---|---|
| `parseCsvLine(line)` | Parses CSV rows, including quoted values. |
| `parseForecastCsv(text)` | Converts CSV text into structured forecast data. |
| `normalizeForecastRow(row)` | Standardizes numeric fields and metadata. |
| `handleForecastCsvFile(event)` | Imports selected CSV files. |
| `loadStarterDataset()` | Loads demo data for UI testing. |
| `syncWorldBankHistory()` | Pulls historical nominal GDP from World Bank. |
| `fetchWorldBankAPI()` | Pulls the latest available nominal GDP from World Bank. |
| `validateEvidenceData()` | Checks whether imported data has required evidence metadata. |
| `runBacktest()` | Tests forecast logic against historical observations. |
| `runAcademicForecast()` | Produces forecast bands. |
| `exportForecastCsv()` | Exports forecast results as CSV. |
| `exportForecastTemplate()` | Exports the evidence CSV template. |
| `exportAuditPack()` | Exports assumptions, diagnostics, limitations, and results. |


## Era-specific growth anchors

When a historical administration preset is selected, the one-year projection starts from that era's rough growth anchor rather than the current 2026 Q1 growth signal. This prevents historical scenarios from accidentally inheriting a modern growth baseline.
