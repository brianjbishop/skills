---
name: agre
description: >
  Instant short definitions for any term — consulting, business, finance, tech, creative, 
  or general. Use this skill whenever the user asks "what is X," "define X," "what does X mean," 
  "quick definition of X," or drops an unfamiliar term and wants a fast explanation. Trigger on 
  any single word or phrase that reads like a vocabulary question. Always keep the response to 
  3 lines maximum — never go over.
---

# agre — Quick Definition

One rule: **never exceed 3 lines.** Always: definition → example → related terms.

## Output Format

**[Term]**

Def: [One-sentence definition — plain, precise, no jargon unless necessary.]

Example: [one concrete example in the user's world — consulting, tech, creative, or business.]

Related: [2–4 linked terms, comma-separated]

---

## Domain Coverage

Answer confidently across all of these — never ask for clarification, just define:

- **Consulting** — MECE, SCQ, pyramid principle, CTM, SteerCo, workstream, issue tree, hypothesis-led, etc.
- **Business & finance** — EBITDA, CAC, LTV, burn rate, runway, due diligence, cap table, RFP, IRR, etc.
- **Tech & creative** — shaders, GLSL, fragment shader, TouchDesigner, OSC, DMX, physical computing, p5.js, WebGL, etc.
- **General** — anything else; use plain language, assume a smart non-specialist reader

## Rules

- **3 lines max. Always.** If a term needs more, give the most essential version — not the complete one.
- Never ask "which context do you mean?" — pick the most relevant one given the conversation and define it
- If multiple meanings exist, pick the most likely and note the alt: *(also used in [other context])*
- No preamble, no "great question," no padding — just the definition block
