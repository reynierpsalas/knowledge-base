# AGENTS.md: Knowledge Base Vault

This folder is a personal knowledge base (an Obsidian vault of plain Markdown files).
It holds project context, reusable conventions, and work logs. Read this file first.

## Structure

```
projects/<name>/        # everything specific to ONE project
  overview.md           # what it is, stack, repos, current status (read first)
  requirements.md       # scope: in, out, constraints, open questions
  decisions.md          # why things are the way they are (newest first)
  logs/YYYY-MM-DD.md    # short dated session notes
reference/              # reusable across ALL projects (conventions, how-tos, checklists, snippets)
inbox/                  # unsorted raw notes, waiting to be triaged
templates/              # note templates. Never treat these as real notes
```

Rule of thumb: if a note would make sense unchanged in a different project, it goes in
`reference/`. If it only makes sense for one project, it goes in `projects/<name>/`.

## Note conventions

- Plain Markdown only. Use standard `[[wikilinks]]` for links between notes.
- Do not use plugin-dependent syntax (Dataview queries, etc.) in notes you create.
- Every note starts with YAML frontmatter, then a `# Title`, then a 1-2 sentence summary.
- Frontmatter fields: `project`, `status`, `date` or `updated` (YYYY-MM-DD), `tags` (optional).
- File names: lowercase, words separated by hyphens (`commit-messages.md`).
  Logs are named by date (`2026-10-13.md`).
- One topic per note. If a note grows past about 200 lines, propose splitting it.
- Link instead of copying. Refer to reference notes rather than repeating their content.

## Safety rules

1. **Never store secrets** (API keys, passwords, tokens, private keys, connection strings
   with credentials). Write where a secret lives instead (e.g. "in the host's env vars").
2. **Never delete or rename notes** unless explicitly asked. Propose it instead.
3. **Write scope:** by default, only create or edit files in `inbox/` and
   `projects/*/logs/`, and make the specific updates described under "End of a session".
   Ask before editing anything else, especially `reference/`.
4. Do not edit `templates/` or `.obsidian/`.
5. Never invent facts. If something is unknown, write it under "Open questions" or ask.

## Working on a project

At the start of a session:
1. Read `projects/<name>/overview.md`.
2. Read `projects/<name>/decisions.md` and the two most recent files in `logs/`.
3. Read `requirements.md` before building or suggesting new features.
4. Do not build anything listed under "Out of scope".
5. Follow the relevant notes in `reference/`, unless `overview.md` lists a project-specific
   deviation. Project-specific rules win over reference rules.

During the session:
- If a decision is made (a choice with real trade-offs), record it in `decisions.md`.
- If scope changes, update `requirements.md`.

## End of a session

When asked to wrap up (or when a session clearly ends), do these three things:
1. Create `logs/YYYY-MM-DD.md` from `templates/project/log.md` (append if today's log exists).
   Keep it to 5-10 lines: Done, Learned / gotchas, Next.
2. Add any new decisions to the top of `decisions.md` using the template format.
3. Update "Current status" and the `updated` date in `overview.md`.

## Starting a new project

When asked to create a project `<name>`:
1. Create `projects/<name>/` and `projects/<name>/logs/`.
2. Copy the four templates from `templates/project/` (`overview.md`, `requirements.md`,
   `decisions.md`) into the folder. The `log.md` template is used per session, not copied.
3. Fill in what is known. Mark unknowns as `TBD` and list them under "Open questions".
   Do not guess.

## Using reference notes

- Check `reference/` before proposing a convention, structure, or procedure.
- If you notice a reusable pattern during a task, do not edit `reference/` directly.
  Add a rough note to `inbox/` and mention it, so it can be reviewed and promoted.

## Triaging the inbox

When asked to triage `inbox/`:
- Propose a destination for each note (project folder, `reference/`, or delete).
- Wait for confirmation before moving anything.
