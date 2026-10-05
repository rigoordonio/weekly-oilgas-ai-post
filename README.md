# Weekly Oil & Gas AI Post

A Claude Code skill that drafts one short LinkedIn post a week on the latest oil and gas AI news. It emails the draft for approval and publishes it only after you approve.

## What it does

1. **Finds the story.** Searches for oil and gas AI news from the last 7 days (14 days if needed) from sources such as Reuters, JPT, Offshore, Rigzone, Energy Voice and World Oil. It picks one story with a named company, a concrete AI deployment and a clear date, and skips anything already in `past-topics.md`.
2. **Reads the article.** Opens and reads the full article. Every fact in the post must come from it.
3. **Drafts the post.** No more than 20 lines: the news in one sentence, the key numbers, why it matters, a closing question, a source line and exactly 4 hashtags.
4. **Checks the draft.** Facts, date window, line count, hashtags and no confidential information.
5. **Emails for approval.** Sends one approval email through Gmail (Composio) with the full post text, the key facts and the article link.
6. **Publishes only after approval.** When you reply `post it` in Claude, it publishes the post to LinkedIn (Composio) as a public post.
7. **Logs the story** in `past-topics.md` so it isn't repeated.

## Files

| File | Purpose |
| --- | --- |
| `SKILL.md` | The skill instructions Claude follows |
| `config.example.md` | Template for your personal settings |
| `config.local.md` | Your name, employer and approval email (git-ignored, create it yourself) |
| `past-topics.md` | Log of drafted and published stories (git-ignored, created on first run) |
| `README.md` | This file |

## Requirements

- [Claude Code](https://claude.com/claude-code)
- [Composio](https://composio.dev) with **Gmail** and **LinkedIn** connected

## Install

Clone this repo into your Claude Code skills folder:

```bash
git clone https://github.com/rigoordonio/weekly-oilgas-ai-post.git ~/.claude/skills/weekly-oilgas-ai-post
cd ~/.claude/skills/weekly-oilgas-ai-post
cp config.example.md config.local.md   # then fill in your details
```

No API keys are stored in this repo. Gmail and LinkedIn access is handled by your Composio account.

## Usage

In Claude Code:

```
/weekly-oilgas-ai-post
```

Or ask: *"Do the weekly oil and gas AI post."* Review the approval email, then reply `post it` (or send edits) in Claude.

To run it every Monday, schedule it with `/schedule`. A scheduled run stops after sending the approval email; nothing is published until you approve.

## Guardrails

- Drafts only. Nothing is published without your explicit approval of that draft.
- Uses public information only: no employer, client, project or pricing data, and no tagged people.
- Summaries are written in its own words, with the original publisher cited. It never reuses the article's images.
