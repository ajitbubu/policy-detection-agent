# ID-PRIVACY® Gap Analysis vs. Top 10 In-Window Regulation Changes
**Run date:** 2026-05-09
**For:** Director of Engineering, DataSafeguard

---

## Legend — IMPORTANT

All "coverage status" values in the table below are **ASSUMED** by the Privacy Regulation Intelligence Agent based on the public posture of a mature Universal CMP. **The agent has no codebase access in this run.** Every row must be **verified by engineering** before it is treated as a true gap or true coverage.

- **Likely covered** — capability is core to a mature CMP; verify version/feature flag is on for affected tenants.
- **Partial** — capability exists in a related form but the specific delta is probably not implemented; verify and scope.
- **Likely gap** — no obvious off-the-shelf coverage; expect new design or significant work.

Effort: **S** ≈ ≤5 person-days, **M** ≈ 1–4 person-weeks, **L** ≈ 1+ person-month or cross-team.

---

## Gap analysis table

| # | Item | ID-PRIVACY® subsystem(s) likely affected | ASSUMED coverage status | Suggested verification step for engineering | Rough effort |
|---|------|------------------------------------------|-------------------------|---------------------------------------------|--------------|
| 1 | IAB TCF v2.3 — `disclosedVendors` segment mandatory from 2026-02-28 | Consent Signals (TCF string emit/parse); Vendor/SDK Governance; Audit/Logging | **Partial** — base TCF support is core; whether the v2.3 `disclosedVendors` segment is generated and signed is the actual question | Confirm CMP build version is registered with IAB Europe as v2.3-compliant; sample-decode 50 production TC strings and verify `disclosedVendors` is present and matches displayed vendor list | M |
| 2 | California CCPA regs — ADMT opt-out, Risk Assessments, Cybersecurity Audits (effective 2026-01-01; ADMT consumer rights 2027-01-01) | Consent Banner (ADMT preference surface); DSR Engine; Audit/Logging; Tenant Config/Admin UI; Documentation/DPIA/RoPA | **Partial** — DNS/Limit-Use of SPI exists; a separate ADMT preference and ADMT-specific access right are likely not yet a first-class object | Walk the ADMT decision-tree against current CA ruleset: is there a configurable ADMT purpose category? Does the DSR engine accept an "access ADMT logic" request type? Are risk-assessment artefacts auto-exportable? | L |
| 3 | UK Data (Use and Access) Act 2025 — three new PECR cookie exemptions (live 2026-02-05) | Cookie Classification ML; Geo/Jurisdiction Routing; Tenant Config; Documentation | **Likely covered (routing)** but **Partial (classification)** — UK ruleset routing exists; whether the classifier supports the three new exempt subcategories (first-party analytics, appearance/functionality, emergency-assistance) as distinct labels is uncertain | Confirm UK ruleset variant exists and diverges from EU; confirm classifier ontology has the three new labels; confirm UK tenants can opt to skip consent gating on those labels | M |
| 4 | India DPDP Rules — Phase II (Consent Manager regime) effective 2026-11-13 | Consent Capture & Storage (Consent-Manager-format records); Consent Signals (revocation hooks); Cross-border Transfer; Tenant Config; DSR Engine; Documentation | **Likely gap** — registered Consent Manager format / certification / revocation API are India-specific; integration probably not built | Decide product strategy (be a CM, partner with CMs, or both); review draft DPDP Rules schema against current consent-record schema; estimate registration / certification path with MeitY | L |
| 5 | California Delete Act / DROP — data brokers must poll DROP every 45 days from 2026-08-01 | DSR Engine; Audit/Logging; Tenant Config (data-broker flag); Vendor/SDK Governance | **Likely gap** — DROP polling client + match logic + 90-day determination workflow are net-new | Inventory which tenants are CA-registered data brokers; confirm DROP API is available in CPPA's test environment; design poller, match-rule, response-and-evidence pipeline | L |
| 6 | New US state laws live 2026-01-01 (IN, KY, RI, MN) | Geo/Jurisdiction Routing; Consent Banner copy; DSR Engine; Documentation; Tenant Config | **Likely covered** — these follow the VCDPA/CPA pattern that ID-PRIVACY ruleset templates already serve | Confirm jurisdiction-routing covers IN/KY/RI/MN GeoIP; confirm DSR response-time defaults match each statute (45/60 days + cure rules); confirm RI's lower threshold is reflected in tenant-eligibility helper | S |
| 7 | Maryland MODPA — operative for processing on/after 2026-04-01; sensitive-data sale ban regardless of consent | Consent Banner (no "consent overrides" path for sensitive-sale in MD); Vendor/SDK Governance (block list for sensitive purposes); Cookie Classification ML (precise-geo, health, etc.); Tenant Config; Documentation | **Partial** — vendor/SDK gating exists; the inversion "consent is not enough — necessity test required" is probably not a first-class rule | Confirm MD ruleset can flag sensitive-data purposes as "block-on-sale" even when consent is granted; confirm precise-geo (≤1,750 ft) is a routable trigger; confirm under-18 detection path | M |
| 8 | Connecticut + Oregon UOOM (GPC) recognition mandates from 2026-01-01; CT neural-data sensitive 2026-07-01 | Consent Signals (GPC ingest, state-specific behaviour); Geo/Jurisdiction Routing; Cookie Classification ML (neural data label) | **Likely covered (GPC)** — GPC handling is core. **Partial (CT neural)** — the "neural data" sensitive label probably lacks a classifier rule | Run conformance suite for GPC across CT and OR rulesets; add a "neural data" sensitive label and confirm vendor templates can be mapped to it where applicable | S–M |
| 9 | Colorado CPA biometric (HB24-1130) + neural data (HB24-1058) | Cookie Classification ML; Vendor/SDK Governance; Consent Banner (opt-in for biometric/neural); Audit/Logging (retention schedule); Documentation | **Partial** — opt-in pattern is supported; the biometric retention schedule and sale-ban enforcement are probably tenant-policy not platform-enforced | Confirm biometric / neural data are first-class purpose categories; confirm a per-tenant retention schedule attaches to biometric records; confirm sale of biometric / neural data is hard-blocked, not soft-warned | M |
| 10 | EDPB Pseudonymisation Guidelines 01/2025 (final pending) + EU Digital Omnibus proposal (draft Article 88a folding cookies into GDPR) | Consent Capture & Storage (definition of "pseudonymised" record); Audit/Logging; Documentation; (potentially) Consent Banner if Omnibus advances | **Likely covered** for current pseudonymisation claims; **N/A** for Omnibus (pre-binding) | Re-read internal "what we call pseudonymised" claims against EDPB draft criteria; tag the Digital Omnibus as a tracked dossier with weekly scan; do not act yet | S (now), L (if Omnibus advances) |

---

## Summary read-out

- **Highest-risk gap right now:** Item 1 (TCF v2.3) if any TCF-claiming tenants are still on v2.2 builds. Verify in the next 48 hours.
- **Largest scope of new work likely required:** Item 4 (India Consent Manager) and Item 5 (DROP polling) — both are net-new integrations, not configuration changes.
- **Cheapest wins:** Items 6 and 8 — most can be handled by ruleset templates and config, assuming the platform's jurisdiction-routing layer is healthy.
- **Most volatile item to track:** Item 10 — both the EDPB final guidelines and the Digital Omnibus could change category at any quarterly scan.

*All gap statuses above are ASSUMED; please have engineering confirm before resourcing.*
