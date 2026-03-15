# Workflow

## Session startup — do this before every task, in order
1. Read chapter-1/SPEC.md — confirm scope and which phase gate is active
2. Read PROGRESS.md — confirm last completed task and what comes next
3. Read chapter-1/the-brief.md if this is the first session or the problem has shifted
4. State your plan for this session before writing any code

## Always
- Read SPEC.md before starting any task
- Write a build plan before writing code — state what you will build and in what order
- One task at a time — finish and confirm before starting the next
- Update PROGRESS.md after every completed task, before moving to the next
- Run `npm run typecheck` and `npm run lint` before marking any task done
- Start a new conversation when moving to a different feature or task

## Never
- Install a dependency without flagging it and waiting for approval
- Modify the database schema without updating SPEC.md first
- Hardcode strings, API keys, or environment-specific values
- Skip a phase gate — wait for explicit approval before proceeding
- Proceed to the next task without updating PROGRESS.md
- Use `NEXT_PUBLIC_` prefix for any secret or API key

## Phase gates — wait for explicit approval before proceeding
- Requirements approved: "Requirements approved. Proceed to design."
- Design approved: "Design approved. Proceed to failing tests."
- Tests confirmed failing: "Tests approved. Proceed to implementation."
- Implementation complete: "Feature approved. Proceed to next task."

## Use Plan Mode for any task touching more than 2 files
Press Shift+Tab to enter Plan Mode. Save the plan to .cursor/plans/[feature].md before building.

## When something breaks — follow this order
1. Describe the observable failure — what the user sees, exact input, exact output
2. Add targeted logs to identify the failure point — do not fix yet
3. State the most likely root cause based on the logs
4. Make the minimal fix
5. Verify — confirm the fix works and nothing else regressed
6. Remove the logs
7. Add a rule to known-issues.md if this failure could recur
