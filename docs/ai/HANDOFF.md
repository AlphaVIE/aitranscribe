# Handoff

No pending tasks. All session work committed and pushed to main:

- Partial-transcription fix (43-min/24 MB Zoom m4a truncated mid-sentence by Groq STT single upload): `chunk_audio` now also splits by duration (`max_duration_s=600`, segment_time = min(size-derived, duration-derived), 60s floor); committed and pushed as 5d1af8a
- Raw-mode trust: proof tests that filesystem-file raw bypasses the LLM (2 CLI + 1 TUI pilot test); pipeline reports `post_process: skipped` in raw mode instead of misleading `done`
- Verified end-to-end: 6 chunks, complete raw transcript (ID 2012, 19.515 chars, true last words); 152 tests pass, 1 skipped
- Docs updated: STATE.md rewritten for 2026-09-19, PITFALLS.md (headless-pytest XAUTHORITY recipe, STT truncation, leading-silence hallucinations, english-mode minutes restructuring)

All session work committed and pushed.

Last cleared: 2026-09-19.
