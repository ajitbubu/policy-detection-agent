# ID-PRIVACY® Gap Analysis vs. Top 10 In-Window Regulation Changes

**Prepared by:** Privacy Regulation Intelligence Agent (initial activation)
**For:** Ajit, Director of Engineering, DataSafeguard
**Date:** 2026-05-09
**Window:** 2026-05-09 → 2027-05-09

---

## Legend — IMPORTANT

> **All coverage statuses below are ASSUMED.** I have **no access to the ID-PRIVACY codebase, roadmap, configuration store, or test suite.** Every "Likely covered / Partial / Likely gap" entry must be **verified with engineering** before being treated as a status. Use the "Suggested verification step" column as the prompt for an internal walkthrough. Effort estimates are calibrated to a Universal CMP of typical scope (S = ≤1 sprint, M = 2–4 sprints, L = ≥1 quarter, multi-team).

---

## Gap analysis table

| # | Item | ID-PRIVACY® subsystem(s) likely affected | ASSUMED coverage status | Suggested verification step for engineering | Rough effort to close gap if needed |
|---|---|---|---|---|---|
| 1 | IAB TCF v2.3 mandatory transition (2026-02-28) | Consent Signals (TCF string generation, GVL sync), Consent Banner (vendor-count rendering on layer 1), Audit/Logging (string ↔ UI parity) | **Partial** — likely already on TCF 2.2; the Disclosed Vendors bitfield + weekly GVL sync + UI/string parity validators are the new burden | Run IAB Europe's official validator against a representative live tenant in EU; confirm GVL sync cadence in code; diff vendor visibility flags vs. bitfield | **M** |
| 2 | EU Digital Omnibus — proposed GDPR Art. 88a / 88b (mid-late 2026 adoption; +6/+24 mo applicability) | Consent Banner (single-click refusal), Consent Storage (6-month re-prompt suppression state), Consent Signals (machine-readable browser-level signal handling), Geo/Jurisdiction Routing | **Likely gap** — 6-month no-reprompt window is a stateful constraint most CMPs do not enforce strictly; machine-readable signal acceptance for non-GPC signals is not yet specified | Inventory current re-prompt logic; map state model to a "last-refusal timestamp" per origin/user; design abstraction for inbound signal types beyond GPC/TCF | **L** |
| 3 | UK DUAA 2025 — PECR amendments + new ICO guidance (2026-02-05 live; 2026-06-19 complaints workflow) | Cookie Classification ML (new exempt categories), Tenant Config (UK-specific exemption toggles), DSR Engine (complaints workflow), Audit/Logging | **Partial** — classification taxonomy may not yet encode the three new UK-only consent exemptions; complaints workflow likely needs new module | Confirm classifier emits per-cookie "consent_required vs. exempt" with jurisdiction context; check whether tenant admin can mark cookies as UK-exempt-statistical; spec the complaints inbox | **M** |
| 4 | India DPDP Phase 2 — Consent Manager (2026-11-14) | Tenant Config, Consent Capture & Storage (interoperability with registered Consent Managers), Documentation/DPIA | **Likely gap** — Consent Manager interoperability is a novel India-specific architecture; ID-PRIVACY needs either to integrate as a Data Fiduciary client of registered CMs OR pursue registration as a Consent Manager itself (product/strategy decision) | Product + Legal: decide CM-integrator vs. CM-registrant posture; if integrator, define CM API contract & test against a registered CM sandbox once DPBI publishes one | **L** (if registering as CM) / **M** (integrator-only) |
| 5 | California CCPA Regulations Package (2026-01-01 live; ADMT 2027-01-01) | Consent Banner (close-or-navigate-away ≠ consent), DSR Engine (ADMT access/opt-out), Audit/Logging (risk assessments), Documentation | **Partial** — banner-dismiss-as-rejection is likely already enforced in newer CMPs but may need explicit codification & test; ADMT rights are entirely new and need a dedicated workflow by Jan 2027 | Audit current banner X-button / outside-click behavior across templates; design an ADMT request workflow with new request types and decision-disclosure fields | **M** |
| 6 | California AB 566 — browser opt-out preference signal (2027-01-01) | Consent Signals (broader signal sources beyond GPC), Consent Banner (do not display contradictory banner when signal received), Geo/Jurisdiction Routing | **Partial** — GPC handling likely exists; OOPS may use new signal envelopes (mobile in-app browsers, OS-level signals) the platform doesn't currently parse | Catalogue all inbound opt-out signal mechanisms today; define a generic "opt-out preference signal" abstraction; add test fixtures for mobile/in-app contexts | **M** |
| 7 | Multi-state US — UOOM mandatory (OR 2026-01-01 live; CT 2026-07-01 amendment; NJ 2026-07-15 cure sunset; NJ regs adoption 2026-06-02) | Geo/Jurisdiction Routing, Consent Signals (per-state semantics), Tenant Config, Audit/Logging | **Partial** — geo-routing engine likely exists; the per-state nuance (sale only vs. sale+share+targeted ads; signal-vs-prior-choice precedence; re-prompt rules) requires a state-specific rule matrix | Produce the 11-state UOOM behaviour matrix; add automated tests per state; verify signal-handling priority order matches each state's rule | **M** |
| 8 | Maryland MODPA (effective 2026-04-01) | Cookie Classification ML (sensitive-data tags), Vendor/SDK Governance (suppress sale even on consent), Geo/Jurisdiction Routing, Tenant Config | **Likely gap** — most CMPs treat consent as the override; MODPA inverts that for sensitive data sale (no override). Engine must enforce a rule that user consent does NOT unblock a category | Add a "consent-cannot-override" enforcement flag per data category per jurisdiction; verify default for MD residents on sensitive categories blocks sale regardless of banner state | **M** |
| 9 | EDPB Guidelines 2/2023 — final scope of Art. 5(3) ePrivacy (final 2024-10-07; Cookie Banner Taskforce update 2026-04-30) | Cookie Classification ML (pixels, fingerprinting, IP-only tracking, SDK identifiers), Vendor/SDK Governance (non-cookie trackers), Audit/Logging | **Partial** — classifier likely covers pixels and standard fingerprinting; IP-only tracking, link decoration, IoT/device identifiers may be under-covered | Run classifier against EDPB-provided use cases; verify each pattern (URL tracking, IP-only, server-side pixel, IoT mediated reporting) is captured and gated behind consent | **M** |
| 10 | France CNIL — sustained dark-pattern / reject-all parity enforcement (continuous; €150M+ fines 2025–2026) | Consent Banner (parity styling, click-count parity, copy review), Tenant Config (French-locale-specific toggles), Audit/Logging | **Likely covered** — modern CMPs implement first-layer reject-all parity; risk is in template drift across legacy customers | Run an automated audit on all FR-locale tenant banners: assert reject button equal pixel area, equal click count, no preferential color contrast, no "deny" hidden behind "manage" | **S** (audit + remediation tooling) |

