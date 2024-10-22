There are several forks, derivatives, and downstream projects based on the original Synergy project.

- [History](#history-summary)
- [Fork List](#fork-list)
- [Comparison (high-level)](#comparison-high-level)
- [Technical Differences](#technical-differences)

# History (summary)

- 2001: Synergy was [[born|History]]
- 2018: Synergy forked to Barrier
- 2021: Barrier forked to Input Leap
- 2024: Deskflow became upstream of Synergy

See also: [[Full history|History]]

## Fork List

Accurate as of Oct 2024.

| Project | Base | Started | Type | Status |
| --- | --- | --- | --- | --- |
| Deskflow | Synergy v1.15 | 2024 | Upstream | Active |
| Synergy (>v1.15) | Deskflow | 2024 | Downstream | Active |
| Synergy (v3.x) | Synergy v1.x | 2023 | Downstream | Active |
| Input Leap | Barrier v2.4 | 2021 | Fork | Active |
| Barrier | Synergy v1.9 | 2018 | Fork | Superseded* |
| Synergy (<=v1.15) | - | 2001 | Original | Superseded |

\* As of Oct 2024, the last commit on Barrier was `653e4ba` (2 years ago). The general view is that it is an inactive project superseded by Input Leap.

## Comparison (high-level)

Only comparing active projects.

Accurate as of Oct 2024.

| | Deskflow | Input Leap | Synergy (v1.x) | Synergy (v3.x) |
| --- | --- | --- | --- | --- |
| License | GPLv2 | GPLv2 | GPLv2 | Proprietary |
| Stability | Leading edge | Stable | Stable | Stable |
| Legacy systems | No | Yes | Yes | No |
| Community-driven | Yes | Yes | No | No |
| Funding | Sponsored | None | Customers | Customers |
| Customer code | No | No | Yes* | Yes* |
| GUI features | Original | Original | Original | Extended |
| GUI technology | Qt | Qt | Qt | Electron |
| Auto-discovery | No | Yes** | No | Yes** |
| Synergy protocol | Yes | No | Yes | Yes |
| Barrier protocol | Yes | Yes | No | No |

\* Customer code in Synergy 1 includes code to enable customers to enter a license key. Synergy 3 adds a small layer of proprietary code in a separate unlinked binary for customers who want an easier config experience and other features that aren't of interest to the Deskflow community but are of interest to Synergy customers.

\** Input Leap (and Barrier) use the legacy auto-discovery from Synergy (Bonjour) which was removed from Synergy due to issues with stability. Deskflow does not intend to develop an auto-discovery feature. Synergy 3 uses mDNS for auto-discovery.

## Technical Differences

There are some technical differences between Deskflow and Input Leap. We don't believe that this makes one better than the other; they are simply different technical approaches that are important to study and understand. The differences are often driven by community preference and project philosophy. The communities for each project are made up of both programmers and non-programmer contributors.

Accurate as of Oct 2024.

| | Deskflow | Input Leap |
| --- | --- | --- |
| Code reviews | Required | Sometimes |
| Dependencies | CMake [`FetchContent`](https://cmake.org/cmake/help/latest/module/FetchContent.html) | [Git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) |
| Qt support (minimum) | Qt 6 | Qt 5 |
| Depend on [`libei`](https://gitlab.freedesktop.org/libinput/libei) | Required | Optional |
| Depend on [`libportal`](https://github.com/flatpak/libportal) | Required | Optional |
| ARM64 support | Linux + macOS | macOS only |

See also:
- [[History]]
- [[Relationship with Synergy]]