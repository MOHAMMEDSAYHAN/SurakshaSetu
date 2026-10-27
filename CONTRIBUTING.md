# Contributing to SurakshaSetu

Thanks for helping protect people from fraud!

## Good first contributions
- **Scam phrases** in Tamil / Telugu / Hindi (add to `data/sample/scam_scripts.jsonl`). Use *synthetic* text — never paste real victims' messages, numbers or UPI IDs.
- **Test cases** for false positives (legit bank / OTP / delivery messages).
- **Voice prompts**: human-voice recordings for RED / AMBER / GREEN verdicts.

## Workflow
1. Fork → branch (`feat/...`, `fix/...`) → PR against `main`.
2. Run `pytest -q` before pushing. CI must be green.
3. Keep the intent model < 5 MB and avoid heavy dependencies in `android/`.

## Rules
- No real personal data in the repo. Sample data is synthetic.
- No code that sends audio or SMS content off-device.
- Never message the user that something is "100% safe".

By contributing you agree your work is licensed under the MIT licence.
