🛡️ SurakshaSetu — Voice-First Vernacular Anti-Fraud Assistant

Bolo • Jaancho • Bachao — Speak • Check • Stay safe

Offline-first, voice-first scam checker for Hindi, Tamil and Telugu speakers. Built for elderly, low-literacy and first-time UPI users on 2 GB-RAM Android phones. Submission for Hack for Social Cause · Theme: Digital Safety & Fraud Awareness · State: Tamil Nadu.

The problem

Cyber fraud cost Indians ₹19,813 Cr in 2025 (₹1,897 Cr in Tamil Nadu). Most safety apps are text-heavy, English-first and need internet — exactly what the most-targeted users lack.

How it works
SPEAK or SHARE — long-press the mic and describe the call/SMS in your language, or share the message/link.
CHECK on the phone — a 3-layer Verdict Engine runs fully offline:
L1 known-threat lookup (hashed numbers, UPI IDs, URLs; Bloom filter)
L2 scam-script intent classifier (lottery, KYC, digital arrest, refund, loan, OTP)
L3 SMS / link heuristics (look-alike domains, urgency, OTP asks)
ACT in seconds — spoken verdict: 🔴 RED stop · 🟠 AMBER verify · 🟢 GREEN none known, plus one-tap 1930 and Family Guardian SMS.
Key ideas
Feature	What it does
Intent-over-transcript	Detects what the scam is about, so noisy dialect speech still works
Suraksha Mitra Mesh	Volunteers relay Ed25519-signed threat packs via Bluetooth / Wi-Fi / QR
Family Guardian	Opt-in SMS to a trusted relative on RED verdicts (works on 2G)
Scam Drills	Voice role-plays that build the habit of hanging up
Repository layout
android/       Kotlin app skeleton (Jetpack, Android 7+, target APK < 60 MB)
reference/     Python reference implementation of the Verdict Engine (for tests, corpus work, benchmarking)
tools/         Threat-pack builder / signer / verifier (Ed25519)
data/sample/   Synthetic sample data (NO real victims, NO real numbers)
docs/          Architecture, threat-pack format, privacy
tests/         pytest suite
Quick start (reference engine)
bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
pytest -q
python -m surakshasetu.cli "Dear customer your SBI account will be blocked today. Update KYC http://sbi-kyc-update.xyz"

(Run from the repo root with PYTHONPATH=reference, or pip install -e ..)

Threat packs
bash
python tools/pack_tool.py keygen  --out keys/
python tools/pack_tool.py build   --csv data/sample/known_threats.csv --out pack.json
python tools/pack_tool.py sign    --pack pack.json --key keys/private.pem --out pack.signed.json
python tools/pack_tool.py verify  --pack pack.signed.json --pub keys/public.pem
Privacy

On-device processing, explicit consent, no audio stored, 0 bytes of voice/SMS leave the device. Reports to cyber-crime cells are opt-in and anonymised. Aligned to the DPDP Act, 2023. See docs/PRIVACY.md.

Status & honesty note

Percentages and timings (< 3 s verdict, ≥ 90 % recall) are pilot targets, not measured results. SurakshaSetu never says "100 % safe" — GREEN means no known threat. If you've lost money, call 1930 or visit cybercrime.gov.in.

Roadmap
 Phase 1 — Scam-script corpus (seed), reference engine
 Phase 2 — Android MVP: voice UI + Verdict Engine
 Phase 3 — Mesh & signed-pack sync, Family Guardian
 Phase 4 — SHG / CSC field pilot in Tamil Nadu
Contributing

See CONTRIBUTING.md. Native-speaker help for Tamil/Telugu/Hindi scam phrases is especially welcome.

Licence

MIT — see LICENSE.
