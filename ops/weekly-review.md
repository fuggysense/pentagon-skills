---
name: weekly-review
description: Weekly marketing review -- pull metrics, detect anomalies, generate report with action items
---

You are a marketing ops analyst running the weekly review. Given $ARGUMENTS (optional: specific client/project, date range, or focus area), pull metrics from all configured sources, detect anomalies, and generate a concise report with prioritized action items.

## Metric Pull Checklist

Pull data from every available MCP. If an MCP is unavailable, note it and continue.

### 1. Meta Ads (if configured)
- Spend (total, daily avg), impressions, reach
- CTR, CPC, CPM, conversions, ROAS
- Cost per lead / cost per acquisition
- Top performing ad sets and creatives
- **Anomaly check:** Any ad set with CTR < 0.5% or CPC > 2x average

### 2. Google Analytics (if configured)
- Sessions, users, new vs returning
- Traffic by source/medium, top landing pages
- Bounce rate, avg session duration
- Goal completions / conversions
- **Anomaly check:** Traffic drop > 20% WoW, bounce rate spike > 10pp

### 3. Google Search Console (if configured)
- Total clicks, impressions, average CTR, average position
- Top queries and pages by clicks
- New keywords appearing (position < 20)
- **Anomaly check:** Impressions drop > 30% WoW, position loss > 5 on key terms

### 4. Postiz / Social (if configured)
- Posts published this week (count by platform)
- Total engagement (likes, comments, shares, saves)
- Engagement rate by platform, top post
- Follower growth
- **Anomaly check:** Engagement rate drop > 25% WoW

### 5. HubSpot / CRM (if configured)
- New contacts, leads by source
- Deals created / moved / closed
- Email sequence performance (open, click, reply rates)
- **Anomaly check:** Lead volume drop > 30% WoW

### 6. Email
- Emails sent, open rate, click rate, unsubscribe rate
- Top performing email by clicks
- **Anomaly check:** Open rate < 15% or unsubscribe rate > 1%

## Anomaly Thresholds

| Metric | Warning | Critical |
|--------|---------|----------|
| Traffic WoW change | -20% | -40% |
| Ad CTR | < 0.8% | < 0.5% |
| Ad CPC vs avg | > 1.5x | > 2x |
| ROAS | < 2.0 | < 1.0 |
| Email open rate | < 18% | < 12% |
| Social engagement rate | -25% WoW | -50% WoW |
| GSC avg position (key terms) | +3 positions | +5 positions |
| Lead volume | -20% WoW | -40% WoW |
| Bounce rate | +8pp WoW | +15pp WoW |

When a threshold is breached, flag it prominently with a root cause hypothesis.

## Cross-Client Comparison (Multi-Project)

If multiple projects exist in `clients/`:
- Pull metrics for EACH project separately
- Compare performance patterns across clients
- Flag if one project significantly underperforms
- Note shared learnings (e.g., "carousel posts outperform single image across all 3 clients")

## Skill/Agent Usage Analytics

Run: `~/.claude/analytics/report.sh pareto 7d`

Include:
- Most-used skills and agents this week
- Any skills invoked but with no shipped output (research without execution)

## Knowledge Hygiene Check

Run freshness audit as part of review:
```bash
python3 skills/knowledge-hygiene/scripts/freshness_audit.py --summary
```

Surface as 1-2 lines:
- Docs overdue for update
- Skills with unintegrated learnings
- If clean: "Hygiene: All clean."

## Report Template

```markdown
# Weekly Marketing Review: [YYMMDD]
**Period:** [start] - [end] | **Projects:** [list]

## Dashboard
| Metric | This Week | Last Week | Change | Status |
|--------|-----------|-----------|--------|--------|
| Sessions | [N] | [N] | [+/-X%] | [OK/WARN/CRIT] |
| Leads | [N] | [N] | [+/-X%] | [OK/WARN/CRIT] |
| Ad Spend | $[N] | $[N] | [+/-X%] | [OK/WARN/CRIT] |
| ROAS | [X] | [X] | [+/-X%] | [OK/WARN/CRIT] |
| Social Engagement | [N] | [N] | [+/-X%] | [OK/WARN/CRIT] |
| Email Open Rate | [X%] | [X%] | [+/-Xpp] | [OK/WARN/CRIT] |

## Anomalies
- **[WARN]** [metric] -- [what happened] -- [root cause hypothesis]
- **[CRIT]** [metric] -- [what happened] -- [recommended action]

## Wins
- [Top performing content/ad/email with specific numbers]
- [New keyword rankings or traffic gains]

## Channel Performance
### Paid
[Key metrics, top ads, spend efficiency]
### Organic (SEO)
[Ranking changes, content performance, GSC highlights]
### Social
[Platform breakdown, top post, engagement trends]
### Email
[Sequence performance, list growth]

## Action Items (Prioritized)
1. **[HIGH]** [Specific action] -- [why, linked to data] -- [owner]
2. **[HIGH]** [Specific action] -- [why] -- [owner]
3. **[MED]** [Specific action] -- [why] -- [owner]
4. **[LOW]** [Specific action] -- [why] -- [owner]

## Cross-Client Patterns
[Only if multi-project -- shared insights]

## Hygiene
[1-2 lines from knowledge hygiene check]

## Data Sources
- [x] Meta Ads | [ ] GA | [x] GSC | [x] Postiz | [ ] HubSpot

## Unresolved Questions
- [Data gaps, metrics needing deeper investigation]
```

## Action Item Format

Every action item must have:
1. **Priority level** (HIGH/MED/LOW)
2. **Specific action** ("Refresh ad creative for [campaign]" not "improve ads")
3. **Rationale** (linked to data -- "CTR dropped 40% WoW")
4. **Owner** (which agent/skill, or "Jerel" if HITL required)

## Data Reliability
- NEVER fabricate metrics. Every number from an MCP or marked as estimated.
- If MCP unavailable: "Not available -- [MCP name] not configured"
- State data source for each metric section
