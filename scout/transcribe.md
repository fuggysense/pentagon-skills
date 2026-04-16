---
name: transcribe
description: Parse sales call transcripts from Fathom/Gong exports. Extract objection moments, pain phrases, trigger events. Use when transcript files are dropped in research/inputs/transcripts/.
---

Parse transcript(s) at $ARGUMENTS.

1. Read the transcript file(s)
2. Identify and extract:
   - Objection moments (prospect pushes back, hesitates, says "but...")
   - Pain phrases (frustration, confusion, fear expressions)
   - Trigger events (what happened before they started looking)
   - Trusted voice references (who they mention listening to)
3. Output each as a verbatim quote with timestamp
4. Save to clients/<project>/research/raw/transcripts-extracted.md

Tag each quote: [objection], [pain], [trigger], [trusted-voice].
Preserve exact wording — do not clean up or paraphrase.
