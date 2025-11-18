# [project-name] - [project-description-oneliner]

## What This Project Is About

[project-description-short-paragraph]

## Instructions

1. Read `.claude/WIP.md`: if something is there, continue the work, if not pick the first item from `.claude/ROADMAP.md`, if empty ask the user.
2. For each new high-level task (feature, doc change, refactoring, ...):
  1. Add the entry in `.claude/ROADMAP.md` on top (LIFO)
  2. Create a new git branch `git checkout -b [type]/[name]`
  3. Keep track of the step you are in the file `.claude/WIP.md` at all times to ensure continuity across sessions (context gets lost):
    1. Template for the task follows the TDD principles: RED -> TEST -> GREEN -> TEST -> REFACTOR (remove redundancies) -> README (general)
      1. How to run tests: [command-to-run-tests]
      2. Tests must be ANTAGONISTIC (try to break code): test null/undefined/empty inputs, concurrent calls, edge cases
      3. RED phase: verify tests FAIL before implementing
      4. GREEN phase: run ALL tests, not just current module/unit tests
      5. REFACTOR phase: if tests break → REVERT immediately and fix the root cause
    2. Update `.claude/WIP.md` at EACH step, commit locally on the branch when each step succeeds and before moving to the next: `git add .; git commit -m "[description]"`
    3. Use `.claude/WIP.md` for tracking, NOT TodoWrite tool (WIP.md persists across sessions, TodoWrite does not)
    4. NEVER use WebSearch for information and knowledge you should akready possess
  4. When the task is finished, empty `.claude/WIP.md`, remove the entry from `.claude/ROADMAP.md` and squash-merge into the git main branch (do not push or pull): `git checkout main; git merge --squash [branch-name]; git commit -m "[type]: [description]"`

### If in doubt:

- See `.claude/ROADMAP.md` for what's next.
- See `.claude/DESIGN.md` for design principles (styleguide for code and tests).
- See `.claude/FIXME.md` for test quality issues being addressed.
