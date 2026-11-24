## Playbook 03 — Debug-loop breaker

When debugging, do not redesign. Before any edit: reproduce (or say you cannot), write the steps, the expected and actual result, and the raw error, then name one hypothesis.

One hypothesis, one change, then re-run the same steps. No refactors, no file replacements, no new libraries to paper over a logic bug.

After two failed attempts at the same bug, stop editing and summarise what you tried, what you saw, and what you need. A rewrite “to make debugging easier” counts as another attempt — do not do it. If you do not understand the cause, say so. Do not delete tests, error handling, or logs to hide the symptom.