---

## Cross-cutting recommendations (not item-specific)

These are not in the table above because they cut across multiple rows; they are observations from the gap pattern.

- **Jurisdiction rule matrix is now the platform's center of gravity.** The fragmentation across US states, EU member states (post-ePrivacy-Regulation withdrawal), and India's phased rollout means the geo-routing + per-jurisdiction config layer is the highest-leverage code in the platform. A formal, versioned, and externally-reviewable jurisdiction rule matrix (with effective dates per rule) would simplify multiple gaps above. Rough effort: **L**.
- **Signal abstraction layer.** Today: GPC. Soon: AB 566 OOPS, GDPR Art. 88b machine-readable signals, possible state extensions. A generic "preference signal" interface with per-jurisdiction semantics decouples a lot of forthcoming work. Rough effort: **M**.
- **Audit-trail / proof-of-consent retention.** PECR fines now uplifted to UK GDPR ceilings (£17.5m / 4%); CNIL enforcement is in nine figures; CCPA cybersecurity audits arrive 2028. Logging schema and retention need to be defensible at the level of a regulator's evidentiary request. Rough effort: **M** for schema review; **L** for full attestable audit pipeline.

---

## Reminder

Please treat this document as **input to a verification meeting with engineering and legal**, not as an authoritative status report. The author of this document has zero visibility into the ID-PRIVACY codebase.
