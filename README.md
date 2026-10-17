# searchtok agent skill

teach your agent to research tiktok and instagram reels with [searchtok](https://searchtok.app): the outliers in your niche (posts that got far more views than their account usually gets), the hooks and formats behind them, the creators worth watching and what your competitors post. every number comes from real posts.

works in claude code, codex, openclaw and any agent that reads [agent skills](https://agentskills.io). your agent talks to searchtok through the mcp server or the cli, so you need a searchtok plan: [https://searchtok.app](https://searchtok.app).

## install

```bash
npx skills add Mitchell2398/searchtok-agent
```

it asks which agents to install to. to pick them yourself: `-a claude-code`, `-a codex` or `-a openclaw` (add `-g` to install for every project, not just this one).

**claude code by hand:** copy `skills/searchtok` into `~/.claude/skills/` (every project) or `.claude/skills/` (this project).

```bash
git clone https://github.com/Mitchell2398/searchtok-agent
cp -r searchtok-agent/skills/searchtok ~/.claude/skills/
```

**openclaw:** `npx skills add Mitchell2398/searchtok-agent -a openclaw`. not on clawhub yet.

## connect searchtok

the skill checks this first and tells you what's missing. pick one:

- **mcp** (claude code, claude.ai, chatgpt, cursor, openclaw...): `https://searchtok.app/mcp`. in claude code: `claude mcp add --transport http searchtok https://searchtok.app/mcp`, then sign in from `/mcp`.
- **cli** (coding agents, scripts): `npx searchtok auth:login`. or set `SEARCHTOK_API_KEY` to a key from [https://searchtok.app/app/settings/keys](https://searchtok.app/app/settings/keys).

then ask your agent something like "what's working for dentists on tiktok".

## as a plugin

this repo is also a plugin: the skill plus the searchtok mcp server.

- `plugin.json` and `mcp.json`: the [agent plugins](https://agent-plugins.org) standard (cursor, codex).
- `.claude-plugin/plugin.json` and `.mcp.json`: claude code and grok build.
- `gemini-extension.json`: gemini cli. `gemini extensions install https://github.com/Mitchell2398/searchtok-agent`

**what it connects to:** one remote mcp server, `https://searchtok.app/mcp` (streamable http). you sign in with oauth the first time it's used, and your agent keeps that sign-in. no scripts, hooks or binaries run.

## what's in it

- `skills/searchtok/SKILL.md`: when to use searchtok, the setup check, every tool with its cli command and credits, and the evidence rules (hooks quoted exactly, every outlier score with its explanation, every post linked, what was searched).
- `skills/searchtok/references/`: 7 playbooks, one per kind of question. the same ones searchtok's own agent uses, each crediting the creators it learned from.
- `skills/searchtok/recipes/`: copy-paste prompts for agents that run on a schedule.

## recipes

searchtok doesn't send alerts: your own agent does the watching.

- [competitor watch](skills/searchtok/recipes/competitor-watch.md): Every Monday at 9am, check up to 5 competitor accounts and report their new posts that got 3x or more their usual views, with each hook quoted exactly.
- [niche watch](skills/searchtok/recipes/niche-watch.md): Every Monday at 9am, find the posts from the last 7 days that beat their account's usual views in your niche, with why each one worked.

## about this repo

generated from searchtok's own playbooks and tool list, so it never drifts from what searchtok's agent does. please don't send changes here: they'd be overwritten on the next update. questions: [https://searchtok.app](https://searchtok.app).

mit licence: see [LICENSE](LICENSE).
