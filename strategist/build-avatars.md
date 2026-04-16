---
name: build-avatars
description: Build 3+ distinct advertising avatars per project for DCT targeting with 12-point psychological breakdown
---

# Avatar Research — Build DCT Targeting Avatars

Build 3+ distinct advertising avatars from buyer psychology. Each avatar is a targetable sub-segment with its own awareness level, sophistication level, emotional entry point, and messaging strategy. Feeds directly into ad-concepts for DCT batch generation.

**Input:** $ARGUMENTS (project name or context)

---

## Prerequisites

**Required:** ICP (demographics + buying behavior), Offer (what we sell + proof elements)
**Recommended:** Buyer profile (deep psychology — emotions, fears, Schwartz map)

**Foundation flexibility:** If buyer-profile doesn't exist but ICP contains deep psychology (emotions, fears, Schwartz map, relationship impacts, past solutions), use ICP as foundation. Map:
- Core Problem -> Avatar "Day-to-Day Struggles"
- Top 5 Emotions -> Avatar "Primary Emotion"
- Top 5 Fears -> "Beliefs We Must Overcome"
- Relationship Impacts -> "Day-to-Day Struggles" + "Image They Project"
- Past Solutions Tried -> "Other Solutions Tried" + "Why Those Failed"
- Schwartz Awareness Level Map -> "Market Awareness"

If NEITHER buyer-profile NOR rich ICP exists, build buyer profile first.

---

## Process: 4 Phases + 2 HITL Gates

### Phase 0: Context Load

1. Load: buyer-profile, icp, offer, brand-voice, story-bank
2. Check if avatars already exist — if <60 days old, offer refresh/extend/skip
3. Flag gaps in foundation files

### Phase 1: Avatar Hypothesis Generation

Segment using these axes:
- **Schwartz awareness level** — Unaware behaves differently from Solution-Aware
- **Market sophistication** — L2 never-seen-ads vs L4 been-burned
- **Primary emotion** — fear-driven vs aspiration-driven vs confusion-driven
- **Life stage trigger** — what event pushed them to act NOW
- **Failed solution history** — what they tried, how it shapes skepticism
- **Cultural/values segment** — religious considerations, family structure, community identity

Generate 4-6 hypotheses:

```
| # | Working Name | Awareness | Soph | Primary Emotion | What Makes Them Different |
|---|-------------|-----------|------|-----------------|--------------------------|
| 1 | "The ..." | Problem-Aware | L3 | Fear of... | They've tried X and failed... |
```

**HITL Gate 1:** User selects 3+ to develop. Can merge, rename, suggest new segments.

### Phase 1.5: Sales Copy Extraction (Optional)

If existing sales copy/landing pages exist, extract buyer psychology:

| Element | What to Look For |
|---------|-----------------|
| Demographics | Who addressed? Age, career, income signals |
| Core Problem | Emotional + situational challenge named/implied |
| Emotions Triggered | Feelings validated or agitated |
| Fears Invoked | Worst-case scenarios, "if you don't act" |
| Relationship Impacts | How problem affects family, work, social |
| Past Solutions Referenced | "You've tried X but..." language |
| Resistances Addressed | Objections preemptively handled |
| Transformation Promised | "After" state described |
| Language Patterns | Exact phrases, slang, emotional vocabulary |
| Proof Elements | Social proof, data, testimonials, guarantees |

Map each finding to the specific avatar it enriches. Copy extraction supplements but does NOT replace external research.

### Phase 2: External Research Prompts

For each selected avatar, generate **3 copy-paste-ready prompts**:

**Perplexity** (factual/data — cite sources): Real demographics, market data, competing products, pricing, regulatory context.

**Grok** (social sentiment — X/Reddit): What real people say, language used, frustrations, beliefs/objections, solutions mentioned.

**ChatGPT** (synthesis): Take buyer-profile excerpt, generate full 12-point breakdown for this sub-segment. Deeper psychological analysis.

Each prompt includes: product context, market/geography, avatar description, relevant buyer-profile excerpt, exact 12-point structure to fill.

User runs prompts externally, pastes results back.

### Phase 2.5: Market Sophistication Audit

