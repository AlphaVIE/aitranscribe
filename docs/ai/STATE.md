# Project State

Current status as of 2026-09-21.

## Current Focus
- Quoted audio-file paths in the TUI and CLI are normalized before existence checks on branch `codex/fix-quoted-audio-path`.
- PR #75 is open from `AlphaVIE/aitranscribe` to `georgernstgraf/aitranscribe`.

## Verification
- The reported Windows audio path exists locally; its quoted form previously failed the TUI existence check.
- New focused tests: 3 passed (`tests/test_cli.py -k "quoted_path or normalize_file_path"`).
- Full Windows suite is not green because existing SQLite tests attempt to unlink still-open temporary databases (`WinError 32`); first failure occurs after 57 passes in `tests/test_cli.py`.

## Working Tree
- Pre-existing user changes in `config.example` and untracked `~/` remain untouched.
