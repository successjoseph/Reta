# Reta

## Table of Contents
- [About](#about)
- [Repository Contents](#repository-contents)
- [Proposed Architecture](#proposed-architecture)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Authors and License](#authors-and-license)

## About

Reta contains no implemented application code — it is a planning-stage repository for a proposed Android app, also called "Reta." GitHub does not detect a primary language because there is no source tree yet, only design documentation. Reta is envisioned as an on-device automation app that records, stores, and replays UI interactions (taps, swipes, typed input, delays) directly on an Android device, triggerable hands-free via a local wake-word ("Reta"), and built to run fully offline for privacy. Note: `README.txt` in this repository is present but empty — the actual project write-up lives in `Creation-Logs/text/idea.txt` instead.

## Repository Contents
- `README.txt` — empty (0 bytes).
- `Creation-Logs/text/idea.txt` — the full concept document: problem statement, proposed solution, core features (recording, sequence storage/management, playback with speed/delay overrides, voice-triggered hotword detection with local STT and fuzzy sequence matching, scheduling via AlarmManager/WorkManager, and a local-only privacy/logging model with 7-day raw logs auto-summarized into `summary.json`), a proposed technical architecture table (Kotlin, AccessibilityService + InputManager, PocketSphinx/Porcupine + Vosk, Room/SQLite, WorkManager, optional embedded Ktor/Jetty server), a sketched Android project directory layout, and a suggested development timeline.
- `.gitignore` — present but empty (0 bytes).

## Proposed Architecture
As described in `idea.txt`, the intended stack is: Kotlin for the Android app; an `AccessibilityService` + `InputManager`-based recorder/player; on-device hotword detection (PocketSphinx or Porcupine) with Vosk for local speech-to-text; Room (SQLite) for storing sequences, metadata, and logs; `AlarmManager`/`WorkManager` for scheduling; and an optional local-only HTTP trigger server (Ktor/Jetty) for network-triggered runs. None of this has been implemented in the repository yet.

## Roadmap
`idea.txt` lays out an explicit phased development timeline (~6–7 weeks estimated to MVP):
1. **Phase 0 — Setup (1 week):** project scaffolding, Room DB, permissions/accessibility onboarding, basic UI skeleton.
2. **Phase 1 — Recording & Playback Core (2 weeks):** Accessibility-based recorder, reliable `PlayerService`, Room persistence.
3. **Phase 2 — Voice Trigger & STT (1.5 weeks):** hotword detection, Vosk-based local STT, command-to-sequence matching.
4. **Phase 3 — Scheduling, Quick Tile & Logs (1 week):** local scheduler, Quick Settings tile/notification actions, daily-log + weekly-summary pipeline.
5. **Phase 4 — Polish & QA (1 week):** UI polish, edge cases, battery profiling, permission UX, privacy audit (no audio retention).

Stretch goals noted in the doc include opt-in encrypted cloud sync, a visual flowchart-based macro editor, and a community sequence marketplace.

## Contributing
This is a private, personal planning repository — notes for future-you rather than an open project.

## Authors and License
**Author:** [successjoseph](https://github.com/successjoseph)
No license file included in this repository — all rights reserved by default.
