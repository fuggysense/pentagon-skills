---
name: weekly-review
description: Pull campaign metrics and compile weekly performance report. Flags anomalies. Use every 7 days or on demand.
---

Run weekly review for $ARGUMENTS (client name or "all").

1. Pull metrics from available sources:
   - Meta Ads: CPA, CTR, spend, impressions, conversions
   - Google Analytics: traffic, bounce rate, conversions
   - GSC: rankings, clicks, impressions
   - Postiz: engagement, reach
2. Compare vs. previous week and targets
3. Flag anomalies: CPA +50%, CTR -30%, spend stopped, ad disapproved
4. Compile report with 2-3 concrete action items

Output: docs/ops/weekly/YYMMDD.md
DM Strategist with report + action items.
If anomalies detected, DM Strategist immediately — don't wait for the scheduled review.
