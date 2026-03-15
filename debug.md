# /debug

Use when something is broken and the cause is not obvious.

1. Describe the observable failure — what the user sees, exact input, exact output
2. Hypothesise — state the 2–3 most likely root causes before touching any code
3. Add targeted logging to confirm which hypothesis is correct — do not fix yet
4. Ask the user to reproduce while logging is active
5. Identify the root cause from the logs
6. Make the minimal fix
7. Remove the logging
8. Verify the fix — confirm the failure no longer occurs
9. Add a rule to .cursor/rules/known-issues.md if this could recur
