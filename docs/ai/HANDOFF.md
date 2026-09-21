# Handoff

## 2026-09-21 session: prompt transplant from polished-recognition (#73, pushed as 58b1301)
- `[post_process.translate]` default hardened to the sister project's #56 clause; `[post_process.system]` gains the injection-guard line (restores pre-port core.py protection).
- `_load_prompts()` auto-upgrades pristine legacy values (full-pristine files rewritten, customized files upgraded in memory with notice); 5 new tests in tests/test_cli.py, 2 expectations updated.
- Verification: full pytest NOT runnable on this host (no venv/pytest/deps/X) — verified via py_compile + a 28-check harness exec'ing the real prompt functions from main.py (template validity, builders, pristine/customized/fully-custom migration, validation). Full suite (`venv/bin/pytest`) still needs a run on the dev machine.
- Issue #73 left OPEN pending that full-suite run.
- Pre-existing uncommitted dirt NOT touched: AGENTS.md, tui.py modifications + untracked skills/.

Previous state:
No pending tasks. All session work committed and pushed to main:

- Partial-transcription fix (43-min/24 MB Zoom m4a truncated mid-sentence by Groq STT single upload): `chunk_audio` now also splits by duration (`max_duration_s=600`, segment_time = min(size-derived, duration-derived), 60s floor); committed and pushed as 5d1af8a
- Raw-mode trust: proof tests that filesystem-file raw bypasses the LLM (2 CLI + 1 TUI pilot test); pipeline reports `post_process: skipped` in raw mode instead of misleading `done`
- Verified end-to-end: 6 chunks, complete raw transcript (ID 2012, 19.515 chars, true last words); 152 tests pass, 1 skipped
- Docs updated: STATE.md rewritten for 2026-09-19, PITFALLS.md (headless-pytest XAUTHORITY recipe, STT truncation, leading-silence hallucinations, english-mode minutes restructuring)

All session work committed and pushed.

Last cleared: 2026-09-19.
