# Project State

Current status as of 2026-09-21.

## Current Focus
- Quoted audio-file paths in the TUI and CLI are normalized before existence checks on branch `fix/quoted-audio-path`.
- PR #76 is open from `AlphaVIE/aitranscribe` to `georgernstgraf/aitranscribe`. PR #75 was closed automatically when its head branch was renamed.
- Branch names must never contain `codex`, `AI`, `KI`, `ChatGPT`, or similar assistant/tool branding. This preference is also stored globally in `C:\Users\Arman\.codex\AGENTS.md`.

## Verification
- The reported Windows audio path exists locally; its quoted form previously failed the TUI existence check.
- New focused tests: 3 passed (`tests/test_cli.py -k "quoted_path or normalize_file_path"`).
- Full Windows suite is not green because existing SQLite tests attempt to unlink still-open temporary databases (`WinError 32`); first failure occurs after 57 passes in `tests/test_cli.py`.

## Working Tree
- Pre-existing user changes in `config.example` and untracked `~/` remain untouched.
