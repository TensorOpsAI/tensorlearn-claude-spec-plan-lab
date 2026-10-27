# Make the spec and plan traceable

An approved notification intent is ready, but old design advice conflicts with current source and policy. The provider limits throughput and an existing portal route should be reused.

This lab follows *Write the intent*. The fictional clinic's results-ready notification now has an approved intent in `intent.md` (items I-1 to I-4, plus two open decisions). `inputs/current-policy.md` holds the current provider and privacy constraints; `inputs/archived-design.md` is an old proposal that was never approved.

Terms used below:

- **Traceable:** each intent item can be followed through a numbered requirement, a plan step and a test, and every file path you name really exists (or is clearly marked as a new file).
- **Release gate:** the rule from I-1 that a patient is notified only after a doctor has reviewed and released the result.
- **Idempotency key:** the value that makes a retried send safe to repeat. `inputs/current-policy.md` sets it to the released result version, so one released version is never delivered twice.

**What you'll practise:** planning with Claude Code before any code is written: turning an approved intent into a spec and an ordered plan, and checking what Claude proposes against the repository instead of trusting old design notes.

**In the course slides:** Chapter 1, Lessons 2 and 3 (Requirements and design; Plan mode). The slides number requirements R1, R2 and concerns C1; here the approved items are I-1 to I-4 and you choose your own requirement IDs.

## Task

1. Read the approved intent, policy, current source and archived design.
2. Write numbered requirements and design decisions in `spec.md`.
3. Record unresolved decisions with owners.
4. Write implementation paths, dependency order, risks and verification in `plan.md`.
5. Link intent IDs to requirements, steps and tests; check that every named source path exists, or is explicitly marked as a proposed new file.

A good way to work: use plan mode (press Shift+Tab until the footer shows plan mode) while Claude reads the inputs and drafts the structure, and ask it to check every path it proposes with `ls` before it goes into a document. The tests don't exist yet: in both documents, describe each test by a name and what it checks; don't create test files. There is no code to run in this lab. To list every source path you named: `grep -on 'src/[A-Za-z0-9_./-]*\.mjs' spec.md plan.md`.

## Working rules

Only `spec.md` and `plan.md` may change. Claude can read the repository, list files and edit these two documents. No implementation, new source or test files, dependency installation or invented approvals.

## Acceptance targets

- Each approved intent item maps to requirements, plan steps and tests.
- Current privacy and provider limits are preserved.
- The plan references real repository paths and does not depend on a nonexistent helper.
- Open recipient/channel choices retain explicit owners.
- Source remains unchanged.

## Done when

- Every heading from the starter templates is still there and has content under it.
- The traceability table in `spec.md` has a row for each of I-1 to I-4, with a requirement and a test.
- Every `src/...` path from the `grep` above either exists (check with `ls`) or is called a new file on the same line.
- Both open decisions appear with their owners, and `git status` shows only `spec.md` and `plan.md` changed.

## Graded format

- Keep the template headings exactly: `## Requirements`, `## Design`, `## Open decisions and owners` and `## Traceability` in `spec.md`; `## Ordered steps`, `## Paths and dependencies` and `## Risks and verification` in `plan.md`. Write at least a full sentence under each.
- `spec.md` traceability table: one row per intent item, with the first cell starting with its ID (`I-1` to `I-4`) and the Requirement and Test cells filled.
- `plan.md` table: at least 4 rows with Requirement, Step and Test filled. In *Existing path*, put only a file that exists in `src/`, or leave it empty or `-`.
- *Ordered steps* is a numbered list (`1.`, `2.`, ...) of at least 3 steps.
- Name both existing source files where the plan reuses them. A proposed file must be called new on the same line (for example "new file `src/service/notify.mjs`"); never present the archived helper as existing.
- Write limits as digits (for example 50, not fifty). State the release gate and the idempotency key, and say in one sentence that clinical content stays out of notifications and logs.
- If a line mentions archived advice (portal redesign, notifying on upload, the archived helper), say on that line that it is rejected, excluded or not used. Otherwise it counts as adopted and caps the score at 25/100.

## How to submit

1. Fork this repository to your personal GitHub account. Use fictional information
   only, keep the fork public, and keep `main` as its default branch. In your fork's
   **Actions** tab, click **I understand my workflows, go ahead and enable them** if shown.
2. On the lab page, use **Connect GitHub for scoring** to install the read-only grading
   App on your fork, then **Recheck connection**.
3. Download the TensorLearn connector from the lab page and extract it outside your fork.
   From your fork folder, run the page's `--code` connection command and paste your token
   only into the hidden terminal prompt. This opens a Claude Code session connected to the lab.
4. In that session, run `/load`. Run `/load` again after your instructor launches the round.
5. Create a branch such as `spec-plan/first-draft` and complete the task above. Change only the
   files the task allows: any other change, including `CLAUDE.md`, `.claude/` settings or
   agents, or notes files, makes the submission invalid.
6. Commit and push your branch. Open a PR **inside your own fork**, targeting its `main`
   branch (GitHub may suggest the upstream repository: select your fork instead). Check
   that **Check spec-plan submission** starts in the PR's checks. Keep the PR open; no merge
   is required.
7. Run **`/submit`** in the connected Claude Code session, then `/check` (or refresh the
   lab page) to read your saved score. The Actions run is useful feedback, but it does not
   submit your work.

A change to your answer needs a new commit, push and `/submit`. Keep `main` unchanged:
the grader compares your PR with the released starter.

## What is graded

The pinned grader in `.github/workflows/grade.yml` reads your files as data and runs your
code only in an isolated, offline container. Every check is a fixed rule; no AI model
judges your work. Your score is out of 100. Your facilitator separately reviews
clarity and reasoning.

- spec.md and plan.md fill every section; each intent item I-1 to I-4 is traced to a requirement and a test.
- The plan table is complete, the steps are ordered, and every source path named either exists or is clearly marked as new.
- The release gate, privacy rules, provider limits and idempotency key are kept.
- Tests cover gating, privacy, duplicate retries and throughput; open decisions keep their owners.
- Adopting archived advice (portal redesign, upload-triggered notifications, the missing helper) caps the score at 25/100.
