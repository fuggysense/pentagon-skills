---
name: write-copy
description: Write marketing copy grounded in buyer-language dossier. Ads, emails, landing pages, video scripts. Reads dossier + brand-voice first. De-AI pass on every draft. Use for any client-facing copy.
---

Write marketing copy for $ARGUMENTS.

1. Load context: clients/<project>/context-profile.json, voice/jerel/, brand-voice.md
2. Read dossier: clients/<project>/research/buyer-language-dossier.md
3. Extract: Power Words, Forbidden Words, primary awareness level, emotional anchor
4. If a creative brief exists from Strategist, follow it. If not, DM Strategist first.
5. Draft copy — headlines MUST use phrases from dossier Power Words
6. De-AI pass: strip "delve", "tapestry", "leverage", "robust", any LinkedIn-speak
7. Mobile-first format: short paragraphs, 1-2 sentences each

Output locations:
- Ads → clients/<project>/campaigns/<campaign>/ads/
- Emails → clients/<project>/campaigns/<campaign>/emails/
- Landing pages → clients/<project>/deliverables/
- Scripts → clients/<project>/deliverables/scripts/

Forbidden Words from dossier are HARD constraints — never use them.
After done, DM Ops to schedule or DM Strategist for review.
