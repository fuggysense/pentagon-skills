---
name: deep-research
description: Multi-agent parallel research orchestrator — MECE decomposition, 3-6 sub-agents, gap analysis, synthesized report
---

Multi-agent parallel research orchestrator. Decomposes any research topic into 3-6 specialized angles using MECE principles, spawns sub-agents in parallel, runs gap analysis, synthesizes into one comprehensive document. 90.2% better than single-agent research (Anthropic eval).

Use $ARGUMENTS as the research topic/question.

## When to Use

- "Deep research", "thorough research", "research everything about"
- Comprehensive coverage needed (not a quick lookup)
- Research document for strategic decisions
- Competitor deep dives, market analysis, technology evaluation
- Any task requiring 3+ web searches across different angles

NOT for: Quick lookups, single questions, fact checks.

## Architecture

```
     [Broad: Decompose question]
          /        \
[Narrow: 3-6 parallel agents]     <- Wave 1
          \        /
     [Evaluate: Gap analysis]
          /        \
[Deep: 1-2 targeted agents]       <- Wave 2 (if needed)
          \        /
     [Synthesize: Final report]
```

## Phase 1: Gather Context

Before spawning agents:

1. **Get today's date** — inject into every sub-agent prompt so they search current info.
2. **Clarify purpose** — "What will you use this research for?" The answer shapes everything.
3. **Ask about sources** — "Are there specific sources to prioritize?" Options: specific people/accounts, specific sites/communities, URLs to anchor around, or "no, use defaults."

## Phase 2: MECE Decomposition

Break the topic into **Mutually Exclusive, Collectively Exhaustive** angles. Each angle:
- Does NOT overlap with any other (prevents duplicate work)
- Together they cover everything relevant (no gaps)
- Is specific enough for one agent to investigate thoroughly

### Common Decomposition Patterns

| Research Type | Typical Angles |
|--------------|----------------|
| Market/Competitor | Market size + trends, Competitor landscape, Customer pain points, Pricing + business models |
| Content/Platform | Best practices, Niche-specific strategies, Real examples with metrics, Psychology/copywriting |
| Technology | Current state/ecosystem, Real code patterns, Community sentiment, Comparisons/alternatives |
| Business Strategy | Market data/benchmarks, Practitioner strategies, Competitive landscape, Community discourse |

### Scale to Complexity
- Simple factual: 3 agents
- Multi-faceted: 4-5 agents
- Complex strategic: 5-6 agents (hard cap — more = more overlap)

## Phase 3: Spawn Parallel Sub-Agents

Every sub-agent prompt MUST include these 6 elements:

1. **WHO** — who the research is for and what they do
2. **WHY** — the specific purpose
3. **WHAT ANGLE** — specific scope AND boundaries: "Cover X. Do NOT cover Y — another agent handles that."
4. **HOW** — which tools to use
5. **SEARCH STRATEGY** — "Start with SHORT, BROAD queries (2-4 words). Evaluate. Then progressively narrow."
6. **SOURCE QUALITY** — "Prefer: practitioner blogs, official docs, academic papers, primary sources. Avoid: SEO content farms, listicles."

### Sub-Agent Prompt Template

```
You are researching [ANGLE] for [USER CONTEXT].

TODAY'S DATE: [DATE]
PURPOSE: [WHY this research matters]
YOUR ANGLE: [SPECIFIC SCOPE]
BOUNDARIES: [What you do NOT cover — other agents handle those]

SEARCH STRATEGY:
- Start with short, broad queries (2-4 words)
- Evaluate, then progressively narrow
- Cross-reference claims across multiple sources
- Aim for 2+ independent sources per key finding

SOURCE QUALITY: Prefer practitioner blogs, official docs, engineering posts.
Avoid SEO content farms and listicles.

QUALITY BAR: Be exhaustive. Extract every actionable insight, specific number,
concrete example, framework, contrarian take. If you find only 3 bullet points, you failed.

OUTPUT FORMAT:
## Key Findings
[Numbered list with inline source citations]
## Evidence Quality
[Which findings are well-sourced vs. speculative]
## Contradictions Found
[Conflicting information between sources]
## Notable Quotes
[Direct quotes with attribution]
## Sources
[Full list with URLs]
```

## Phase 4: Gap Analysis

After ALL sub-agents return — process as a batch, not one at a time:

1. Review all findings together
2. Check: does each MECE angle have 2+ independent sources?
3. Identify contradictions between agent findings
4. Identify coverage gaps — topics no agent covered adequately
5. **If significant gaps**: spawn 1-2 targeted follow-up agents (Wave 2)

## Phase 5: Synthesize

Cross-reference all findings into ONE document. Do NOT concatenate — synthesize.

```markdown
# [Topic Name]

Research compiled [date]. [N] parallel tracks synthesized.
**Purpose**: [what this research will be used for]
**Sources**: [N] web sources, [N] code examples, etc.

---

## Executive Summary
[3-5 bullet points — most important findings]

---

## Part 1: [Angle Name]
### [Sub-topic]
[Dense, actionable content with specific numbers and examples]

---

## Contradictions & Open Questions
[Where sources disagreed, what remains unresolved]

---

## Key Takeaways
[Numbered list of most actionable insights]

---

## Sources
[All sources cited, organized by section]
```

### Quality Gate (ALL must pass before saving)
- Specific numbers present, not just generalities
- Concrete examples from real companies/creators
- Sources attributed throughout
- Contradictions flagged (not hidden)
- User would learn something genuinely new

## The 5 Pitfalls That Kill Quality

1. **Duplicate work** — without explicit "do NOT cover X" boundaries, agents overlap. MECE prevents this.
2. **Overly-specific queries** — agents default to long queries. Explicitly prompt "start broad, then narrow."
3. **SEO content farm results** — add source quality heuristics to every prompt.
4. **Anchoring bias** — if you read Agent 1 before Agent 2 returns, you filter through Agent 1's frame. Batch ALL results.
5. **"Good enough" stopping** — require 2+ sources per finding. One source = opinion. Two = pattern.

## External LLM Synthesis (Token-Saving)

Sub-agents can offload synthesis to cheaper models:

```bash
scripts/research-llm.sh auto "Synthesize these raw search findings...
RAW FINDINGS: [paste]
OUTPUT FORMAT: Key Findings, Evidence Quality, Sources"
```

| Provider | Model | Best For |
|----------|-------|----------|
| Kilo Gateway | minimax-m2.5 | General synthesis, cheapest |
| Kilo Gateway | nemotron-3-super | Complex synthesis |
| Gemini CLI | gemini-2.5-flash | Fallback |
| Auto | Kilo > Gemini | Set-and-forget |

Ask user which backend before spawning.

## Output

Save to: `docs/research/[topic-slug]-[YYYY-MM-DD].md`
