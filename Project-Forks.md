There are several forks, derivatives, and downstream projects based on the original Synergy project.

# Fork History

# Summary

- 2001: Synergy was [born](../History)
- 2018: Synergy forked to Barrier
- 2021: Barrier forked to Input Leap
- 2024: Deskflow became upstream of Synergy

# Full details

Accurate as of Oct 2024.

| Project | Base | Started | Type | Status |
| --- | --- | --- | --- | --- |
| Deskflow | Synergy v1.15 | 2024 | Upstream | Active |
| Synergy (>v1.15) | Deskflow | 2024 | Downstream | Active |
| Synergy (v3.x) | Synergy v1.x | 2023 | Downstream | Active |
| Input Leap | Barrier v2.4 | 2021 | Fork | Active |
| Barrier | Synergy v1.9 | 2018 | Fork | Superseded* |
| Synergy (<=v1.15) | - | 2001 | Original | Superseded |

\* As of Oct 2024, the last commit on Barrier was `653e4ba` (2 years ago). The general view is that it is a dead project superseded by Input Leap.

# Comparison

Only comparing active projects. Accurate as of Oct 2024.

| | Deskflow | Input Leap | Synergy (v1.x) | Synergy (v3.x) |
| --- | --- | --- | --- | --- |
| License | GPLv2 | GPLv2 | GPLv2 | Proprietary |
| Stability | Leading edge | Stable | Stable | Stable |
| Legacy systems | No | Yes | Yes | No |
| Community-driven | Yes | Yes | No | No |
| Code reviews | Required | Sometimes | Required | Required |
| Funding | Sponsored | None | Customers | Customers |
| Customer code* | No | No | Yes | Yes |
| GUI features | Original | Original | Original | Extended |
| GUI technology | Qt | Qt | Qt | Electron |
| Auto-discovery | No | Yes** | No | Yes** |

\* Customer code in Synergy 1 includes code to enable customers to enter a license key. Synergy 3 adds a small layer of proprietary code in a separate unlinked binary for customers who want an easier config experience and other features that aren't of interest to the Deskflow community but are of interest to Synergy customers.

\** Input Leap (and Barrier) use the legacy auto-discovery from Synergy (Bonjour) which was removed from Synergy due to issues with stability. Deskflow does not intend to develop an auto-discovery feature. Synergy 3 uses mDNS for auto-discovery.

See also:
- [[History]]
- [[Relationship with Synergy]]