Research what marketing messages each avatar has ALREADY been exposed to. Getting sophistication wrong = writing ads that talk down to cynical buyers or over-complicate for fresh audiences.

For each avatar, generate Perplexity + Grok prompts asking about:
- Competing ads running now (brands, headlines, visual styles)
- Common marketing claims in circulation (top 10)
- Seminars/webinars/events in the space
- Content marketing saturation (crowded or sparse?)
- Claims debunked on forums
- Ad formats they scroll past / mock

Assign sophistication level WITH evidence:

```
## Sophistication Assessment — Avatar [N]: [Name]
### Level: L[1-5]
### Evidence: [X] competing brands, [X] common claims, [X] rejected claims
### What still breaks through: [specific approaches]
### Creative strategy: Lead with [X], support with [Y], never lead with [Z]
```

Output: sophistication-map with cross-avatar matrix.

### Phase 3: Avatar Compilation

Compile into standardized format per avatar:

```markdown
# Avatar [N]: [Name]
> [One-sentence: who they are and why they're distinct]

## Quick Reference
| Field | Value |
|-------|-------|
| Awareness Level | [Schwartz] |
| Sophistication Level | [1-5] |
| Primary Emotion | [from buyer mapping] |
| Primary Fear | [from buyer mapping] |
| Buying Trigger | [event pushing action] |
| Ad Entry Point | [ad type that reaches them] |

## 12-Point Breakdown

### 1. Demographics
[Age, gender, location, income — specific to THIS sub-segment]

### 2. Day-to-Day Struggles
[Concrete daily reality. Specific behaviors, thoughts, routines.]

### 3. Image They Project
[Public persona they maintain]

### 4. Status They Aspire To
[Concrete status goal — specific material and social markers]

### 5. How Our Product Helps Them Achieve Status
[Mechanism linking product to THEIR status aspiration]

### 6. Beliefs We Must Overcome
1. "[Belief]" — Counter: [evidence or reframe]
2. "[Belief]" — Counter: [evidence or reframe]
3. "[Belief]" — Counter: [evidence or reframe]

### 7. Other Solutions Tried
### 8. Why Those Failed
### 9. Similar Products Considered
### 10. Why Those Fell Short

### 11. Market Awareness (Schwartz)
**Level:** [Unaware / Problem-Aware / Solution-Aware / Product-Aware / Most Aware]
**Evidence:** [why this level]
**Ad implication:** [hook type required]

### 12. Market Sophistication
**Level:** [1-5]
**Evidence:** [competing messages seen, cynicism level]
**Ad implication:** [creative approach that breaks through]

## Messaging Guidance (for ad-concepts)
- **Best Angle Types:** [story, fear-validation, contrarian, data-led...]
- **Language to Use:** [phrases from research]
- **Language to Avoid:** [triggers, loaded terms]
- **Proof Elements That Resonate:** [which case studies/data hit hardest]
- **Buying Emotion:** Not "[surface desire]" but "[deeper trigger]"
- **How to Position:** [specific framing that converts]
```

**Quality checks:**
- Flag sections where research was thin
- Cross-check demographics against ICP
- Verify Schwartz level matches evidence
- Ensure each avatar is GENUINELY DISTINCT (different awareness, emotion, entry point)

**HITL Gate 2:** Present all avatars side by side. Show quick reference + how each differs. User approves/edits/merges/splits.

### Phase 4: Save + Index

Write avatar files + index with summary table:

| # | Name | Awareness | Soph | Primary Emotion | Buying Trigger |
|---|------|-----------|------|-----------------|---------------|

---

## Distinctness Criteria

Avatars MUST differ on at least 2 of these axes:
1. Awareness level (Schwartz)
2. Sophistication level (1-5)
3. Primary emotion
4. Life stage trigger
5. Cultural/values segment

If two avatars share the same awareness AND emotion AND trigger, they're not distinct enough — merge or re-segment.

---

## Pipeline

```
ICP + Offer (foundation)
    |
Buyer Profile (deep psychology, optional)
    |
Avatar Research -> 3+ avatars with 12-point breakdown
    |
Ad Concept Engine -> DCT batches per avatar
```

Refresh cadence: every 60 days, or when campaign results show an avatar underperforming.
