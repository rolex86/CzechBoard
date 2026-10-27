# CzechBoard – development baseline

This is a personal Czech-first fork of HeliBoard, currently at research/test-corpus stage. **No modified APK or Czech autocorrection change has been built yet.**

## Goals
- Keep colloquial Czech words as typed (e.g. `celej`, `dobrej`, `zvyklej`).
- Correct adjacent-key typos and missing diacritics while keeping user style.
- Support offline personal dictionary imports (verify upstream support and format before changing code).
- Build and test independent APK on a Pixel 8 Pro without replacing the original keyboard.

## Security baseline
- No `android.permission.INTERNET` in the checked upstream app manifest. Validate the *merged* release manifest and dependencies on every build.
- Upstream declares `READ_CONTACTS`; audit necessity before claiming a minimal-permission keyboard.
- Avoid typing real credentials until release build, signature, and privacy behavior are verified.
- A GitHub fork alone is not a security audit.

## Test data
`tests/typo-cases.tsv` contains expected outputs, **not passing tests**. Keep original text alongside corrected intent; context-sensitive edits need sentence-level evaluation.

## Next engineering steps
1. Determine actual Czech dictionary format and upstream correction scoring behavior.
2. Build baseline APK unmodified and verify installation side-by-side using an isolated application ID and provider authorities.
3. Add colloquial vocabulary and regression tests, then measure against baseline and SwiftKey.
4. Only then adapt scoring/word boundary correction as needed.

Upstream: https://github.com/HeliBorg/HeliBoard
