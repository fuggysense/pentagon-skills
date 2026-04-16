---
name: buyer-research
description: Mine buyer language from Reddit, YouTube, Trustpilot, DataForSEO, and sales transcripts. Produces buyer-language-dossier.md. Use when starting a new client, refreshing stale copy, or ingesting customer data.
---

Run a buyer-language research pipeline for $ARGUMENTS.

1. Load context: clients/$ARGUMENTS/icp.md, offer.md, brand-voice.md, learnings.md
2. Check clients/$ARGUMENTS/research/inputs/ for real customer data (objections.md, prospect-qa-*.md, transcripts/)
3. Check clients/$ARGUMENTS/swipe-file*.md for existing scraped quotes
4. Fan out parallel research: Reddit, YouTube comments, DataForSEO ("people also ask"), Trustpilot/G2
5. Save raw pulls to clients/$ARGUMENTS/research/raw/
6. Checkpoint: surface top 20 verbatim quotes — wait for human taste veto
7. Synthesize into dossier (9 sections, both Schwartz frameworks)

Output: clients/$ARGUMENTS/research/buyer-language-dossier.md

Rules:
- VERBATIM quotes only — no paraphrasing
- Minimum 15 pain, 10 outcome, 10 objection quotes with source attribution
- Real customer data (inputs/) overrides scraped data
- Map both Schwartz frameworks with evidence per level
- After completion, DM Copywriter + Strategist that dossier is ready
