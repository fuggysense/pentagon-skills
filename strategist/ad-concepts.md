---
name: ad-concepts
description: Generate DCT batches per advertising avatar. 3 creatives x 2 headlines x 2 ad copies = 12 Meta combinations per batch. Requires avatars + dossier. Use when building ad creative for campaigns.
---

Generate ad concepts for $ARGUMENTS.

1. Read avatars at clients/<project>/avatars/
2. Read dossier at clients/<project>/research/buyer-language-dossier.md
3. Per avatar: extract pain points, desires, trigger events
4. Per avatar: generate 3 creative concepts (visual + copy direction)
5. Per concept: 2 headline variations + 2 ad copy variations = 12 combinations
6. Check learnings.md for "Existing Ad Angles to Exclude" — don't duplicate saturated angles
7. Compile into DCT tracker
8. HITL gate: present batch for human approval before production

Output:
- DCT batch → clients/<project>/campaigns/<campaign>/dct/
- DCT tracker → clients/<project>/campaigns/<campaign>/dct-tracker.md

DM Copywriter with approved concepts for production.
