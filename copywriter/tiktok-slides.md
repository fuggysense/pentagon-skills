---
name: tiktok-slides
description: Create TikTok Photo Mode carousels — 3:4 specs, multi-layer prompt architecture, slide narrative flows, batch generation, cross-slide consistency, and story continuity tracking.
---

Story-driven TikTok Photo Mode carousels with cross-slide consistency, brand-aware prompts, and batch generation.

Use $ARGUMENTS for the project name, batch number, content pillars, or specific request.

## Step 0: Load Client Context (MANDATORY)

Load ALL of these from `clients/<project>/` before writing a single prompt:

| File | What it gives you | Required |
|------|-------------------|----------|
| `brand-voice.md` | Voice, tone, terminology | Yes |
| `offer.md` | Product, value prop, differentiators | Yes |
| `visual-style-guide.md` | Visual DNA, mood, photography style | Yes |
| `typography.md` | Font hierarchy, color pairings, AI text rendering | Yes |
| `assets/brand-colors.md` | Hex codes, usage rules | Yes |
| `story-bank.md` | Real narratives (not made-up) | Yes |
| `icp.md` | Audience, what they care about | Yes |
| `campaigns/<campaign>/content-strategy.md` | Content pillars | If available |

If `visual-style-guide.md` or `typography.md` don't exist, create them first using AURA templates.

## TikTok Photo Mode Design Rules

