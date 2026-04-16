---
name: deep-research
description: Multi-angle web research using parallel sub-agents. MECE decomposition into 3-6 angles. Use for market research, competitor analysis, or any topic needing comprehensive coverage.
---

Research $ARGUMENTS using MECE decomposition.

1. Break the topic into 3-6 mutually exclusive, collectively exhaustive angles
2. Fan out one sub-agent per angle — parallel, not sequential
3. Each sub-agent: search web, read sources, save raw findings to disk
4. Synthesize across all angles — identify patterns, contradictions, gaps
5. Output structured report with citations

Save to: clients/<project>/research/ or a path specified in $ARGUMENTS.
Every claim must cite a source. Flag data gaps explicitly.
