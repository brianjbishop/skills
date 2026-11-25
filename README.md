# skills

All of b.'s agent skills in one place: the ones b. wrote, the ones b. downloaded, and the ones that came built into Claude.

Each skill is a folder with a `SKILL.md` (YAML frontmatter with `name` and `description`, then plain Markdown instructions) and sometimes `references/`, `scripts/` or examples beside it.

## Folders

- `made/` skills b. wrote himself.
- `downloaded/` third-party skills (design ones in `downloaded/design/`), copied here because their licenses allow it, with each license kept beside the skill.
- `built-in/` skills that ship with Claude, copied from Anthropic's public repo under Apache 2.0.

---

## made/

| Skill | What it does | Source |
| --- | --- | --- |
| [site-stack](made/site-stack) | Build and edit b.'s portfolio site (Notion CMS, Astro theme, Vercel, Cloudinary/R2) and act on Figma comments | Written for this repo |
| [dlog](made/dlog) | Turn an AI session or diff into a narrative devlog entry | Uploaded to Claude |
| [notion-presentation-style](made/notion-presentation-style) | Turn a Notion page into a divider-based presentation that still reads as a doc | Notion Skills library |
| [match-meeting-note-to-calendar-event](made/match-meeting-note-to-calendar-event) | Rename a Notion AI meeting note to match its calendar event | Notion Skills library |
| [counsel](made/counsel) | Sparring partner to prep for high-stakes conversations and pitches | Uploaded to Claude |
| [test](made/test) | Pressure-test an argument or storyline before it goes to a client | Uploaded to Claude |
| [review](made/review) | Review and rewrite slide decks to executive standard | Uploaded to Claude |
| [research](made/research) | Structured web research and outline generation for strategy work | Uploaded to Claude |
| [agre](made/agre) | Three-line definitions of any term | Uploaded to Claude |
| [pithy](made/pithy) | Compress writing into something shorter and sharper | Uploaded to Claude |
| [prompt-polisher](made/prompt-polisher) | Score and improve prompts for any domain | Uploaded to Claude |
| [prompt-1](made/prompt-1) | Prompt Polisher 1.1: score prompts on 7 dimensions and rewrite | Uploaded to Claude |
| [prompt-2](made/prompt-2) | Prompt Polisher 2.0: adds image prompts and Creative Director mode | Uploaded to Claude |
| [prompt](made/prompt) | Prompt Polisher 3.0: the KERNEL framework | Uploaded to Claude |
| [stack-prints](made/stack-prints) | Model stacked 3D prints that snap apart after printing | Uploaded to Claude |
| [3dprinteros-batch-slice](made/3dprinteros-batch-slice) | Slice STLs one after another in 3DPrinterOS for the Bambu P2S | Uploaded to Claude |
| [apply](made/apply) | Career writing: cover letters, follow-ups, interview prep, resume tailoring | Uploaded to Claude |
| [port-entry](made/port-entry) | Turn a project's notes, repo and files into a brianjbishop.com portfolio section | Uploaded to Claude |
| [brian-blog-voice](made/brian-blog-voice) | Write blog posts in b.'s own voice | Notion Skills library |
| [chef](made/chef) | Three recipes from what's in the fridge, with photo prompts | Uploaded to Claude |
| [chef-bulk](made/chef-bulk) | Batch-cooking recipes that last one to two weeks | Uploaded to Claude |

Some skills here point to reference PDFs (past decks, real examples); those are kept private too, and the tables that list them say so.

No license has been chosen yet for the skills in `made/`. Until one is added, all rights are reserved by b.

## Design

The skills b. reaches for on web and UI work, used across projects including Audiophilium. [site-stack](made/site-stack) is b.'s own; the rest are third-party. Where the license allows it, the skill is copied into `downloaded/design/` with its license and a `SOURCE.md` naming the exact upstream commit. The others are linked only.