### Aspect Ratio
- ALWAYS 3:4 (1080x1440) -- TikTok Photo Mode native
- NEVER 9:16 (that's for video), NEVER 1:1 or 4:5

### Text Placement
- Upper 1/3 of frame ONLY (rule of thirds)
- Bottom blocked by TikTok caption bar, buttons, profile icon
- NEVER place text in bottom 40%

### Consistency Rules
- Same text size, style, placement on every slide within a post
- Same color palette across all slides in a set
- Same layout grid (margins, padding, alignment)
- Every post needs a CTA on the final slide
- Clean > clever -- professional consistency beats creative chaos

## Prompt Architecture (4 Layers + Negative)

### Layer 1: Brand Context (same for entire batch)
```
BRAND CONTEXT: [1-2 sentence brand identity from offer.md]. Visual personality: [from visual-style-guide.md]. Audience: [from icp.md]. Voice: [key traits from brand-voice.md].
```

### Layer 2: Style Anchor (same for all slides in ONE post)
```
STYLE ANCHOR: Background: [hex + description]. Photography: [style]. Color grading: [warm/cool/neutral]. Lighting: [type]. Text treatment: [font style, placement, color]. Negative space: [how much]. All slides in this post use this exact same visual system.
```

### Layer 3: Slide Narrative (unique per slide)
```
SLIDE [N] of [total] -- Role: [hook/build/tension/reveal/CTA].
Story so far: [what previous slides established].
This slide: [what happens here, how it advances narrative].
Next slide will: [what comes after, so this slide sets it up].
```

### Layer 4: Visual Description (the actual image)
```
VISUAL: [Detailed composition, subjects, text overlays, colors, textures]. Aspect: 3:4 portrait (1080x1440).

TEXT OVERLAY: "[exact words -- 3-7 words max, lowercase preferred, no exclamation marks]"
TEXT RULES: Text in upper 1/3 only. One message per slide. Period at end for emphasis.

TYPOGRAPHY: [From client typography.md -- font style, weight, size, color hex per background]
```

### Layer 4b: CTA Slide Template (same for all posts in batch)
```
CTA TEMPLATE: [light bg hex] background. "[CTA text]" in [dark text hex], centered, [font style]. Brand wordmark in [grey hex] below. Thin [accent hex] line between. Clean, minimal, generous white space. Visually identical across all posts.
```

### Layer 5: Negative Prompt (same for entire batch)
```
NEGATIVE: [from visual-style-guide.md]
```

**Assembled prompt = Layer 1 + Layer 2 + Layer 3 + Layer 4 + Layer 5**

## Slide Narrative Flow Patterns

### Pattern A: Hook > Tension > Reveal > CTA
Best for: filter posts, comparisons, "we rejected X"
1. Hook: bold claim/question, dark bg, curiosity
2. Build (1-3 slides): evidence, details, tension
3. Reveal: the payoff, strongest visual moment
4. CTA: light bg switch, clean, brand wordmark

### Pattern B: Timeline
Best for: try-on demos, then vs now, building in public
1. Past: problem state, desaturated, cold
2. Present: current frustration, slightly warmer
3. Future: product solution, warm, glowing
4. CTA: clean light bg

### Pattern C: Mood Board / Style DNA
Best for: archetype reveals, style quizzes, aesthetic posts
1. Title: archetype name + teaser image
2. Mood board (1-2): collage of textures, items, colors
3. Personality: text about what this style means
4. Brand list: names (not logos)
5. CTA: quiz link

### Pattern D: Progression
Best for: try-on sequences, outfit comparisons
1. Setup: context frame
2. Options (2-3): sequential reveals, building momentum
3. Winner: the chosen one
4. CTA: clean payoff

### Pattern E: Numbered Framework (highest save rate)
Best for: tip lists, cheat sheets, save-bait
1. Cover: "0X [Topic] Tips" with numbered promise, creator selfie bg
2. Steps (3-5): pill-badge number, 3-column icon grid, dark bg first then white flip
3. Reference card: ultra-dense cheat-sheet (drives saves)
4. CTA: "Save this + follow" dual-action

### Pattern F: Confession > Lessons (high trust)
Best for: credibility building, myth-busting
1. Cover: confession hook on red/dramatic bg
2. Reality check: before/after contrast
3. Lessons (3-5): unique photo + accent color, lesson label small caps
4. Synthesis: pure black, single aphorism
5. CTA: comment emoji trigger

### Pattern G: Alternating Rhythm (best for long sequences)
Best for: multi-step systems, workflow reveals
1. Cover: two-font headline (condensed sans + italic serif)
2. Problem: dark diagnostic slide
3. Steps: alternating light > dark > light > dark (visual pacing)
4. Synthesis: pure black text-only
5. CTA: bookmark icon + themed emoji trigger

## Batch Generation Workflow

### Phase 1: Context Loading
1. Load ALL client files from Step 0
2. Build Brand Context (Layer 1), Negative Prompt (Layer 5)
3. Load content pillars + story bank

### Phase 1.5: Pre-Batch Intelligence (MANDATORY for batch 2+)

**1.5a: Story Continuity** -- read `clients/<project>/campaigns/tiktok-slideshows/story-ledger.md`:
- Angles used 2+ times must rest 2 batches
- No pillar >40% or <15% across all batches
- Pay off open threads from previous batch
- Never repeat a hook within 3 batches
- New content must not contradict previous claims

**1.5b: Performance Review** -- pull Postiz analytics for previous batch, rank by engagement, identify top 3 / bottom 3, log to story ledger.

**1.5c: Competitor Scan** -- use ScrapeCreators API for TikTok/IG competitor profiles, categorize hooks, score power level, append outliers to hooks-db.

### Phase 2: Calendar + Copy
1. Build 2-week calendar: pillar, hook, slide count, story pattern per post
2. HITL gate: present calendar for review
3. Write slide-by-slide text + captions (load brand voice first)
4. Map each post to narrative flow pattern

### Phase 3: Prompt Construction
1. Write Style Anchor (Layer 2) per post
2. Write Slide Narrative (Layer 3) per slide
3. Write Visual Description (Layer 4) per slide with typography from `typography.md`
4. Assemble all layers into complete prompts
5. HITL gate: present all prompts grouped by post

### Phase 4: Image Generation
NEVER generate standalone scripts. Use `scripts/generate_batch.py` with JSON manifest.
```bash
python skills/tiktok-slideshows/scripts/generate_batch.py manifest.json -o <output-dir>
python skills/tiktok-slideshows/scripts/generate_batch.py manifest.json --dry-run
python skills/tiktok-slideshows/scripts/generate_batch.py manifest.json -o output/ --retry-failed
```

### Phase 5: Assembly + Publishing
1. Review images in post groups (does each post flow as story?)
2. Adjust text in Canva using `typography.md` if needed
3. Select trending music in TikTok app
4. Upload as Photo Mode, schedule via Postiz

### Phase 5.5: Ledger Update (MANDATORY)
Update `story-ledger.md`: batch log, pillar usage, hooks used, exhausted angles, key claims, CTAs used, narrative arc tracker, archetypes covered.

### Phase 6: Winner Recreation (after 7+ days)
Pull analytics, rank by engagement + saves. For top 3: analyze why, generate variations. Options: repost exact (TikTok rewards this), variation for next batch, repurpose to IG carousel (resize 3:4 to 4:5).

## Quality Checklist

### Per Slide
- [ ] 3:4 (1080x1440)
- [ ] Text in upper 1/3
- [ ] Colors from brand palette only
- [ ] No pure black or pure white
- [ ] Text legible at phone screen size
- [ ] Matches style anchor
- [ ] Advances narrative (not standalone)

### Per Post
- [ ] 6-9 slides (never exceed 9)
- [ ] Complete micro-story
- [ ] Slide 1 = strong hook (two-font cover: condensed sans + italic serif)
- [ ] Penultimate slide = pure black synthesis (text-only, philosophical)
- [ ] Final slide = CTA with bookmark icon + themed comment emoji
- [ ] Visual consistency across all slides
- [ ] Caption <= 2200 chars + 3-5 hashtags
- [ ] At least 1 background pattern interrupt (dark>light flip or colored bg)

### Per Batch
- [ ] All client context files loaded
- [ ] Brand context block consistent
- [ ] Style anchors reference visual-style-guide.md
- [ ] Typography follows typography.md
- [ ] Negative prompt from visual-style-guide.md

## Cross-Slide Consistency Checklist

**Within a post:**
- Same background tone, text position, font treatment, photography style, borders/margins
- Narrative flows (each slide builds on previous)
- CTA slide uses light bg

**Across posts in batch:**
- Posts in same pillar share visual system
- All CTA slides visually identical
- Same negative prompt and brand context

## Learnings
- Gemini 3.1 Flash renders text well at 3:4
- 3:4 is correct TikTok Photo Mode ratio; 9:16 causes cropping
- Standalone prompts produce inconsistent slides; multi-layer prompts fix this
- Style anchor + slide narrative layers = cross-slide consistency
- Brand context in every prompt prevents generic output
- 3 API keys with round-robin = 3x throughput
