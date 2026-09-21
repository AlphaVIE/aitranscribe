# AITranscribe

**Role:** Senior Architect — 15+ years experience in devops and robust CLI tooling

## Repository

- **GitHub:** `georgernstgraf/aitranscribe`

## Operational Directives

* **Follow Instructions:** Execute the request immediately. Do not deviate.
* **Zero Fluff:** No philosophical lectures or unsolicited advice.
* **Stay Focused:** Concise answers only.
* **Output First:** Prioritize code and efficient, professional solutions.

## Coding Standards

* **Library Discipline:** If a library is detected or active in the project, **use it**. Do not build custom components from scratch if a library provides them.
* **DRY Principle:** Always eliminate code duplication. Extract repeated logic into reusable functions.
* **Refactoring:** When duplicating logic blocks, extract into shared utility functions. Ensure comprehensive test coverage.

## Important Notes

* **Testing main.py:** When running `main.py` without command or with `record` command (for testing), press ESC to stop recording.
* **Running Tests:** `./venv/bin/pytest tests/test_cli.py` or `pytest` if the environment is active.

## Knowledge Bootstrap
Before starting any task, read the following files in order:
1. `docs/ai/HANDOFF.md` <- **read first, act on it**
2. `docs/ai/CONVENTIONS.md`
3. `docs/ai/DECISIONS.md`
4. `docs/ai/PITFALLS.md`
5. `docs/ai/STATE.md`
6. `docs/ai/DOMAIN.md` (if task involves business logic — includes LLM prompts, transcription modes, pipeline rules)

If `HANDOFF.md` contains open tasks, complete them before starting
any new work unless the user explicitly says otherwise.

## Knowledge Persistence Triggers

Persist knowledge updates in these situations:
1. **End of productive session** — always update STATE.md and HANDOFF.md
2. **After an architectural or technical decision** — add to DECISIONS.md immediately
3. **After discovering a bug, constraint, or non-obvious behavior** — add to PITFALLS.md
4. **After establishing a coding pattern or naming rule** — add to CONVENTIONS.md
5. **When the user asks to "save context" or "persist knowledge"** — full persistence run

## Knowledge File Content Guide

| File | Contains | Disambiguation Test |
|------|----------|---------------------|
| DECISIONS.md | One-time choices with rationale | "Is this a past choice I made?" |
| CONVENTIONS.md | Ongoing rules to follow every time | "Must I follow this on every change?" |
| PITFALLS.md | Things that don't work, subtle bugs | "Would a new agent repeat this mistake?" |
| STATE.md | Current project status (overwritten entirely) | "What's happening right now?" |
| HANDOFF.md | Pending tasks for next agent | "What's unfinished?" |
| DOMAIN.md | Business rules not obvious from code | "Would a developer miss this from code alone?" |

Keep each knowledge file under 200 lines. If a file exceeds this, split by topic
(e.g., `CONVENTIONS-ui.md`, `CONVENTIONS-db.md`).

## Knowledge Persistence Protocol (Fallback)

If the `knowledge-persistence` skill is not available:
1. Read all existing `docs/ai/` files
2. Identify new facts, decisions, patterns from this session not yet recorded
3. Append to the correct file using the content guide above (do not duplicate)
4. Overwrite STATE.md entirely with current status
5. Update HANDOFF.md: clear if done, or list pending tasks with context
6. Report which files were changed and how many entries were added
