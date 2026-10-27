# Make the spec and plan traceable

An approved notification intent is ready, but old design advice conflicts with current source and policy. The provider limits throughput and an existing portal route should be reused.

## Task

1. Read the approved intent, policy, current source and archived design.
2. Write numbered requirements and design decisions in `spec.md`.
3. Record unresolved decisions with owners.
4. Write implementation paths, dependency order, risks and verification in `plan.md`.
5. Link intent IDs to requirements, steps and tests; check that every named source path exists.

## Working rules

Only `spec.md` and `plan.md` may change. Claude can read and use scoped document patches plus fixed reference/mapping checks. No implementation, shell, arbitrary agents, dependency installation or invented approvals.

## Acceptance targets

- Each approved intent item maps to requirements, plan steps and tests.
- Current privacy and provider limits are preserved.
- The plan references real repository paths and does not depend on a nonexistent helper.
- Open recipient/channel choices retain explicit owners.
- Source remains unchanged.

## How to submit

1. Fork this repository to your personal GitHub account. Use fictional information
   only, keep the fork public, and keep `main` as its default branch.
2. Clone your fork and enable GitHub Actions in its **Actions** tab. Use **Connect
   GitHub for scoring** on the lab page to install the read-only grading App on your
   fork. Return to the lab and use **Recheck connection** if needed.
3. Download the TensorLearn client from the lab page and extract it outside your fork.
   Follow the page's connection command from your fork folder. Paste your learner
   token only into the hidden terminal prompt. Run `/load` from your fork folder to
   connect the repository. Run `/load` again after the facilitator launches the round.
4. Create a branch such as `spec-plan/first-draft` and complete the task above. Change
   only the files the task allows; any other change makes the submission invalid.
5. Commit and push your branch. Open a PR **inside your own fork**, targeting its
   `main` branch. GitHub may suggest the upstream repository: select your fork instead.
   Opening or updating this PR starts the checks automatically.
6. Keep the PR open. When ready, run **`/submit`** in the connected Claude Code session
   to submit that exact pushed revision for the current round. **No merge is required.**
7. Use `/check` or refresh the lab page to read the saved result. The Actions run and
   `lab-score/score.json` are useful feedback, but an Actions check alone does not
   submit your work or prove that the server saved a score.

A change to your answer requires a new commit, push, and explicit `/submit`. Keep
`main` unchanged: the grader compares your PR with the released starter.

## What is graded

The pinned grader in `.github/workflows/grade.yml` reads your files as data and runs
your code only in an isolated, offline container. Every check is a fixed rule; no AI
model judges your work. Your facilitator separately reviews clarity and reasoning.

- spec.md and plan.md fill every section; each intent item I-1 to I-4 is traced to a requirement and a test.
- The plan table is complete, the steps are ordered, and only real source paths are named.
- The release gate, privacy rules, provider limits and idempotency key are kept.
- Tests cover gating, privacy, duplicate retries and throughput; open decisions keep their owners.
- Adopting archived advice (portal redesign, upload-triggered notifications, the missing helper) caps the score at 25/100.
