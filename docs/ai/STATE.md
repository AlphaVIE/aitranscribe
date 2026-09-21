# Project State

Current status as of 2026-09-21.

## Current Focus
- PR #77 (`fix/audio-chunking-windows`) fixes large media preparation and misleading FFmpeg duration errors on Windows. It is independent of open PR #76 for quoted file paths.
- The reported `interview.mp3` is a 2.36 GiB MP4 container with H.264 video and AAC audio. Large filesystem inputs are converted directly to 32 kbps audio before chunking, without copying the video to a second 2.36 GiB temp file.
- FFmpeg 9.0.1 was installed locally via WinGet. Existing terminal sessions need a restart to see the updated PATH.

## Verification
- `tests/test_core.py`: 28 passed.
- Focused core/CLI tests: 26 passed.
- Local preparation of the reported file: 2,538,059,829-byte source -> 9,368,313-byte MP3 audio -> four chunks of roughly 2.34 MB. No STT or LLM request was made.
- The full Windows suite has known unrelated SQLite cleanup failures (`WinError 32`).

## Working Tree
- This fix lives in a separate worktree from the one used for PR #76.
