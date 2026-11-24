# Quick start

1. Copy the two rules into your project:

   ```bash
   mkdir -p .cursor/rules
   cp rules/02-scope-guard.mdc .cursor/rules/
   cp rules/03-debug-loop-breaker.mdc .cursor/rules/
   ```

2. If you do not already have an `AGENTS.md`, copy `templates/AGENTS.md` to your project root and fill in the `[brackets]`. Paste the two sections from `agent-sections/` into that file. Claude Code users should also copy `templates/CLAUDE.md`.

3. Start a **new** agent chat (old chats will not see new rules).

4. Open `playbooks/03-debug-loop-breaker.md` and paste **Prompt 1**. Do not skip the “no edits yet” step.

The scope-guard rule is meant to stay on. You can leave the debug-loop rule installed, or add it only when you are stuck.