| Skill | What it does | Source | Here |
| --- | --- | --- | --- |
| [site-stack](made/site-stack) | b.'s portfolio site stack, driven by Notion and Figma comments | Written for this repo | Copied |
| [frontend-design](downloaded/design/frontend-design) | Distinctive visual direction for new or reshaped UI | [anthropics/skills](https://github.com/anthropics/skills) | Copied, Apache-2.0 |
| [impeccable](downloaded/design/impeccable) | Design, critique, audit and polish a frontend; builds on frontend-design | [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Copied, Apache-2.0 |
| [ui-ux-pro-max](downloaded/design/ui-ux-pro-max) | UI/UX design data and rules for web, mobile and desktop | [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | Copied, MIT |
| [high-end-visual-design](downloaded/design/high-end-visual-design) | Calm, polished UI: soft contrast, whitespace, spring motion | [Leonxlnx/taste-skill-classics](https://github.com/Leonxlnx/taste-skill-classics) | Copied, MIT |
| [anti-ui-slop](downloaded/design/anti-ui-slop) | Keep agent-built UI product-specific, with a finish gate | [uizze/uizze](https://github.com/uizze/uizze) | Copied, Apache-2.0 |
| [diagram-design](downloaded/design/diagram-design) | Branded architecture diagrams, flowcharts, timelines and more | [cathrynlavery/diagram-design](https://github.com/cathrynlavery/diagram-design) | Copied, MIT |
| design-taste-frontend | Build or redesign company sites to a high bar | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | Linked only: bundles about 40 MB of third-party photos under their own licenses |
| redesign-existing-projects | Audit an existing page before restyling it | [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | Linked only: retired upstream and folded into design-taste-frontend |
| web-design-guidelines | Review UI code against Vercel's Web Interface Guidelines | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | Linked only: its bundled guidelines file comes from a repo with no stated license |

To install a linked-only skill, follow the install line in its upstream README (most use `npx skills add <repo> --skill <name>`).

## downloaded/

| Skill | What it does | Source | License |
| --- | --- | --- | --- |
| [postiz](downloaded/postiz) | Schedule posts to 28+ social and chat channels with Postiz | [gitroomhq/postiz-agent](https://github.com/gitroomhq/postiz-agent) | AGPL-3.0 (kept in folder) |
| [cowork-plugin-customizer](downloaded/cowork-plugin-customizer) | Customize a Claude plugin for an organization's tools | Anthropic cowork-plugin-management plugin | Apache 2.0 (kept in folder) |
| [create-cowork-plugin](downloaded/create-cowork-plugin) | Build a new Claude plugin from scratch | Anthropic cowork-plugin-management plugin | Apache 2.0 (kept in folder) |

## built-in/

Copied from [anthropics/skills](https://github.com/anthropics/skills) under Apache 2.0. See [built-in/THIRD_PARTY_NOTICES.md](built-in/THIRD_PARTY_NOTICES.md).

| Skill | What it does |
| --- | --- |
| [docx](built-in/docx) | Create, read and edit Word documents |
| [pdf](built-in/pdf) | Read, merge, split, fill and create PDFs |
| [pptx](built-in/pptx) | Create and edit PowerPoint decks |
| [xlsx](built-in/xlsx) | Create and edit spreadsheets |
| [skill-creator](built-in/skill-creator) | Create, test and improve skills |

### Built-in skills listed but not copied

These come with Claude but aren't published under a license that allows copying, so they're listed here only. They're already available inside Claude.

| Skill | What it does | Why not copied |
| --- | --- | --- |
| chrome-browser | Use Claude in Chrome | Proprietary |
| computer-use | Control apps on your own computer | Proprietary |
| built-in-browser | Use the browser inside the Claude desktop app | Proprietary |
| docs | Make editable Claude Docs | Not publicly released |
| google-workspace | Make and edit Google Docs, Sheets and Slides | Not publicly released |
| deep-research | Multi-source research reports | Not publicly released |
| morning | Morning summary | Not publicly released |
| import-memory | Import memory from another assistant | Not publicly released |

---

## Installing a skill

**Claude.ai or the Claude app:** zip the skill's folder (the folder itself, with `SKILL.md` at its top), then go to Settings > Capabilities > Skills and upload the zip.

**Claude Code:** copy the folder to `~/.claude/skills/<skill-name>/` for all projects, or to `.claude/skills/<skill-name>/` inside one project.

```bash
git clone https://github.com/brianjbishop/skills.git
cp -r skills/made/site-stack ~/.claude/skills/
cp skills/made/site-stack/config.example.json ~/.claude/skills/site-stack/config.local.json
```

**Other agents:** every `SKILL.md` is plain Markdown. Paste it into the agent's instructions, or point the agent at the file.

## Not here

- **pl-copilot** wasn't found in Claude, Drive, Notion or GitHub. It can be added once it turns up.
