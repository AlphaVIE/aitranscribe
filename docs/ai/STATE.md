# Project State

Current status as of 2026-09-19.

## Current Focus
Partial-transcription bug (43-min Zoom m4a, 24 MB) diagnosed and fixed. Root cause was STT-side truncation of very long single uploads, proven by a raw-mode comparison run (raw 19.056 chars = english 18.805 chars, same mid-sentence cutoff). `chunk_audio` now also splits by duration. Full meeting transcribes completely (raw ID 2012, 19.515 chars, ends with the recording's actual last words). 152 tests pass, 1 skipped.

## Completed (this cycle)
- [x] Raw-mode suspicion cleared: `process_file_for_tui` with `pre_process_mode='raw'` provably bypasses the LLM (2 new CLI proof tests, 1 TUI pilot test clicking the raw radio into `collect_settings`); pipeline now reports `post_process: skipped` instead of misleading `done` in raw mode
- [x] `chunk_audio(file_path, max_size_mb=25, max_duration_s=600)`: segment_time = min(size-derived, duration-derived even split), 60s floor kept; ffprobe failure falls back to size-only decision (small-file passthrough preserved); matches README's "25 MB or 10-minute segments" claim
- [x] 3 new duration-chunking tests in test_core.py (small-but-long splits, duration-vs-size precedence, within-both-limits passthrough); all pre-existing segment-time expectations unchanged
- [x] Verified end-to-end: 6 chunks, per-chunk volumedetect (chunk0 = leading silence → Thank-you hallucinations), chunk5 (4.8s) holds the true last words; /tmp chunks cleaned up by pipeline
- [x] PITFALLS.md: headless-pytest XAUTHORITY recipe, STT long-upload truncation, leading-silence hallucinations, english-mode minutes restructuring

## Pending
- None open (changes uncommitted — commit/push on user request)

## Blockers
- None

## Next Session Suggestion
Optional: silence-trimming or hallucination filtering for leading-silence chunks; prompt tuning if english-mode minutes style is unwanted (currently restructures + relocates passages).
