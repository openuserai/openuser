# USER.md Standard
**Specification v0.2**
 
> A simple, open format for telling AI agents who you are.
 
## Overview
 
`USER.md` is a structured markdown profile that describes a person to AI. Create it once at **[OpenUser.ai](https://openuser.ai)** — every agent that reads it understands you: your background, preferences, communication style, and how to work with you.
 
The primary consumer is an AI agent using an OpenUser plugin (coming soon). The format is markdown — token-efficient, human-readable, and natively understood by language models.
 
---
 
## How It Works
 
```
Create → Host → Plugin fetches at session start → Agent knows you from word one
```
 
1. **Create** — Complete the onboarding at OpenUser.ai. Your USER.md is generated from your answers and published at `openuser.ai/yourname`.
2. **Install the plugin** — Add the OpenUser plugin to your agent (Claude, ChatGPT, Gemini etc.) and configure your username once during setup.
3. **Fetch at session start** — Every time a session begins, the plugin fetches your latest profile and injects it into the agent's context automatically. The agent knows who you are before you type a single word.
4. **Stay current** — Push updates anytime: re-run the interview, make changes in your profile, sync via the API (coming soon), or connect data sources (coming soon). The plugin always fetches the latest version.
---
 
## The Format
 
`USER.md` is plain markdown. Only `User Profile` section is required — everything else is optional, and will be under the `Additional Context` section.
 
```markdown
# User Profile
 
- **Name:** Alex Wren
- **Call me:** Alex
- **Country:** United States
- **Language:** English
- **Username:** openuser.ai/alexwren
- **Occupation:** Project Manager
- **Industry:** Technology

# Additional Context

Launching a new product line in Q3. Coordinating across 4 teams. Focused on reducing meeting overhead and improving async communication.

## Communication

- **Tone:** Direct and concise
- **Verbosity:** Short unless depth is needed
- **Format:** Prose over bullet points; code examples over abstract explanation

## Work Style

- **Decisions:** Data-driven — show me tradeoffs
- **Collaboration:** Async-first
- **Feedback:** Blunt is fine. Don't soften bad news.

## Constraints

- No motivational content or unsolicited encouragement
- No emoji-heavy responses
- Never guess — say when unsure

## Agent Instructions

- Always show your reasoning
- If unsure, say so

## Open To

- Project management roles, operational leadership, cross-functional collaboration, and discussions around better planning, clearer execution, and helping teams move faster with less friction.

```
 
---
 
## Section Reference
 
| Section | Required | Purpose |
|---|---|---|
| `User Profile` | **Yes** | Name, country, language, username - are required. Call me, occupation, industry - are optional |
| `Additional Context` | No | Freeform notes — preferences, projects, interests, instructions, anything relevant |
 
---
 
## Fetching a Profile
 
### Primary endpoint
 
```
GET https://openuser.ai/{username}
```
 
Returns `text/markdown` by default — optimized and efficient for delivery.
