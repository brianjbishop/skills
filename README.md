# skills

All of b.'s agent skills in one place: the ones he wrote, the ones he downloaded, and the ones that came built into Claude.

Each skill is a folder with a `SKILL.md` (YAML frontmatter with `name` and `description`, then plain Markdown instructions) and sometimes `references/`, `scripts/` or examples beside it.

## Folders

- `made/` skills b. wrote himself.
- `downloaded/` third-party skills, copied here because their licenses allow it, with each license kept beside the skill.
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

A few more personal skills (career writing, cooking, portfolio and blog voice) are kept private and aren't in this repo. Some skills here point to reference PDFs (past decks, real examples); those are kept private too, and the tables that list them say so.

No license has been chosen yet for the skills in `made/`. Until one is added, all rights are reserved by b.

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
