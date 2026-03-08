# Braindump - Personal Research Vault

## Overview
Personal research knowledge base managed with Obsidian and GitHub.
Claude Code automates research workflows: planning, execution, and organization.

## Structure
```
/
├── Inbox.md          # Add topic words here (one per line) — Claude turns them into research plans
├── Thoughts/         # Random thoughts — Claude organizes without destroying
├── Topics/           # One folder per research topic
│   └── <topic>/
│       ├── _index.md        # Topic overview, status, key questions
│       ├── notes/           # Research notes and findings
│       └── references/      # Source summaries and links
├── Templates/        # Obsidian templates for consistent formatting
├── Maps/             # Maps of Content (MOCs) linking related topics
├── Archive/          # Completed or paused research
└── .claude/skills/  # Claude Code skills for automation
```

## Workflows

### Deep Research Workflow
1. `/deep-memo <words>` — Claude adds topic words to `Inbox.md`, commits to main and pushes
2. `/deep-plan` — Claude creates structured research plans, commits to main and pushes
3. `/deep-research` — Execute research for planned topics, commits to main and pushes
4. `/deep-suggest` — Claude suggests follow-up research directions (read-only, no commits)

### Quick Q&A
1. `/ask <question>` — Ask anything, get an answer, findings auto-saved to the vault
   - Searches existing vault for context, uses web if needed
   - Creates notes and references in the appropriate topic folder
   - Commits to main and pushes (no PR overhead)

### Thoughts Workflow
1. User drops random thoughts in `Thoughts/` (freeform markdown)
2. `/dump` — Claude adds tags, wikilinks, and connections without modifying original content, commits to main and pushes

## Conventions
- All files are Markdown (.md), compatible with Obsidian
- Use `[[wikilinks]]` for internal links between notes
- Use YAML frontmatter for metadata (status, tags, dates)
- Tag taxonomy:
  - `#topic/<name>` — topic identifier
  - `#status/planned` — research plan created, awaiting execution
  - `#status/active` — research in progress or completed
  - `#status/paused` — research paused
  - `#status/done` — research completed
  - `#thought` — random thought
  - `#thought/<theme>` — themed thought
  - `#reference` — reference/source file
- Topic folder names: lowercase, hyphens for spaces (e.g., `machine-learning`)
- Note filenames: descriptive, lowercase, hyphens (e.g., `transformer-architecture.md`)

## Working with this repo
- When creating a new topic, use the topic template in `Templates/`
- When adding research notes, use the note template
- Always add appropriate frontmatter and tags
- Link related notes using `[[wikilinks]]`
- Prefer updating existing notes over creating duplicates
- Inbox.md lines can be minimal — just a word or phrase is fine
- Thoughts files should be left as-is; only enhance, never rewrite

## Claude Code Skills
- `/ask <question>` — Quick Q&A — ask anything, findings saved to vault
- `/deep-memo <words>` — Add topic words to Inbox.md for later research
- `/deep-plan [topics]` — Create research plans from Inbox.md or from arguments
- `/deep-research [topics]` — Execute research for planned topics
- `/deep-suggest [topics]` — Suggest additional research directions
- `/dump [files]` — Organize thoughts with vault context
- `/todo [task]` — Record and update todo items

