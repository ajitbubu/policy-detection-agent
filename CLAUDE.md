# CLAUDE.md — policy-detection-agent

Repository: `ajitbubu/policy-detection-agent`
Owner: Ajit Sahu, Director of Engineering, DataSafeguard
Target platform: ID-PRIVACY® Universal Consent Management

## Purpose

Continuously monitor global data-privacy and cookie/consent regulation changes and translate them into ID-PRIVACY engineering action (alerts → Jira stories under epic `IDP-11488` → email drafts to `asahu@datasafeguard.ai`).

## Architecture

Two-role split:

- **Subagent** — `privacy-regulation-watcher` (`.claude/agents/privacy-regulation-watcher.md`). Has only WebSearch, WebFetch, Read, Write, Bash. Scans Tier 1/2/3 sources, applies trigger rules, writes alert files to `regulation-watch/alerts/<YYYY-MM-DD>/<alertId>.md` in the agent's OUTPUT FORMAT, and returns a JSON summary.
- **Orchestrator** — main Claude Code session. Has the Atlassian and Gmail MCP tools the subagent does not. Reads the subagent's alert files, creates Jira stories + Gmail drafts per the DELIVERY rubric, updates `regulation-watch/alerts-emitted.json`, appends `regulation-watch/regulation-watch.log`.

The DELIVERY split is documented in the agent file's `## DELIVERY` section. Do not give the subagent Atlassian or Gmail tools — keep the role boundary clean.

## Locked configuration

Source of truth: `regulation-watch/jira-config.json`.

| Setting | Value |
|---|---|
| Jira project | `IDP` |
| Jira epic (UCM) | `IDP-11488` |
| Email recipient | `asahu@datasafeguard.ai` |
| Confirmed by | Ajit Sahu, 2026-05-09 |

When creating Jira stories under IDP-11488, both `Customer` (multi-select, use `DSG Internal` id `10316`) and `Product` (multi-select, use `UCM` id `10039`) are required. The IDP project rejects creates without both.

## Delivery rubric

Per `.claude/agents/privacy-regulation-watcher.md` § DELIVERY:

- **CRITICAL / HIGH** → Gmail draft + Jira story (priority Highest / High) under IDP-11488, labels `privacy-regulation-watch` + jurisdiction code + `UCM`
- **MEDIUM** → Gmail draft only
- **LOW** → append to `regulation-watch/digest-pending.md`; emitted as Monday digest by the weekly Routine

## Repo layout

```
.claude/agents/privacy-regulation-watcher.md   subagent definition (operating prompt + DELIVERY)
regulation-watch/
  jira-config.json                              locked config
  alerts-emitted.json                           dedupe state, 30-day window
  regulation-watch.log                          append-only run log
  digest-pending.md                             LOW items awaiting Monday digest
  alerts/<YYYY-MM-DD>/<alertId>.md              one file per emitted alert
  scan-<YYYY-MM-DD>.json                        subagent scan summary per run
  horizon-reports/<YYYY-MM>.md                  Routine 3 monthly horizon reports
  baseline-state-of-the-world.md                top-10 in-window items (refreshed on activation)
  gap-analysis.md                               ASSUMED ID-PRIVACY coverage map
  monitoring-sources.md                         Tier 1/2/3 source list
  routines.md                                   Claude Code on the web Routines spec
```

## Routines (Claude Code on the web)

Three scheduled tasks defined in `regulation-watch/routines.md`:

| # | Routine | Cron (America/New_York) | What it does |
|---|---|---|---|
| 1 | Privacy Reg Watch — Daily Tier 1 | `0 23 * * 2` | Tier 1 scan; emit alerts per DELIVERY |
| 2 | Privacy Reg Watch — Weekly Tier 2 + Digest | `30 23 * * 1` | Tier 2 scan + LOW digest as Gmail draft |
| 3 | Privacy Reg Watch — Monthly Tier 3 Horizon | `0 11 1 * *` | Tier 3 horizon report saved + emailed |

All three: model **Sonnet**, repo `ajitbubu/policy-detection-agent`, cloud env Default, connectors **Atlassian + Gmail only**, permissions "Allow unrestricted branch pushes" **OFF**.

## Branch & merge conventions

- Routine commits land on `claude/regwatch-<tier>-<date>` branches with draft PRs to `main`.
- Merge each Routine PR before the next run of the same Routine fires, otherwise dedupe state regresses (the next clone won't see the appended `alerts-emitted.json`).
- Per the harness's restriction, pushes are only accepted on `claude/*` branches. To promote a branch to `main`, use the GitHub MCP `create_branch` tool (not `git push origin <branch>:main`).

## Operational caveats

- **WebFetch returns HTTP 403** on official `.gov` / `.gov.uk` / `.europa.eu` / `iabeurope.eu` domains in both local and (likely) cloud runtimes. Until allow-listed, every alert ships with a "link-verified-by-reference" caveat. Allow-list before relying on primary-source verification.
- The agent's CADENCE section in the operating prompt says Mon–Fri 08:00 ET. The Routines schedules override that with the cron above. Routine config is authoritative.
- The subagent's tools list (`WebSearch, WebFetch, Read, Write, Bash`) intentionally excludes Atlassian and Gmail. Do not loosen this — the orchestrator owns delivery and state.

## Manually triggering a scan

From a Claude Code session in this repo:

```
Use the privacy-regulation-watcher subagent. Run the daily Tier 1 scan
per its operating rules and DELIVERY section. Working folder:
./regulation-watch/.
```

The subagent will write to `regulation-watch/alerts/<today>/...` and return a JSON summary; you (the orchestrator) then handle Jira + Gmail.

## Self-check before delivering any alert

From the operating prompt's SELF-CHECK section — the orchestrator must verify before creating Jira / Gmail:

- Primary source URL confirms the claim (or alert is labeled `SECONDARY — pending primary confirmation`)
- Effective vs. publication vs. enforcement dates correctly distinguished
- At least one ID-PRIVACY subsystem identified
- At least one concrete engineering action specified
- Severity matches the rubric, not vibes
- No duplicate in `regulation-watch/alerts-emitted.json` within 30 days
- Confidence honestly stated

## Session history

- 2026-05-09 — Initial activation; baseline state-of-the-world produced (top 10 in-window items through 2027-05-09); first daily Tier 1 scan emitted 1 HIGH alert (RW-2026-05-09-01, FTC v. Kochava sensitive-location order) → Jira `IDP-11489`, Gmail draft `r-8257231129572050191`.
- 2026-07-14 — First weekly Tier 2 scan: 1 HIGH alert (RW-2026-07-14-01, SCOTUS *Trump v. Slaughter* threatening EU-US DPF adequacy) → Jira `IDP-12663`, Gmail draft `r118814986414348482`; 1 MEDIUM alert (RW-2026-07-14-02, Chile Law 21.719) → Gmail draft `r7509166546461918679`, no Jira; 7 LOW items → consolidated digest Gmail draft `r-5718038244074039136`, `digest-pending.md` cleared.
