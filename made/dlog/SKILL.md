---
name: dlog
description: >
  Narrative d.log writer for Brian. Transforms pasted AI conversation history
  and/or code diffs into a blog-ready devlog entry — capturing not just what
  changed, but why, and the thinking that led there. Output is a narrative intro
  followed by a structured breakdown of meaningful changes. Use this skill
  whenever Brian says "write a devlog", "document this session", "log what I
  built", "turn this into a blog post", "document my AI session", "write up
  what changed", "make this readable", or pastes a conversation/diff and wants
  it turned into something a human can follow. Also trigger when Brian says
  "devlog this" or drops a raw session and asks for a write-up. Always use
  this skill — do not summarize the session conversationally instead.
---

# d.log Skill

Brian works across code, hardware, audio, and creative tools — often with AI
as a collaborator. Sessions generate a lot of output but leave little trace of
the thinking behind decisions. This skill bridges that gap.

The goal: produce a devlog entry that reads like a clear, well-reasoned blog
post — useful for a public audience *and* as a personal record Brian can return
to months later.

---

## Inputs

Accept any combination of:
- **Pasted conversation history** (Claude, ChatGPT, Cursor, etc.)
- **Code diffs** (copy-pasted `git diff`, before/after snippets, or file chunks)
- **Both together**

Do not require clean input. Raw, messy, multi-turn sessions are the norm.

---

## Output Format

Two-part structure, always:

### Part 1 — Narrative Intro (3–5 paragraphs)
- Opens with what Brian was trying to accomplish — the *intent*, not the outcome
- Describes the arc of the session: what the problem was, how the thinking evolved, what got resolved (or didn't)
- Written in third person ("b. was working on...") or first person if Brian specifies
- Tone: warm, direct, technically curious — matches Brian's voice (see Voice section below)
- Should read like a blog post someone would actually want to read
- Does **not** recap every step — focuses on the meaningful turns

### Part 2 — Structured Breakdown
A sectioned changelog of meaningful changes. For each:

```
### [Change Title] — [one-line description of what changed]

**Why:** What problem this solved or goal this served
**What:** The actual change, explained briefly — assume reader knows the domain
  but define any specific tools/concepts on first mention
**Impact:** What this enables, unblocks, or changes downstream
```

Only include changes that represent a meaningful decision or shift — skip
housekeeping, minor fixes, or iterations that were just noise in the session.
Aim for 3–7 entries. If the session was exploratory with no firm output, say so
clearly in the intro and structure the breakdown around key learnings instead.

---

## Extraction Logic

When reading a conversation history, identify:
1. **The opening intent** — what did Brian ask for or try to do first?
2. **Pivots** — moments where direction changed, a constraint emerged, or the approach shifted
3. **Decisions** — places where a choice was made between options (even implicitly)
4. **Outcomes** — what actually got built, changed, or resolved by the end

When reading a diff, identify:
1. **What was removed or replaced** and why it was insufficient
2. **What was added** and what it enables
3. **Non-obvious structural choices** — naming, organization, abstraction level

Prioritize *why* over *what*. The code speaks for itself. The reasoning doesn't.

---

## Voice Guidelines

Brian's written voice:
- Concise and forward-moving — no over-explaining, trusts the reader
- Leads with observation, not framing ("The routing was wrong" not "I want to talk about routing")
- Em-dashes for connective asides — used sparingly
- Lists only the most compelling points, never exhaustive
- Collaboration front and center — names tools and collaborators (including AI) honestly
- Cuts defensiveness — if something didn't work, says so plainly and moves on
- Technical but not gatekeeping — defines domain terms briefly on first use

Do not:
- Use phrases like "In this devlog..." or "Today I worked on..."
- Over-explain context the reader can infer
- Pad the narrative with generic observations about AI or software development

---

## Optional Parameters

Brian can specify at the top of his request:
- `audience: [public / personal / technical]` — defaults to mixed (public-ish, explains concepts briefly)
- `project: [project name]` — used in the header and helps with tone
- `format: [narrative only / breakdown only / both]` — defaults to both
- `pov: [first / third]` — defaults to third person unless specified

---

## Output Header

Always open with:

```
## Devlog — [Project Name or inferred topic] · [Date if known, else omit]
```

---

## Edge Cases

**Session went in circles / nothing shipped:** Note this honestly in the intro.
Structure the breakdown as "Key Learnings" instead of changes. Dead ends have
narrative value — they're decisions too.

**Very short input:** If the session is brief (< 10 exchanges or a small diff),
produce a shorter entry — don't pad. One tight paragraph + 2–3 breakdown items
is fine.

**Sensitive or in-progress work:** If the content seems clearly unfinished or
experimental, add a brief note at the top: `[Draft — work in progress]`.

**Multiple projects in one session:** If the conversation spans clearly separate
work, split into two devlog entries with a horizontal rule between them.
