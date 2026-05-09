# Privacy Regulation Watcher — Routines spec sheet

**For:** registration in Claude Code on the web → Routines
**Confirmed by:** Ajit Sahu, Director of Engineering
**Spec date:** 2026-05-09
**Repository:** `ajitbubu/policy-detection-agent`

These three Routines run the `privacy-regulation-watcher` subagent on the configured cadences. State files live under `regulation-watch/` in the repo root, so the cloud sandbox finds them on each run after cloning.

**Common settings for all three Routines:**
- Model: **Sonnet**
- Repository: **`ajitbubu/policy-detection-agent`**
- Cloud Environment: **Default**
- Trigger: **Schedule** (cron + timezone)
- Timezone: **`America/New_York`** (matches the agent prompt's CADENCE section)
- Connectors: **Atlassian** + **Gmail** only — remove every other connector before saving
- Permissions tab: leave "Allow unrestricted branch pushes" **OFF**
- Working folder (referenced inside each prompt): `./regulation-watch/` (relative to repo root)
- Email recipient (locked): `asahu@datasafeguard.ai`
- Jira project / epic (locked): `IDP / IDP-11488`

A note on cadence: the user-defined schedules below override the default Mon–Fri daily cadence written into the agent prompt. The agent prompt's CADENCE section is informational; the Routines schedules are authoritative.

---

## Routine 1 — Privacy Reg Watch — Daily Tier 1

**Schedule (human):** Every Tuesday at 23:00 America/New_York
**Schedule (cron):** `0 23 * * 2`
**Next run after spec date:** Tue 2026-05-12, 23:00 ET

**Prompt:**

```
Use the privacy-regulation-watcher subagent. Run the daily Tier 1 scan per its operating rules and DELIVERY section. Working folder: ./regulation-watch/ (relative to the cloned repo root). Email recipient: asahu@datasafeguard.ai. Jira project/epic: IDP / IDP-11488. State files (alerts-emitted.json, regulation-watch.log, alerts/<date>/*.md, jira-config.json) are committed to the repo at ./regulation-watch/ — read for dedupe, write your updates back, and commit + push to a branch named `claude/regwatch-tier1-<YYYY-MM-DD>` (one branch per run; open a draft PR if one does not already exist). If zero qualifying changes detected, log silently and exit — no email, no Jira, no chat output, but still commit the appended log line.
```

---

## Routine 2 — Privacy Reg Watch — Weekly Tier 2 + Digest

**Schedule (human):** Every Monday at 23:30 America/New_York
**Schedule (cron):** `30 23 * * 1`
**Next run after spec date:** Mon 2026-05-11, 23:30 ET

**Prompt:**

```
Use the privacy-regulation-watcher subagent. Run the weekly Tier 2 scan and produce the LOW-severity weekly digest per its operating rules and DELIVERY section. Working folder: ./regulation-watch/ (relative to the cloned repo root). Email recipient: asahu@datasafeguard.ai. Jira: IDP / IDP-11488. Weekly digest goes as a Gmail draft (do not auto-send). State files are committed to the repo at ./regulation-watch/ — read for dedupe, write your updates back, and commit + push to a branch named `claude/regwatch-tier2-<YYYY-MM-DD>`; open a draft PR if one does not already exist. After the digest is drafted, clear ./regulation-watch/digest-pending.md.
```

---

## Routine 3 — Privacy Reg Watch — Monthly Tier 3 Horizon

**Schedule (human):** 1st of every month at 11:00 America/New_York
**Schedule (cron):** `0 11 1 * *`
**Next run after spec date:** Mon 2026-06-01, 11:00 ET

**Prompt:**

```
Use the privacy-regulation-watcher subagent. Run the monthly Tier 3 horizon scan per its operating rules. Working folder: ./regulation-watch/ (relative to the cloned repo root). Save the horizon report to ./regulation-watch/horizon-reports/<YYYY-MM>.md and email a summary as a Gmail draft to asahu@datasafeguard.ai. No new Jira tickets unless an item independently qualifies as HIGH or CRITICAL per the agent's severity rubric (in which case follow the standard DELIVERY path). Commit + push to a branch named `claude/regwatch-tier3-<YYYY-MM>`; open a draft PR if one does not already exist.
```

---

## Pre-flight to confirm before first scheduled run

- [ ] Allow-list official `.gov`, `.gov.uk`, `.europa.eu`, `iabeurope.eu` domains for WebFetch in the cloud environment — primary-source verification keeps failing with HTTP 403, and the agent currently ships the operational caveat on every alert.
- [ ] Confirm the cloud sandbox can clone `ajitbubu/policy-detection-agent` and access `./regulation-watch/`.
- [ ] Confirm Atlassian and Gmail MCP connectors are authorised on the account that owns the routines.
- [ ] First weekly run on 2026-05-11 will produce an empty digest if no LOW items have accumulated by then — that is expected.
- [ ] Routine commits land on `claude/regwatch-*` branches with draft PRs. A human reviews and merges to base before the *next* run sees the updated state — otherwise dedupe / log appending may regress on the next run. Consider setting auto-merge on these PRs once you trust the cadence.
