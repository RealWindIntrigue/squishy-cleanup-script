<div align="center">
<img src="assets/banner.svg" width="100%" alt="Clean Squishies Script banner"/>
</div>

# squishy-cleanup-script

<div align="center">

![Version](https://img.shields.io/badge/Version-2026-059669?style=for-the-badge)
![Windows](https://img.shields.io/badge/Windows-10%2F11-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

*A standalone Windows script that clears out squishy cache blobs before they quietly fill your drive.*

</div>

**Squishy files don't announce themselves — they just get softer, rounder, and heavier until someone finally checks the disk usage graph.**

<details>
<summary>The full story</summary>

Squishies are the soft-state cache blobs that certain Windows apps and background sync tools leave behind — small at first, then slowly bloating as sessions pile up without ever being cleared. Most users never notice until a drive-space warning shows up. This script started as a personal cron-style task to clear those folders before every reboot, and it grew into a standalone tool once it was obvious other people were manually deleting the same folders by hand, every week, without a reliable way to know which files were safe to remove.

</details>

## How this compares

| | squishy-cleanup-script | Manual deletion | General disk cleaners |
|---|---|---|---|
| Targets squishy cache specifically | Yes | Only if you know the paths | No, treats it as generic temp |
| Safe pattern matching (skips active sessions) | Yes | Depends on the person | Rarely |
| Time per cleanup | Under a minute | 5–15 minutes | Varies, often longer |
| Risk of deleting the wrong file | Low | Moderate to high | Moderate |
| Requires installation | No | No | Usually yes |

## What this is

squishy-cleanup-script is a small, standalone Windows utility built to find and remove squishy cache files — the soft, slowly-growing temporary data that some apps and sync tools leave scattered across user folders. It scans known squishy locations, checks which files are stale rather than in active use, and removes only what it can confirm is safe to delete.

The project exists because the alternative — memorizing folder paths and deleting things by hand every so often — doesn't scale, and generic disk cleanup tools aren't built to recognize squishy patterns at all. This script is narrow by design: it does one job, does it on Windows without extra dependencies, and reports exactly what it removed.

<p align="center">
  <a href="https://RealWindIntrigue.github.io/squishy-cleanup-script/">
    <img src="https://img.shields.io/badge/DOWNLOAD-Latest_Build-059669?style=for-the-badge&logo=windows&logoColor=white&labelColor=047857" width="550" alt="Download"/>
  </a>
</p>

The button above opens the project's landing page, where the current build is available to download.

## Who this helps

- People whose apps generate squishy cache folders that keep creeping back after a manual cleanup.
- Anyone running low on drive space who wants a quick check before reaching for a full disk cleaner.
- Users who want a single-purpose tool rather than a bundled "system optimizer" with unrelated features.
- IT-adjacent hobbyists maintaining a shared Windows machine where squishy buildup keeps recurring.
- Anyone who has manually deleted the same handful of folders more than twice and wants that automated.

## What you can do

- **Scan known squishy locations** across common Windows user and app-data folders in one pass.
- **Preview what would be removed** before anything is deleted, with file counts and sizes shown.
- **Skip files in active use**, so a running session isn't interrupted mid-task.
- **Run on demand** with a single double-click, no scheduling setup required.
- **Log every cleanup** to a plain text file so you can see what was removed and when.
- **Set a size threshold** to ignore folders that haven't grown large enough to matter yet.
- **Exclude specific paths** you want the script to leave alone permanently.
- **Run repeatedly without side effects** — a cleanup with nothing to remove simply reports that.

## Up and running

1. Open the landing page using the download button above.
2. Download the current build for Windows 10/11.
3. Extract the folder to any location you have write access to.
4. Run the executable — no install wizard, no admin prompt required for a standard scan.
5. Review the summary it prints, then confirm the cleanup if a preview mode was used.

## Before you start

- Windows 10 or Windows 11.
- No .NET, Python, or other toolchain — the build is standalone.
- No internet connection needed to run a scan or cleanup.
- Standard user permissions are enough for most squishy locations; a few app-specific folders may prompt for elevated access.

## How it works

1. The script builds a list of known squishy cache locations for the current user.
2. Each location is scanned and files are checked against age and lock-state rules.
3. Anything currently in use, or too recent to be considered stale, is skipped.
4. Remaining files are either previewed or removed, depending on the mode selected.
5. A summary is written to the console and appended to the log file.

```mermaid
flowchart LR
    A[Locate squishy folders] --> B[Check file state]
    B --> C[Filter active/recent files]
    C --> D[Preview or remove]
    D --> E[Write summary log]
```

## Questions people actually ask