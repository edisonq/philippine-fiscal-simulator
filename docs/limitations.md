# Limitations

This simulator is experimental and simplified.

## Current Limitations

- Household indicators are proxy estimates, not official household forecasts.
- The app uses a **price stress multiplier** for household pressure; this is not the same as official CPI inflation.
- Synthetic inequality is not an official Gini estimate.
- Historical administration presets are approximate scenarios, not full historical reconstructions.
- CPI inflation and GDP deflator are not yet fully separated for academic-grade nominal GDP modeling.
- The model does not fully capture interest rates, exchange rates, monetary policy, import prices, sector-level output, enforcement quality, corruption, weather shocks, or political conditions.
- Row-level evidence metadata can be incomplete when different variables come from different agencies. Use optional per-variable source fields for stronger provenance.
- Backtesting quality depends on the quality and completeness of imported data.
- The prototype uses Tailwind from CDN. For production or restricted/offline settings, compile and serve CSS locally.

## Safe Use

Use this simulator for education, discussion, comparison, and transparent scenario exploration.

Do not use it as the sole basis for:

- legal decisions
- tax decisions
- investment decisions
- government policy decisions
- public claims of official forecasts
- financial planning
- election or campaign claims without clear caveats

Always verify data from original sources and consult qualified professionals where appropriate.


## Historical calibration context

Historical presets are simplified era scenarios. They use rough growth anchors for their period, but they are not official historical reconstructions and should not be compared directly against 2026 budget, revenue, deficit, or debt targets.
