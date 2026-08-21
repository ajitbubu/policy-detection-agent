# Weekly LOW-Severity Digest — Pending

Items below are LOW severity per the ANALYSIS FRAMEWORK rubric (awareness only — effective >180 days away, or the item already passed its effective date without CMP-breaking consequence and clarifies/extends existing practice). They are consolidated here for the Monday weekly digest email; no standalone Jira/email is generated per item.

---

## 2026-08-21 — Tier 2 weekly scan additions

### Japan — APPI Amendment (personally-referable information / cookie IDs)
- **Instrument:** Act on the Protection of Personal Information (APPI) amendment bill
- **What changed:** Passed both houses of the Diet 2026-07-10, promulgated 2026-07-17. Introduces a new "personally referable information" category covering cookie IDs, browsing/purchase history, and location data tied to device identifiers; requires consent before a third party receives such data if that party is expected to be able to re-identify the individual. Also introduces Japan's first administrative monetary penalties under APPI (previously criminal-penalty-only).
- **Effective date:** Not yet fixed — Cabinet order to set commencement, no later than 2026-07 (i.e., ~July 2028). T-minus >180 days from scan date (2026-08-21).
- **Primary source:** Japan Personal Information Protection Commission (ppc.go.jp) — not directly fetched (egress-blocked pattern in this environment); reported via Baker McKenzie, Mori Hamada, Fisher Phillips.
- **Secondary refs:** https://www.bakermckenzie.com/en/insight/publications/2026/05/japan-appi-reform-key-changes , https://www.morihamada.com/en/insights/newsletters/138006 , https://www.fisherphillips.com/en/insights/insights/japanese-cabinet-approves-appi-amendments
- **Confidence:** MEDIUM — promulgation date corroborated by 3 sources; exact commencement date still pending Cabinet order, so downstream operational detail (cookie-ID consent mechanics) is not yet actionable.

### China — Certification Measures for Cross-Border Transfer of Personal Information
- **Instrument:** Measures for Certification of Cross-Border Personal Information Transfer, jointly issued by the Cyberspace Administration of China (CAC) and State Administration for Market Regulation (SAMR)
- **What changed:** Establishes a third voluntary compliance pathway (Certification) alongside the existing Security Assessment and Standard Contractual Clauses routes for exporting personal information from China. Relevant to ID-PRIVACY's Cross-border Transfer Mechanism subsystem for any tenant transferring data collected in China.
- **Effective date:** 2026-01-01 (already in force ~8 months as of this scan; publication was 2025-10-17, both outside this platform's monitoring window prior to this Tier-2 scan being the first Tier-2 pass since activation).
- **Primary source:** CAC (cac.gov.cn) / SAMR — not directly fetched in this environment.
- **Secondary refs:** https://cms.law/en/chn/legal-updates/china-issues-measures-for-the-certification-of-the-cross-border-transfer-of-personal-information
- **Confidence:** MEDIUM — this is an additive/voluntary pathway, not a new mandate, so downgraded to LOW despite already being in force; recommend engineering confirm no China-transferring tenant is depending on a pathway this measure implicitly narrows.

### New Zealand — Privacy Amendment Act 2025, Part 1 (IPP 3A indirect-collection notice)
- **Instrument:** Privacy Amendment Act 2025, Royal Assent 2025-09-24
- **What changed:** New Information Privacy Principle 3A requires agencies that collect personal information indirectly (not directly from the individual) to provide notice of that collection. Not cookie-specific, but touches the notice layer adjacent to consent/CMP disclosures.
- **Effective date:** Part 1 (IPP 3A) — 2026-05-01 (already passed; Part 2 was already in force from 2025-09-24).
- **Primary source:** New Zealand Legislation — https://www.legislation.govt.nz/act/public/2025/53/en/latest/ (not directly fetched in this environment; link-verified-by-reference).
- **Secondary refs:** https://securiti.ai/new-zealand-privacy-amendment-bill/
- **Confidence:** MEDIUM-HIGH — legislation.govt.nz listing corroborates dates; downgraded to LOW because most CMP-adjacent notice text likely already satisfies this via existing privacy-notice disclosures — treat as a documentation-language check, not a build item.

---
