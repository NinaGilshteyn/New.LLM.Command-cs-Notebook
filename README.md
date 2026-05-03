# CS Notebook — Claude Code Slash Command

A Claude Code slash command (`/cs-notebook`) that converts raw dev session notes into a structured progress log and saves it as a formatted Word document (`.docx`).

## What it does

1. **Parses raw session notes** — extracts script names, file paths, edits made, commits, repo info, and data locations.
2. **Asks follow-up questions** — if anything is missing (paths, repo, branch, data location, etc.), Claude prompts you with a numbered list of questions before saving. Always ends by asking if you have any additional notes to add.
3. **Generates a structured entry** — organizes everything into a standardized format with tables and categorized next steps.
4. **Saves a `.docx` file** — uses `python-docx` to write a formatted Word document to `Documents\CS_Notebook\`.

Output filename format: `data_{YYYY-MM-DD}_time_{HH-MM-SS}.docx`

Developer name is auto-detected from `git config user.name`, falling back to the OS username — no hardcoding needed.

## Installation

Copy `cs-notebook.md` into your Claude Code commands directory:

```
~/.claude/commands/cs-notebook.md                         # macOS / Linux
C:\Users\<you>\.claude\commands\cs-notebook.md            # Windows
```

Requires Python and `python-docx` (auto-installed on first run if missing).

## Usage

```
/cs-notebook <your raw session notes here>
```

Paste any freeform notes about your coding session. Claude will parse what it can, then ask you targeted questions for anything missing before writing the final document.

## Output sections

| Section | Description |
|---------|-------------|
| Scripts & Files | Name, full path, and language of every file touched |
| Major Edits | Per-file change descriptions and reasons |
| Version Control | Commit messages, repository, and branch |
| Data Storage | Paths, databases, buckets, and output formats |
| Issues & Blockers | Errors and blockers with severity (HIGH / MEDIUM / LOW) and status |
| Next Steps | Broken into four tiers: Immediate, Short-term, Research/Figure out, Backlog |
| Additional Notes | Any extra context or observations added interactively before saving |
| Original Input | Raw notes preserved verbatim |

## Next Steps format

The Next Steps section is split into four tiers so nothing gets lost:

- **Immediate** — do next session (finish scripts, push commits, move data)
- **Short-term** — this week (features, tests, dependencies, refactors)
- **Research / Figure out** — unclear things that need investigation before you can proceed
- **Backlog** — nice-to-haves and ideas to revisit later
