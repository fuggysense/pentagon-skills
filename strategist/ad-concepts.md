---
name: ad-concepts
description: Generate per-avatar DCT ad batches (3 creatives x 2 headlines x 2 copies = 12 Meta combinations each)
---

# Ad Concept Engine — DCT Mode

Generate per-avatar ad angles, assemble complete DCT batches, and compile a tracker for Meta dynamic creative testing.

**Input:** $ARGUMENTS (project name or context — avatars must exist before running this skill)

---

## DCT Batch Structure

Each batch contains:

| Component | Count | Rule |
|-----------|-------|------|
| Creatives | 3 | Each a DIFFERENT visual style. Text on image = standalone visual hook, NOT the Meta headline |
| Headlines | 2 | Different hooks for same angle. Max ~40 chars |
| Ad Copies | 2 | Different frameworks (PAS, story, data-led, contrarian, testimonial, etc.) |

Meta mixes all: 3 x 2 x 2 = **12 combinations per batch**.

### Visual Style Palette (no two in a batch share a style)
- Realistic photography (UGC selfie, editorial, documentary)
- Text-only bold graphic (dark bg, large typography)
- 3D / Claymation / Pixar-style illustration
- Split-screen before/after
- Infographic / data overlay on photo
- Screenshot / WhatsApp / social post aesthetic

### Text-on-Image Hooks
- 2-8 words, scroll-stopping
- Works standalone without reading Meta text fields
- DIFFERENT from both Meta headline and primary text
- One unique hook per creative

---

## Process: 5 Phases + 5 HITL Gates

### Phase 0: Context Load + Avatar Detection

1. Load: buyer-profile, offer, brand-voice, icp, story-bank
2. Detect avatars directory — if missing, run build-avatars first
3. **HITL Gate 0:** Present avatar index. Ask which avatars to target (2+ for meaningful testing)
4. Input existing ads. Extract angles already in use for dedup.

### Phase 0.5: Competitive Swipe File Check

Load existing swipe files if <60 days old. Use for:
- **Dedup** — flag angles competitors already run
- **Blue ocean gaps** — angles NO competitor addresses = priority targets
- **Structural patterns** — proven ad formats to adapt
- **Longevity signals** — ads running 3+ months = confirmed performers

### Phase 1: Angle Generation (Per Avatar)

For EACH selected avatar, load:
- 12-point breakdown + messaging guidance
- Sophistication map (creative strategy per level)
- Swipe file patterns + existing ads exclusion list

**Generate 6-8 angles per avatar.** Score and present grouped:

```
## Avatar 1: [Name] (Awareness: [Level], Soph: L[N])

| Rank | Angle | Psych Trigger | Score |
|------|-------|---------------|-------|
| 1    | ...   | ...           | 9.2   |
```

**HITL Gate 1:** User picks top 2 angles per avatar. Can reject/replace/rerank/move angles between avatars.

After approval: 2 angles x N avatars = batch list. Name: DCT001, DCT002, etc.

### Phase 2: DCT Batch Assembly

For each approved angle, generate the complete batch:

#### Headlines (2 per batch)
- Max ~40 chars, UK English
- Sophistication-driven structure:
  - L1-L2: Lead with claim or enlarged claim
  - L3: Lead with named mechanism
  - L4: Lead with identification/mirror (their exact situation)
  - L5: Ultra-specific insider language

#### Ad Copy (2 per batch)
- Max ~125 chars above fold (Meta primary text)
- Framework selection MUST match sophistication:

| Soph | Preferred Frameworks | Avoid |
|------|---------------------|-------|
| L1-L2 | PAS, Data-led, Story | Contrarian |
| L3 | Story (mechanism reveal), Data-led | Pure claim |
| L4 | Fear-validation, Question-driven, Contrarian, Permission-granting | PAS, Data-led alone |
| L5 | Story (peer voice), Permission-granting | Anything that reads like "ad copy" |

- CTA pressure by sophistication:
  - L1-L2: Direct ("Take the free assessment")
  - L3: Mechanism-led ("See your 3 numbers in 2 minutes")
  - L4: Low-pressure ("No agent call. No obligation. Just clarity.")
  - L5: Whisper ("When you're ready.") or no explicit CTA

#### Image Concepts + Text-on-Image Hooks (3 per batch)
- 3 creatives, each COMPLETELY DIFFERENT visual style
- Visual style by sophistication:
  - L1-L2: Product/lifestyle, bold claims on image
  - L3: Mechanism/process visuals, infographics
  - L4: UGC-style, raw/authentic, text-on-dark, WhatsApp aesthetic
  - L5: Pure UGC, meme format, screenshot aesthetic
- Text-on-image hooks by sophistication:
  - L1-L2: Claim or benefit
  - L3: Mechanism tease
  - L4: Identification question or statement
  - L5: Insider language / colloquial

**HITL Gate 2:** Present each batch as card:

```
### DCT001 — Avatar: [Name] | Angle: [Title]
**Awareness:** [Level] | **Sophistication:** L[N]

| Component | Variant A | Variant B |
|-----------|-----------|-----------|
| Headline  | "[H1]" | "[H2]" |
| Ad Copy   | [Framework]: "[Copy A]" | [Framework]: "[Copy B]" |

**Creative 1** ([Style]): [Desc] | Hook: "[text-on-image]"
**Creative 2** ([Style]): [Desc] | Hook: "[text-on-image]"
**Creative 3** ([Style]): [Desc] | Hook: "[text-on-image]"

Combinations: 12 | Est. cost: $0.20
```

### Phase 3: Image Generation

Execute approved image prompts. Save to campaign directory.

**HITL Gate 3:** Show generated images grouped by batch. Approve or regenerate.

### Phase 4: DCT Tracker Compilation

```markdown
# DCT Tracker — [Client] — [Date]

## Summary
- Avatars targeted: [N]
- DCT Batches: [N]
- Total combinations: [N x 12]
- Status: Ready for upload

## Batches
| Batch | Avatar | Awareness | Soph | Angle | H1 | H2 | Copy A | Copy B | Img 1 | Img 2 | Img 3 |
|-------|--------|-----------|------|-------|----|----|----|----|----|----|----|

## Performance (fill after launch)
| Batch | CTR | CVR | CPA | Spend | Winning Combo | Notes |
|-------|-----|-----|-----|-------|---------------|-------|

## Kill/Scale Decisions
[To be filled]
```

**HITL Gate 4:** Present complete tracker. Approve before upload.

---

## Corrections (Hard Rules)

- NO em-dashes in headlines — use full stops or commas
- NO "Here's the honest answer" — use "The honest answer" (flagged AI pattern)
- NO "The secret wealth" — use "The hidden wealth" (AI-adjacent)
- NEVER dismiss buyer fears as wrong — validate fears, then reframe (reads as gaslighting)
- "Mortgage" alienates devout Muslim audience — use "monthly commitment" or "financing" (riba prohibition)
- NO shaming anxious buyers — triggers defensiveness, not curiosity
- Agent brag angles ("22 years, 729 families") — retargeting only, not cold traffic

---

## Quality Standards

- UK English spelling throughout
- Anti-AI slop check on all copy
- Brand-voice compliance
- Dedup against existing angles before generating
- Distribute visual styles across batches (if DCT001 uses [realistic, text-only, claymation], DCT002 should use different combo)
- Rerun cadence: every 4-6 weeks or when creative fatigue detected
