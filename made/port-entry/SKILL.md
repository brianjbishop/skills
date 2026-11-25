---
name: port-entry
description: >
  Portfolio section writer for Brian (brianjbishop.com). Takes a project's raw
  inputs — Notion pages, GitHub repos, Google Drive folders/docs, blog posts,
  press links, uploaded files — and turns them into a finished portfolio
  section in the exact format and voice of Brian's site: Name (Type) → intro →
  Explore More → Process → Next Steps. Use this skill whenever Brian says "write
  the [X] section for my portfolio/website", "add this project to my site",
  "turn this project into portfolio copy", "package this for brianjbishop.com",
  "write up [project] for my portfolio", or drops a set of project links/repos
  and asks for site-ready copy about a project. Also trigger when he points at a
  project's Notion page + repo + drive folder together and wants them
  synthesized into one section. Always use this skill for portfolio-section copy
  — do not summarize the project conversationally instead.
---

# port-entry — Portfolio Section Writer

Brian's projects live scattered across sources — a Notion page holding the
concept and dev notes, a GitHub repo holding the actual build story, a Drive
folder of assets, a blog post, a press link. His portfolio site
(brianjbishop.com) presents each project as a tight, well-voiced section. This
skill does the connective work: gather every input, read the adjacent sections
to lock the format and voice, and produce a section that drops straight onto the
site.

The goal is copy Brian can paste with light edits — in his voice, structurally
identical to what's already on the page, honest about collaboration, and built
from what the sources actually say.

---

## The Pipeline

Run these in order. Don't skip the gathering — the quality of the section is
capped by how much of the source material you actually read.

### 1. Gather every input

