# User Manual Kit

A starter template for building your personal "Working with Me" page using Claude Code. Fork it, fill it in with AI, deploy to GitHub Pages.

## What is this?

A single-page website that tells your teammates how to work with you — your communication style, values, schedule, personality quirks, and more. Claude Code helps you fill it in by reading your Slack profile and asking you questions.

## Getting Started

### 1. Fork this repo

Click **Fork** on GitHub to create your own copy.

### 2. Clone and open in Claude Code

```bash
git clone https://github.com/YOUR_USERNAME/user-manual-kit.git
cd user-manual-kit
claude
```

### 3. Tell Claude to fill in your manual

Once Claude Code is running, just say:

> "Read my Slack profile and help me fill in my user manual"

Claude will:
- Pull your name, title, and timezone from Slack
- Ask you questions about your working style
- Fill in the HTML template with your answers
- Let you preview locally before pushing

### 4. Enable GitHub Pages

Go to your repo's **Settings > Pages**:
- Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Save

Your site will be live at `https://YOUR_USERNAME.github.io/user-manual-kit/`

## Switching Styles

The page includes 3 built-in visual themes you can toggle with the bar at the top:

- **Monopo** — Dark, bold, typographic (agency-inspired)
- **Editorial** — Warm, light, editorial magazine feel
- **Lottie** — Clean, playful, teal accents

To change the default, tell Claude: "Switch the default style to monopo" (or whichever you prefer).

## Customizing

Everything is in one file: `index.html`. No build tools, no dependencies.

- Want to add a section? Ask Claude.
- Want a completely different visual style? Ask Claude to read one of the `designs/*.md` files and restyle.
- Want to remove a section? Just delete it from the HTML.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- A Slack workspace with the Slack MCP configured (for auto-populating your profile)
- A GitHub account (for deployment)

## Local Preview

```bash
python3 -m http.server 8000
# Open http://localhost:8000
```
