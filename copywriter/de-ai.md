---
name: de-ai
description: Strip AI patterns from any draft. 4-layer detection stack — domain profiles, universal prohibitions, session corrections, voice target. Run on EVERY piece of copy before delivery.
---

# De-AI: 4-Layer AI Pattern Detection & Removal

Run this on every draft before delivery. No exceptions. If it sounds like AI wrote it, it doesn't ship.

Use $ARGUMENTS as the text to de-AI, or a file path to read.

## The 4-Layer Stack

```
Layer 1: Unslop profile      (domain-specific, soft constraints)
Layer 2: overused-ai-patterns (universal, HARD constraints)
Layer 3: corrections.md       (user-accumulated, HARD constraints)
Layer 4: V.O.I.C.E.           (positive voice target — sound like THIS)
```

Layers 1-3 = "avoid this." Layer 4 = "sound like this instead."
Priority: corrections.md > overused-ai-patterns > unslop > voice target.

## Layer 1: Domain-Specific Profiles

Check `skills/unslop/profiles/` for a matching profile:
- `linkedin-posts.md` — for LinkedIn content
- `video-scripts.md` — for video scripts
- `email-sequences.md` — for email drips

These are SOFT constraints (prefer to avoid, not absolute ban).

## Layer 2: Universal Prohibitions (HARD — never use these)

### Prohibited Words

**Transition words:** Moreover, Furthermore, However (sentence-start), Therefore, Additionally, Consequently, Nonetheless, Indeed, Thus, Notably

**Overused descriptors:** Essentially, Vibrant, Bustling, Labyrinthine, Gossamer

**Poetic/literary:** Underscores, Landscape (abstract), Tapestry (abstract), Soul (abstract), Crucible, Nestled, Symphony (abstract), Metamorphosis, Indelible

**Action verbs:** Elevate, Reverberate, Enhance, Delve, Revolutionize, Foster

**Business jargon:** Leverage, Synergy, Scalable, Streamline, Optimize, Empower, Innovative, Disruptive, Robust, Seamless, Holistic, Agile, Dynamic, Frictionless, Ecosystem, Bandwidth, Touchpoint, Granular, Alignment, Ideation, Deliverables, Stakeholder, Framework, Siloed

**Marketing buzzwords:** Cutting-edge, Next-generation, Best-in-class, Data-driven, Thought leadership, Paradigm shift, Game-changer, Low-hanging fruit, Deep dive, Move the needle, Actionable insights, Pain point, Quick win

### Prohibited Rhetorical Constructions

**Elliptical setup:** "The best part? You don't lift a finger." → State the point directly.

**Revelation hook:** "Here's the truth no one is talking about..." → Present information directly.

**Big contrast:** "It's not automation—it's amplification." → State the positive directly.

**Great reframe:** "Everyone's chasing attention—few are earning trust." → Single coherent thought.

**Philosophical reduction:** "AI isn't replacing people—it's replacing waiting." → Describe directly without paradox.

### Prohibited Expressions

**Verbose:** "As a result" → so. "In order to" → to. "It depends on" → depends. "You may want to" → you can.

**Academic:** "It's important to note" → DELETE. "In summary" → DELETE. "It's worth noting that" → DELETE.

**Clichéd:** "Dive into" → explore. "In today's digital era" → today. "A testament to" → proof of.

### Prohibited Structural Patterns

**"It's not X, but Y"** — State Y directly. Don't negate X first.

**Em-dash overuse** — Use periods, commas, or colons. Not dashes.

**Performative emphasis:** "Plot twist:" / "Full stop." / "Let that sink in." / "Here's the kicker" → DELETE all. Let content speak.

**Vague declaratives:** "The implications are significant" → Name the implications. "The stakes are high" → Specify what's at risk.

**False agency:** "The data tells us" → "We found." "The market demands" → "Buyers want."

**Negative listing:** "Not speed. Not scale. Not price. It's trust." → "Trust matters more than speed, scale, or price."

**Dramatic fragmentation:** "Community. That's it." → "The answer is community."

**Three-item lists as default** — Vary count. Use 2, 4, 5. If exactly 3, check if pattern or reality.

## Content Patterns to Detect & Fix

### 1. Puffery
Does the text inflate the importance of mundane details? "This serves as a testament to..." → Cut it.

### 2. Shallow Analysis via "-ing" Phrases
Participle phrases doing analytical work they can't do. "highlighting the collaborative nature of..." → State the insight directly or cut.

### 3. Promotional Tone
Would this sound at home in a press release? If yes, rewrite in conversational tone.

### 4. Elegant Variation
Unnecessary synonym cycling: "the protagonist" → "the key player" → "the eponymous character." Use the actual name.

### 5. Rule of Three
Triads padding thin observations: "adjective, adjective, and adjective." Break the pattern.

### 6. False Ranges
"From problem-solving to artistic expression" — endpoints loosely related, no real scale. Cut.

### 7. Copulatives Avoidance
"Serves as" → "is." "Features" → "has." "Stands as" → "is."

## The De-AI Checklist (Run on Every Draft)

1. [ ] Count flagged AI words — more than 3 in a short piece = rewrite
2. [ ] Check for "-ing" phrases doing analytical work → cut or rewrite
3. [ ] Check for promotional tone → rewrite conversationally
4. [ ] Check for elegant variation → use the actual term
5. [ ] Check for rule-of-three padding → vary list lengths
6. [ ] Check for em-dash overuse → replace with periods/commas
7. [ ] Check for bold overuse → use sparingly
8. [ ] Check for "It's important to note" and similar disclaimers → delete
9. [ ] Check for section summaries → delete "In conclusion" / "Overall"
10. [ ] Read aloud — does it sound like a LinkedIn influencer? → rewrite
11. [ ] Check against client's forbidden words (from dossier) → replace
12. [ ] Check against corrections.md → apply all accumulated fixes

## The Master Fix

Write with specificity. Use plain words. Say "is" not "serves as." Cut any sentence that analyzes significance without adding information. Prefer short, direct constructions over balanced parallelisms. Let facts speak without editorial inflation.

## Output

Return the de-AI'd text with a change summary:
- Words replaced: [count]
- Constructions fixed: [count]
- Sentences cut: [count]
- Worst offenders: [top 3 patterns found]
