# Handoff

## 2026-09-21 session: repo hygiene dirt cleanup (#74, pushed as e6ea800)
- `skills/` symlink removed (was a link into opencode-helpers, not a copy); stale skills/ mandates in PITFALLS/DECISIONS updated to global skill resolution.
- Staged AGENTS.md lean rewrite committed (was already the effective instructions).
- Stale 4-line tui.py select/refresh tweak reverted (origin TUI is far newer).
- Incident: `rm -rf skills/` with trailing slash emptied the helper repo's skills first — fully recovered via `git checkout`, nothing pushed there. Pitfall recorded.
- Tree fully clean. Issue #74 CLOSED per owner.

## 2026-09-21 session: prompt transplant from polished-recognition (#73 CLOSED, pushed as 58b1301)
- `[post_process.translate]` default hardened to the sister project's #56 clause; `[post_process.system]` gains the injection-guard line (restores pre-port core.py protection).
- `_load_prompts()` auto-upgrades pristine legacy values (full-pristine files rewritten, customized files upgraded in memory with notice); 5 new tests in tests/test_cli.py, 2 expectations updated.
- Verification: full suite run on fresh venv under `xvfb-run` (1b0c559 knowledge): 156 passed, 1 skipped, 1 failed — the failure (`test_cli_file_missing_arg`) is pre-existing/environmental (needs valid GROQ_API_KEY in real config; fails identically on unmodified baseline). Issue #73 CLOSED per owner.
- Pre-existing uncommitted dirt NOT touched: AGENTS.md, tui.py modifications + untracked skills/.

Previous state:
No pending tasks. All session work committed and pushed to main:

- Partial-transcription fix (43-min/24 MB Zoom m4a truncated mid-sentence by Groq STT single upload): `chunk_audio` now also splits by duration (`max_duration_s=600`, segment_time = min(size-derived, duration-derived), 60s floor); committed and pushed as 5d1af8a
- Raw-mode trust: proof tests that filesystem-file raw bypasses the LLM (2 CLI + 1 TUI pilot test); pipeline reports `post_process: skipped` in raw mode instead of misleading `done`
- Verified end-to-end: 6 chunks, complete raw transcript (ID 2012, 19.515 chars, true last words); 152 tests pass, 1 skipped
- Docs updated: STATE.md rewritten for 2026-09-19, PITFALLS.md (headless-pytest XAUTHORITY recipe, STT truncation, leading-silence hallucinations, english-mode minutes restructuring)

All session work committed and pushed.

Last cleared: 2026-09-19.