Pull from all sources provided (and ask for the obvious missing one if a project
clearly has a repo or Notion page that wasn't shared):

- **Notion** — `notion-fetch` on the page ID or URL. Read *every tab* (About,
  DevLog, Performance, Feedback, Documentation, etc.). The concept and origin
  usually live in About; the Feedback/notes tab is the raw material for Next
  Steps.
- **GitHub** — fetch the `README.md` for the what/how, but the build story lives
  in `DEVELOPMENT.md` and any `handoff/*.md` docs. Get these via the GitHub API
  if a direct fetch is blocked:
  `curl -s "https://api.github.com/repos/<owner>/<repo>/contents/<path>"` →
  read `download_url`, or pull the blob and base64-decode `content`. Commit
  history (`/commits`) reveals the arc of iterations.
- **Google Drive** — `google_drive_search` to find the folder/docs, then
  `google_drive_fetch` (or `read_file_content`) to read them.
- **Blog posts, press, collaborator docs, any URL** — `web_fetch`.
- **Uploaded files** — read from `/mnt/user-data/uploads`.

### 2. Lock the format and voice

Before writing, `web_fetch` the live portfolio page the section belongs to (e.g.
`brianjbishop.com/bam`). Read the adjacent sections. Match their structure,
length, and cadence exactly — the new section should be indistinguishable in
shape from what's already there. Pay special attention to how existing **Process**
sections read (see the rule below).

### 3. Synthesize into the section structure

Write the section (format below), flag any judgment calls, and present it inline
as copy-pasteable text. Offer a shorter variant.

---

## Output Format

Match this structure — it's the shape of every section on the site:

```
**[Project Name] ([Type])**

[Intro — 1–2 short paragraphs]

Explore More: [Label](url) / [Label](url)

**Process**

[The build story — 1–3 paragraphs]

**Next Steps**

[What showing it taught, 1 paragraph]

Where it goes next:
- [future direction]
- [future direction]
```

**Type** goes in parentheses after the name — the medium/context: Installation,
Wearable, Video Game, Performance, Tool, etc.

**Intro** — Lead with the concrete thing the project *is*, in one observation.
Then: the collaboration (front and center, named honestly — including AI/Claude
if that's true), the question the project asks, its origin or lineage, and
where/how it was shown (venue, residency, being flown out, etc.). Keep it to one
or two short paragraphs.

**Explore More** — a single line of relevant links: GitHub, documentation, press,
a collaborator's own write-up. Omit if there's genuinely nothing to link.

**Process** — see the rule below. This is the section people get wrong.

**Next Steps** — open with what actually showing/performing/testing the project
taught (the honest logistical or design lesson), then a short bulleted list of
future directions. Pull these from the project's own feedback/notes. Compress —
list the most compelling few, never everything.

---

## The Process Rule (most important)

**Process is the story of *making* the thing, not a walkthrough of how the
finished thing works.**

The existing Process sections on the site are build narratives: the sensor
approaches tried and abandoned, "the two hardest problems were power and
calibration," the specific fix that finally worked, the dead ends. They read
like someone recounting how they built it — not a product manual.

So Process should cover:
- The arc of iterations — where it started, what each version added, how it got
  to the version being shown
- The hardest problems and *why* they were hard — the real design tension
- The decisions made and their rationale ("reading breath by volume falls apart
  with six people in a room, so it triggers on direction instead")
- The bugs that actually mattered for the context (a live show, an arcade floor)
- Dead ends, plainly stated — they have narrative value

**This is why `DEVELOPMENT.md` and `handoff/*.md` matter more than the README.**
The README says what the thing does; the dev docs say how it got built and what
broke along the way. Mine those. If they don't exist, reconstruct the arc from
commit history and the Notion DevLog.

Do NOT write Process as: "The system has two views. View A does X. View B does
Y." That's a feature list. It belongs (briefly, if at all) in the intro, not
Process.

---

## Voice Guidelines

Brian's written voice:
- Concise and forward-moving — no over-explaining, trusts the reader
- Leads with observation, not framing ("The routing was wrong," not "I want to
  talk about routing")
- First person — "I" for solo work, "we" when it was genuinely shared; match who
  actually did what
- Em-dashes for connective asides, used sparingly
- Collaboration front and center — names tools and collaborators (including AI)
  honestly
- Cuts defensiveness — if something didn't work, says so plainly and moves on
- Technical but not gatekeeping — defines domain terms briefly on first use
- Lists only the most compelling points, never exhaustive

Do not:
- Open with "In this project…" or "This piece explores…"
- Pad with generic observations about creativity, technology, or connection
- Over-explain context the reader can infer

---

## Source Fidelity

**Don't assert anything the sources don't support.** If a strong, section-worthy
detail isn't in the inputs — a venue, a "flown out to perform," a collaborator's
role — flag it and ask rather than inventing it. Brian confirming it in chat
counts as a source; a plausible guess does not.

**Prefer clean public naming over messy working names.** Raw notes often carry
placeholder names ("Every 1," "Grouped") that got renamed in the polished repo
("Every Breath," "Group Breath"). Use the public-facing names.

**Flag judgment calls at the end.** After the draft, note the two or three
choices worth a second look — naming picked, a collaborator credited a certain
way, a detail included or held back — so Brian can adjust quickly.

---

## Optional Parameters

Brian can specify at the top of his request:
- `type: [Installation / Wearable / Performance / …]` — the parenthetical after
  the name; inferred from context if omitted
- `length: [short / full]` — full matches the depth of existing sections
  (default); short is a tighter, single-paragraph-per-heading version
- `pov: [first / we]` — defaults to matching who did the work
- `page: [bam / didomi / …]` — which portfolio page's format to match; defaults
  to the one the project belongs to

---

## Delivery

Present the section inline as clean, copy-pasteable text in the site's format —
not as a file, since Brian iterates on wording in chat. After the draft:
1. Briefly note the judgment calls made.
2. Offer to tighten further or show a shorter variant side by side.

---

## Edge Cases

**Sparse sources:** If a project has only a repo or only a Notion page, write
from what's there and name the gap — don't pad. Ask for the missing source if it
clearly exists.

**No build docs:** If there's no DEVELOPMENT.md or handoff docs, reconstruct
Process from commit history + Notion DevLog + anything in the conversation. Say
so if the build story is thin.

**Multiple performances/versions:** Lead with the most recent or most
significant showing in the intro; let Process carry the lineage of earlier
versions.

**Nothing shipped yet:** If the project is in progress, write it honestly as
in-progress — Process becomes "where it stands and what's been hard so far,"
Next Steps becomes the near-term plan.
