# CLAUDE.md

This is a **User Manual Kit** — a starter template for building a personal "Working with Me" page using Claude Code. The output is a single-page static HTML site deployed to GitHub Pages.

## Architecture

```
/
├── index.html          # The user manual (single-page, self-contained HTML)
├── designs/
│   └── editorial.md    # Design philosophy for the default Editorial style
├── CLAUDE.md           # This file — instructions for Claude Code
├── README.md           # Getting started guide
└── .claude/
    └── settings.local.json  # Pre-configured permissions
```

## How This Works

The `index.html` file is a complete, self-contained user manual with:
- The Editorial visual style (warm, light, magazine feel)
- All CSS embedded in `<style>` tags (no external dependencies except Google Fonts)
- Placeholder content in `[brackets]` that Claude fills in from Slack profile data and conversation

## Filling In the Template

When a user opens this project in Claude Code, the typical flow is:

1. **Claude reads their Slack profile** using `slack_read_user_profile` to get name, title, timezone
2. **Claude asks the user** about their working style, preferences, values, and personality
3. **Claude edits `index.html`** directly, replacing all `[placeholder]` content with real content
4. **User reviews locally** with `python3 -m http.server 8000`
5. **Claude pushes to GitHub Pages** when ready

## Editing the Page

- This is a single HTML file. Edit it directly — there is no build step.
- All styles are in the `<style>` block at the top.
- Content is plain HTML in the `<body>`. Each section uses semantic class names.

## Using Slack MCP

The Slack MCP is pre-configured. Use it to personalize the manual:

- **`slack_read_user_profile`** — Get the user's name, title, timezone, status, org
- **`slack_search_channels`** — Find channels the user is active in (for "Where to find me")
- **`slack_read_channel`** — Read recent messages for tone/personality signals
- **`slack_search_public`** — Search the user's messages for vocabulary, quotes, emoji patterns

When populating content:
- Replace `[Your Name]` with their display name
- Replace `[Your Title]` with their title
- Update `data-initial` attribute on `.hero__role` with their first name's initial
- Update the `<title>` tag

## Applying a Different Design

Alternative visual styles (Monopo, Lottie) are available in the Figma file:
https://www.figma.com/design/AyUuvVdN3dTKaCtaUSSBZ2/Personal-User-Manual-Templates

If the user wants to restyle the page, use the Figma MCP (`get_design_context` or `get_screenshot`) to read the target design from the Figma file, then rewrite the CSS in `index.html` to match. Keep the HTML structure (class names, nesting) the same — only change the CSS.

The `designs/editorial.md` file documents the philosophy behind the default style.

## Sections Reference

The template includes these sections (all optional — remove or add as needed):

| Section | Class | Purpose |
|---------|-------|---------|
| Hero | `.hero` | Name, title, intro paragraph |
| Traits | `.traits` | 6 personality/work-style cards with icons |
| Communication | `.comm-content` | How you communicate (paragraphs) |
| Pull quotes | `.pull-quote` | Real quotes from Slack messages |
| How to work with me | `.flags` | Green (what works) / Red (what slows me down) |
| Emoji personality | `.emoji-chart` | Bar chart of most-used emojis |
| Energy | `.energy-grid` | Where your time/energy goes (%) |
| Weekly rhythm | `.week-grid` | Visual week schedule |
| Current work | `.project-list` | Active projects |
| Values | `.values-list` | What you care about |
| Vocabulary | `.vocab-grid` | Phrases you use and what they mean |
| Fun facts | `.fun-facts` | Personal/fun things |
| Where to find me | `.tags` | Slack channels |

## Deployment

This site deploys via GitHub Pages from the `main` branch, root (`/`).

To deploy:
1. Commit `index.html` to `main`
2. Push to GitHub
3. Enable GitHub Pages in repo Settings > Pages > Source: "Deploy from a branch" > Branch: `main`, folder: `/ (root)`

Use `gh` CLI to verify Pages status:
```bash
gh api repos/{owner}/{repo}/pages
```

## Local Development

```bash
python3 -m http.server 8000    # Serve at localhost:8000
```

No build step, no dependencies, no npm.
