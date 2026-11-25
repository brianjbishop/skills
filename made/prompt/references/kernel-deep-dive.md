# KERNEL Framework — Deep Dive Reference
Source: Prompt Polisher 3.0 System Instructions (prompt-v3.md)

---

## Overview

KERNEL is a proprietary framework for prompt engineering designed to:
- Minimize token usage (~70% reduction vs. verbose prompts)
- Boost first-try success rates
- Ensure model-agnostic consistency (works across GPT, Claude, Gemini, etc.)
- Make prompts reproducible over time

---

## The Six Principles in Detail

### K — Keep it Simple
**Goal:** Replace verbose context with one clear, focused goal.

**Before (violation):**
```
I'm working on a project for a client in the financial services industry where
they're trying to understand the competitive landscape, and I want you to help
me think through what their options are and what the key considerations might
be and also maybe what some competitors are doing...
```

**After (compliant):**
```
List 5 strategic options for a retail bank entering the wealth management market,
with one key risk per option.
```

**Why it matters:** LLMs perform better with focused, bounded tasks. Verbose prompts
split attention across too many sub-goals.

---

### E — Easy to Verify
**Goal:** Include clear, measurable success criteria so the output can be objectively evaluated.

**Non-verifiable (violation):**
- "Make it engaging"
- "Write it professionally"
- "Make it comprehensive"

**Verifiable (compliant):**
- "Include 3 code examples with comments"
- "Output exactly 5 bullet points, each under 15 words"
- "A 10-year-old should be able to understand the explanation"
- "Include at least one real company name as an example"

**Why it matters:** Without measurable criteria, you can't tell if the output is correct.
You'll iterate endlessly with subjective feedback.

---

### R — Reproducible Results
**Goal:** Avoid temporal references. Use specific versions, dates, and exact requirements
so the same prompt produces consistent results over time.

**Non-reproducible (violation):**
- "Summarize the current trends in..."
- "What are the latest developments in..."
- "What do people think about X today?"

**Reproducible (compliant):**
- "As of Q3 2024, summarize the three leading approaches to..."
- "Using the framework published by McKinsey in 2022..."
- "List the five largest EV manufacturers by market cap as of December 2023"

**Why it matters:** Temporal references cause inconsistent outputs as the model's
knowledge changes or as you run the prompt months later.

---

### N — Narrow Scope
**Goal:** One prompt = one goal. Never combine multiple complex tasks.

**Too broad (violation):**
```
Write a Python function to parse CSV data, add error handling, document it,
and also write unit tests and a README.
```

**Narrow (compliant):**
```
Write a Python function that accepts a CSV filepath and returns a list of dicts.
Handle FileNotFoundError and return an empty list. No other functionality.
```

**Why it matters:** Multi-goal prompts force the model to make tradeoffs. Each sub-task
competes for attention. Split complex work into sequential prompts.

**Sequencing pattern:**
1. Prompt 1: Write the core function
2. Prompt 2: Add error handling to [paste output from 1]
3. Prompt 3: Write unit tests for [paste output from 2]

---

### E — Explicit Constraints
**Goal:** Tell the AI exactly what NOT to do. Negative constraints are as important as
positive instructions.

**No constraints (violation):**
```
Explain machine learning to a business audience.
```

**Explicit constraints (compliant):**
```
Explain machine learning to a business audience.
DO NOT use technical jargon, mathematical notation, or mention specific algorithms.
DO NOT exceed 150 words.
DO NOT recommend any specific tools or vendors.
```

**Common constraint categories:**
- **Format exclusions:** "No bullet points", "No headers", "No markdown"
- **Content exclusions:** "No speculation", "No historical examples before 2020"
- **Scope exclusions:** "Focus only on B2C, not B2B"
- **Tone exclusions:** "Not academic", "Not casual"

**Why it matters:** Constraints reduce the model's solution space, dramatically
reducing unwanted outputs.

---

### L — Logical Structure
**Goal:** Format every prompt with a consistent architecture.

**The four-block structure:**

```
## Context
[Who is the user, what is the situation, what inputs exist]

## Task
[Single specific action — verb + object]

## Constraints
- DO: [requirements]
- DO NOT: [exclusions]
- Format: [output structure]
- Length: [specific count]
- Success criteria: [measurable verification]

## Format
[Exact output format: markdown, JSON, prose, table]
```

**Mapping to scoring dimensions:**
- Context block → scores "Context" dimension
- Task block → scores "Clarity" + "Narrow scope"
- Constraints block → scores "Instructions" + "Specificity"
- Format block → scores "Instructions"

---

## KERNEL Scoring Matrix

Use this when auditing a prompt:

| Principle | Violated | Compliant |
|-----------|----------|-----------|
| K — Simple | Multi-goal, verbose background | Single clear objective |
| E — Verifiable | "Make it good", vague quality | Specific count, measurable output |
| R — Reproducible | "Current", "latest", "today" | Specific date, version, reference |
| N — Narrow | 3+ tasks combined | Exactly one task |
| E — Constraints | No negative instructions | Explicit DO/DO NOT list |
| L — Structure | Free-form paragraph | Context/Task/Constraints/Format |

**Scoring gate:** Each violation caps the maximum achievable score:
- 1 violation: max 7/10
- 2 violations: max 6/10
- 3+ violations: max 5/10

---

## KERNEL vs. Traditional Prompting

| Aspect | Traditional | KERNEL |
|--------|-------------|--------|
| Length | Often long, detailed | Concise, focused |
| Success | "I'll know it when I see it" | Measurable criteria |
| Temporal | References current events | Specific versions/dates |
| Scope | Often bundled tasks | One task per prompt |
| Negatives | Implied | Explicit |
| Structure | Prose paragraph | 4-block architecture |

---

## Common KERNEL Anti-Patterns

**1. The "Context Dump"**
Providing paragraphs of background when only 1-2 sentences are needed.
Fix: Distill to the single most relevant context sentence.

**2. The "Vague Adjective"**
"Make it professional", "Keep it engaging", "Be comprehensive"
Fix: Define what "professional" looks like with a measurable criterion.

**3. The "Multi-Task Bundle"**
"Write X, then analyze it, then suggest improvements, then format it as Y"
Fix: Break into 4 sequential prompts.

**4. The "Moving Target"**
References to "current trends", "latest news", "what people are saying now"
Fix: Pin to a specific date or dataset.

**5. The "Implied Constraint"**
Assuming the model knows what you don't want (jargon, speculation, length bloat)
Fix: Write out every constraint explicitly.

---

## Quick Reference Card

```
KERNEL CHECKLIST

Before submitting any prompt, verify:
[ ] K: Is there ONE clear goal? Could it be simpler?
[ ] E: Is success measurable? How will I know it worked?
[ ] R: Are there any temporal references that could change?
[ ] N: Am I asking for more than one thing?
[ ] E: Have I listed what NOT to do?
[ ] L: Does it follow Context/Task/Constraints/Format?

If any box is unchecked, revise before submitting.
```
