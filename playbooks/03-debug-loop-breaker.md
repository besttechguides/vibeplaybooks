# Playbook 03 — Debug-loop breaker

## What this is for

The loop where the agent keeps changing things, the bug remains (or moves), and you no longer recognise the code. You do not have to understand the whole file to use this. You do have to make the agent slow down.

## What this is not

A guarantee it will find the bug. It is a way to stop digging a deeper hole. If two careful attempts fail, the right move is to gather evidence, not to “let it cook.”

## Install

```bash
mkdir -p .cursor/rules
cp rules/03-debug-loop-breaker.mdc .cursor/rules/
```

Paste `agent-sections/03-debug-loop-breaker.md` into `AGENTS.md`. Start a **new** chat for the bug (old chats are already in the loop).

Keep **02 Scope guard** installed as well.

## Prompt sequence

**Prompt 1 — Evidence only (no edits)**

> We are debugging. Do not edit any files yet.
>
> Bug: [one sentence].
> Steps I take: [1, 2, 3].
> Expected: [what should happen].
> Actual: [what happens].
>
> Here is the error or log output, pasted in full:
>
> ```
> [paste]
> ```
>
> Read the code on the path that would run for those steps. Then tell me: (a) the files and functions involved, in order, (b) one hypothesis for the cause, (c) the single smallest check or edit that would prove or disprove it. Wait for my yes before editing.

**Prompt 2 — One change**

> Hypothesis we agreed: [quote it]. Make only the smallest change that tests it. Do not refactor. Then run or re-state the exact reproduction steps, and report what happened. If you cannot run it yourself, give me the exact steps to run and wait.

**Prompt 3 — If it failed once**

> The bug is still there. This is attempt two, not a rewrite. Say what the first attempt taught us, name a *different* hypothesis, and propose one change. Wait for my yes.

**Prompt 4 — If it failed twice**

> Stop editing. Do not try a third fix. Write a short brief I can reuse: steps, expected, actual, the two hypotheses we tested, the exact diffs, and what evidence is missing. List two things I could collect (a log line, a screenshot, a network trace, a value you cannot see). Then wait.

**Prompt 5 — Once it is actually fixed**

> Summarise the root cause in five lines or fewer, in plain English. List the files that should stay changed. Confirm there are no leftover debug hacks, extra console logs with secrets, or commented-out blocks from the failed attempts. If there are, remove only those leftovers.

## Checklist

- [ ] You started a new chat for this bug
- [ ] Prompt 1 was answered with **no file changes**
- [ ] Each edit was one hypothesis, then a re-test
- [ ] You stopped after two failed attempts, or the bug is gone
- [ ] Leftover debug code from failed attempts is gone
- [ ] You can explain the cause in one short paragraph (even if the explanation came from Prompt 5)

## Done when

1. The original steps now produce the expected result, **or** you have a written brief from Prompt 4 and have stopped the loop.
2. `git diff` (or the agent’s file list) shows a small, relevant change — not a rewritten module.
3. The agent did not delete tests or error handling as part of the “fix.”

## If it still fails

- You may be changing two things at once (code *and* data, or two files). Go back to one.
- The reproduction may be wrong (cached build, old env, different port). Confirm you are hitting the code you think you are hitting.
- If the problem is “I have no idea what this repo does,” run playbook 01 first, then come back.

## Stack notes

Works for any stack. If the bug is in production only, you still start with Prompt 1; add the log lines you have. Do not “fix production” by rewriting local files you have not evidenced.


---

## Want the rest of the launch?

This sample is playbook 03, plus the scope-guard rule and an `AGENTS.md` starter.

The **Vibe Launch Pack** (£12) adds the other 15 playbooks: secrets, auth, Stripe checkout, safe database access, deploy without leaking env, a landing page with a real CTA, waitlist, email, SEO, tests, errors, accessibility, and a pre-launch audit.

[Get the Vibe Launch Pack — £12](https://payhip.com/b/6UGRb)
