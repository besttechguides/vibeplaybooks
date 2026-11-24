# Project brief

Fill in every `[bracket]` before you ask the agent to build or change anything. If you do not know an answer yet, write “unknown — ask before assuming.” Delete any section that truly does not apply.

This file is the source of truth for agents (Cursor, Claude Code, Codex, and others). Keep it short enough to re-read at the start of every session.

## What this product is

- **Product name:** [name]
- **One sentence:** [who it is for, and what job it does]
- **It is not:** [two or three things people might assume that are out of scope]
- **Primary user:** [for example: a UK sole trader; a hobby player; me]
- **Success for a first launch:** [one measurable thing, for example “a stranger can pay £12 and get the ZIP”]

## Stack and commands

- **App type:** [Next.js App Router / Express / other]
- **Language:** [TypeScript / Python / …]
- **Package manager and Node (or Python) version:** [e.g. pnpm, Node 22]
- **Data:** [Postgres / Supabase / SQLite / none]
- **Auth:** [none yet / magic link / other]
- **Payments:** [none / Stripe Checkout / Payhip / other]
- **Email:** [none / Resend / other]
- **Host:** [Vercel / other / not deployed]

```bash
# Install
[pnpm install]

# Run locally
[pnpm dev]          # expected: app at http://localhost:3000

# Test
[pnpm test]

# Build
[pnpm build]
```

If a command fails, stop and report the error. Do not invent a different stack.

## How to work

- Read this file and the relevant playbook before editing.
- Make the smallest change that completes the asked job.
- Do not rewrite working files to “clean them up” unless that is the job.
- Do not add a new dependency without saying why and waiting for a yes, unless the playbook in progress already named it.
- After a change, run the command that proves it (the playbook’s done-when test, or the test/build command above).
- Never say you are done until that command has been run and the result is included.

## Do not do this without asking

- Delete or rename files outside the current job
- Change auth, payments, or environment variable names
- Force-push, rebase shared history, or `git reset --hard`
- Spend money, call a paid third-party API in live mode, or send real email to anyone except an address I give you
- Commit files that may contain secrets (`.env`, credentials, key files)
- Weaken, skip, or delete a test to make a suite pass

## Secrets

- Secret values live in `.env` (or the host’s environment). They are never committed and never sent to the client.
- Anything prefixed `NEXT_PUBLIC_`, `VITE_`, `EXPO_PUBLIC_`, or similar is **public**. Do not put a secret there.
- If you are unsure whether something is a secret, treat it as one and ask.

## Playbook rules in force

List the Vibe Launch Pack playbooks you have installed, so the agent knows they apply:

- [ ] 02 Scope guard (recommended: always)
- [ ] 04 Secrets and env vars (recommended: always)
- [ ] others: [numbers]

Paste the matching sections from `agent-sections/` below this line, or rely on Cursor `.mdc` rules if that is how you work.

---
