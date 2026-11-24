# Debug Loop Breaker — free sample from VibePlaybooks

Your agent keeps “fixing” the same bug, the code no longer looks like yours, and you are not sure what it actually changed. That is the loop this sample is for.

This is a complete playbook: a Cursor rule, an `AGENTS.md` / `CLAUDE.md` section, a numbered prompt sequence, a checklist, and done-when tests. It also includes a scope-guard rule so the agent does not rewrite working files while it debugs.

It will not magically find every bug. It will stop the spiral of silent rewrites. After two failed attempts, the agent has to stop, write down the evidence, and wait.

## Install

```bash
# from this repo, or after unzipping the sample
mkdir -p path/to/your-project/.cursor/rules
cp rules/02-scope-guard.mdc path/to/your-project/.cursor/rules/
cp rules/03-debug-loop-breaker.mdc path/to/your-project/.cursor/rules/
```

If you do not already have an `AGENTS.md`, copy `templates/AGENTS.md` to your project root and fill in the `[brackets]`. Paste the two files from `agent-sections/` into it. Claude Code users should also copy `templates/CLAUDE.md`.

Then start a **new** agent chat and open `playbooks/03-debug-loop-breaker.md`. Paste **Prompt 1**. It asks for evidence and forbids edits until you agree a hypothesis.

More detail is in `QUICKSTART.md`.

## What’s in this repo

```
rules/02-scope-guard.mdc
rules/03-debug-loop-breaker.mdc
agent-sections/               paste into AGENTS.md
templates/AGENTS.md           fill-in project brief
templates/CLAUDE.md           imports AGENTS.md
playbooks/03-debug-loop-breaker.md
```

## The rest of the launch

Auth, Stripe, secrets, deploy, a landing page, email, SEO, tests, and a pre-launch audit are in the **Vibe Launch Pack** — 16 job playbooks, £12, instant download.

[Get the Vibe Launch Pack — £12](PAYHIP_URL)

Not affiliated with Cursor, Anysphere, Anthropic, or any other tool named in these files. Licence: use in your own projects, no resale — see `LICENSE.md`.
