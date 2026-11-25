---
name: brian-blog-voice
description: Draft or revise a post for Brian's 2b.log in his first-person, studio-notebook voice, artifact first, with process, pivots, lessons and exact prompts. Use when asked to write, edit or document a project as a 2b.log blog post.
---

> Use this skill when drafting or revising a post for Brian’s 2b.log. The goal is to sound like a working artist-technologist documenting what happened, not like a polished company case study.

## Voice

Write in **first person**, with a direct, curious, conversational tone. Brian’s posts often feel like a studio notebook made public: the idea, the attempt, what worked, what failed, and what he wants to try next.

- Prefer “I wanted to…,” “I tried…,” “I learned…,” and “this made me wonder…”
- Let excitement, uncertainty, and pivots remain visible.
- Use contractions, occasional parenthetical asides, and natural emphasis.
- Questions can carry the concept: “What if…?” or “How can…?”
- Keep the language grounded in the actual making process.
- Do not fake typos or force slang. Preserve Brian’s looseness without caricaturing it.
- Do not turn the post into marketing copy, an academic essay, or an executive summary.

## Length

Default to compact. Across the current corpus, the median post is roughly 140 words of prose, and some posts are primarily media. Do not pad a simple experiment into a long article.

Longer posts are appropriate when the work has multiple phases, collaborators, technical decisions, or a meaningful conceptual context.

## Default Shape

Start with the artifact or idea as quickly as possible. A strong default is:

1. A media block, embed, or short callout showing what the project is.
2. A brief first-person explanation of what Brian wanted to make and why.
3. The process, including failed attempts or pivots.
4. The output or current state.
5. Lessons and next steps.

Use only the sections the project actually needs. Common headings in Brian’s posts are:

- `What did I do?`
- `Process`
- `Inspo` or `Inspiration`
- `Output`
- `Lessons`
- `Next Steps`
- `Prompts`

Do not impose every heading on every post.

## Formatting

Brian’s posts are visual and artifact-led.

- Put images, videos, embeds, prototypes, and links close to the paragraph that explains them.
- Use a short callout near the top when a one- or two-sentence project description helps orient the reader.
- Use columns for related media when available.
- Use bullets and checklists for plans, feedback, technical steps, and unfinished work.
- Use toggles for raw process material, long prompts, dense documentation, and archives.
- Use dividers between major ideas or phases. Treat each divider as a potential slide break so the blog can also become a presentation (see `notion-presentation-style`). A presentation-ready post should place one clear idea, visual, question, or action between dividers, not several unrelated sections.
- Emojis are welcome when they add energy or navigation.
- Let code and media do some of the explaining; do not repeat everything in prose.

## Content Priorities

### For project documentation

Explain:

- what Brian wanted to make;
- the experience or question behind it;
- what he personally did;
- the tools and materials used;
- where the project changed direction;
- the current output;
- what he learned and what remains unfinished.

Credit collaborators clearly. Distinguish Brian’s role from the group’s work.

### For technical experiments

Move from intention to implementation.

- Start with the behavior Brian wanted.
- Explain the technical idea in plain language.
- Include the relevant code, prototype, or embed.
- Mention what did not work and the pivot it caused.
- End with what can be played with or developed next.

Do not over-explain standard concepts unless they were part of the learning.

### For reflective or conceptual posts

Begin from a lived observation, experience, or tension. Connect it to the larger idea without flattening the uncertainty. Brian often moves from a personal example to a speculative question rather than forcing a final conclusion.

### For event or production posts

Balance the public-facing description with Brian’s actual role and behind-the-scenes labor. Include logistics, fabrication, collaborators, feedback, and the conditions in which the work happened.

## Prompts

When a project used AI or an automation tool, include a `## Prompts` section when the original prompts are available.

1. Name each tool and link to it.
2. Reproduce the **actual prompt** without rewriting it.
3. Put every prompt in a fenced code block with the language set to `markdown`.
4. Label which tool and step the prompt belongs to.
5. Preserve iterations when they show how the result changed.
6. Never invent a missing prompt. Ask Brian for it or mark it as unavailable.

Example structure:

````markdown
## Prompts

### [Tool Name](https://example.com)

#### Initial setup

```markdown
Exact prompt goes here.
```
````

## Titles

Favor concise project names, evocative phrases, playful combinations, or a clear description of the experiment. Brian’s titles often work as names for artifacts rather than headlines optimized for clicks.

Avoid generic titles such as “My Project Journey” or exaggerated claims such as “How I Revolutionized…”

## What to Avoid

- Corporate case-study language: “The challenge,” “The solution,” “key takeaways,” “leveraged,” or “optimized,” unless Brian used it.
- A polished third-person biography tone.
- Overly neat narratives that erase uncertainty, failure, or unfinished work.
- Repeating numbers and summaries in several formats.
- Adding lessons Brian did not actually express.
- Inventing tools, prompts, collaborators, outcomes, or motivations.
- Treating every post as a tutorial.
- Writing a long introduction before showing the work.

## Drafting Workflow

1. Read the source material and identify the artifact, Brian’s role, the motivating idea, process evidence, output, lessons, and next steps.
2. Check a few relevant 2b.log posts, preferably from the same course or project type, for local structure and density.
3. Draft the shortest version that still explains what happened.
4. Add media, links, code, prompts, or process material where they do real explanatory work.
5. Re-read for voice. Replace polished abstractions with Brian’s concrete actions and observations.
6. Verify every factual claim, tool link, collaborator credit, and prompt.

## Final Check

Before publishing, confirm:

- Does the post sound like Brian explaining the work to a curious peer?
- Is the artifact visible or linked near the top?
- Is Brian’s role clear?
- Are experiments, failures, and pivots preserved?
- Are `Lessons` and `Next Steps` used only when there is something real to say?
- Are exact prompts included as `markdown` code blocks when available?
- Did the draft avoid padding and corporate polish?
- Can the post also work as a presentation, with clear divider-based sections and one main idea per section?
- Is anything invented?
