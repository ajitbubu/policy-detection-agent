**STATUS (2026-07-17 run): NOT YET SENT.** Digest compiled below, but the Gmail MCP connector exposed no draft/send tool this run (only `get_message` + label tools loaded) — the weekly digest email could not be drafted. This file is intentionally left uncleared. Next run (with working Gmail access) should send this content as-is and then clear the file, or a human should send it manually to asahu@datasafeguard.ai.

# LOW-Severity Digest — Pending Monday Weekly Email

This file accumulates LOW-severity items between weekly digest sends. The
Monday weekly Routine emails the consolidated digest and clears this file.
Each entry below was screened against the TRIGGER EVENTS and severity rubric
in the privacy-regulation-watcher operating prompt and rated LOW (awareness
only; effective >180 days out, not yet enacted, or clarifying guidance with
no new engineering delta).

---

## Week of 2026-07-17 — Tier 2 scan (APAC / MENA & Africa / LatAm / Global cross-border)

### 1. Japan — APPI amendment bill (not yet enacted)
- **Status:** Cabinet approved and submitted a bill to the Diet on 2026-04-07 to amend the Act on the Protection of Personal Information (APPI). Not yet passed.
- **Why it matters (if passed):** Introduces "personally referable information" (PRI) covering cookie IDs, device IDs, and browsing/purchase history that could become identifying when combined with recipient-side data. Third-party transfer of "contactable" PRI (incl. cookie IDs) would require prior consent — directly touches Consent Signals / Vendor Governance.
- **Timeline:** Even if enacted this Diet session, expected effective date is not before 2028.
- **Action:** No engineering action now. Watch for Diet passage; re-scan monthly (Tier 2 cadence) and escalate to a full alert on enactment.
- Refs: https://www.morihamada.com/en/insights/newsletters/138006 ; https://www.bakermckenzie.com/en/insight/publications/2026/05/japan-appi-reform-key-changes ; https://iapp.org/news/a/navigating-japan-s-proposed-appi-amendments-key-timelines-open-issues-and-action-points

### 2. Global cross-border — EU-US Data Privacy Framework under legal pressure
- **Status:** No binding change. PCLOB cannot conduct its statutory annual review of Executive Order 14086 compliance (board incapacitated); FISA Section 702 lapsed in April 2026 and was kept alive by a short-term extension through mid-June 2026, with status beyond that unclear from this run's sources. Legal commentary expects a possible CJEU "Schrems III" preliminary ruling by late 2026/early 2027.
- **Why it matters:** If the DPF adequacy decision is invalidated, EU-US transfers underpinning many CMP vendor integrations would need to fall back to SCCs/other mechanisms — a potentially CRITICAL event if/when it happens.
- **Action:** No engineering action now. Add to Tier 1 watch trigger: escalate immediately (ad-hoc, within 4 hours) if the CJEU issues a ruling or the European Commission announces suspension/review.
- Refs: https://www.activemind.legal/guides/dpf-supreme-court/ ; https://globaldatashield.com/blog/eu-us-data-privacy-framework-2026

### 3. Global cross-border — EU SCCs for Article 3(2) transfers still not adopted
- **Status:** The European Commission has been developing a new set of SCCs for transfers to non-EEA controllers/processors directly subject to GDPR Art. 3(2) (e.g., targeting EU residents). Originally targeted for adoption in Q2 2025; as of this scan, no formal implementing decision has been published in the Official Journal.
- **Action:** No engineering action now. Re-check monthly; this would become MEDIUM/HIGH once formally adopted (new contractual mechanism to support in Cross-border Transfer Mechanism subsystem).
- Refs: https://commission.europa.eu/publications/publications-standard-contractual-clauses-sccs_en

### 4. UK — ICO updated international transfer guidance (already published, awareness)
- **Status:** ICO published refreshed international-transfer guidance on 2026-01-15 (task-based guidance, new "three-step test" for restricted transfers, aligned to Data (Use and Access) Act 2025 concepts). ICO has signaled plans to update the IDTA and Addendum during 2026 to reflect DUAA changes, but those updated instruments are not yet published per sources reviewed this run.
- **Why it matters:** Once the IDTA/Addendum are actually revised, that would be a MEDIUM/HIGH trigger for the Cross-border Transfer Mechanism subsystem (UK leg).
- **Action:** No engineering action now — guidance restates existing UK GDPR Ch. V framework rather than creating new obligations. Watch for the IDTA/Addendum revision itself.
- Refs: https://www.kennedyslaw.com/en/thought-leadership/article/2026/the-ico-s-2026-updated-international-transfer-guidance-decoding-the-new-uk-regime/ ; https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/international-transfers/adequacy-regulations/how-does-the-uk-extension-to-the-eu-us-data-privacy-framework-work/

### 5. Australia — OAIC Children's Online Privacy Code (not yet registered)
- **Status:** Tranche-one reforms (Privacy and Other Legislation Amendment Act 2024) require OAIC to register a Children's Online Privacy Code by 2026-12-10. Code text not yet published as of this scan.
- **Why it matters (once registered):** Would impose stricter profiling/tracking rules for services "likely to be accessed by children" — touches Consent Banner age-gating and Cookie Classification ML.
- **Action:** No engineering action now (T-146 days, code not yet published). Watch OAIC for code text; escalate to MEDIUM/HIGH once published.
- Refs: https://www.ashurst.com/en/insights/australias-first-tranche-of-privacy-reforms-a-deep-dive-and-why-they-matter/ ; https://www.didomi.io/regulations/australia

### 6. Australia — Privacy Act reform "Tranche 2" (still proposed, no bill)
- **Status:** As of mid-2026, Tranche 2 (fair-and-reasonable test, small-business exemption removal, broadened "personal information" definition to capture online identifiers/IP addresses) remains a government commitment, not enacted law. No bill passed, no firm commencement date.
- **Action:** No engineering action. Continue monthly watch.
- Refs: https://rulesmate.com.au/insights/privacy-act-second-tranche-reforms-2026-outlook ; https://www.biztechlawyers.com/legal-articles/australias-privacy-reform-shaping-the-future-of-data-protection

### 7. Nigeria — NDPC GAID 2025 compliance deadline (housekeeping, deadline already passed)
- **Status:** NDPC's General Application and Implementation Directive (GAID) 2025 (cookie opt-in, homepage-visible notice, no pre-ticked boxes) has been operational since 2025-09-19. The 2025 Compliance Audit Return (CAR) filing deadline was extended to 2026-05-30, which has already passed as of this scan.
- **Action:** No new engineering action — this is a reminder that Nigeria's opt-in cookie regime is already fully in force and should already be reflected in ID-PRIVACY®'s Nigeria jurisdiction ruleset (verify with engineering if not already confirmed in a prior cycle).
- Refs: https://kukie.io/blog/cookie-consent-nigeria-ndpr-compliance ; https://ndpc.gov.ng/

### 8. South Africa — POPIA amended regulations (no new 2026 cookie-specific change found)
- **Status:** Information Regulator published amended POPIA regulations on 2025-04-17 (definitions, data-subject objection rights). No new cookie/consent-specific regulatory action identified in this scan window. Existing guidance: cookie consent valid for 12 months; Direct Marketing Guidance Note (Dec 2024) requires informed, voluntary, specific consent with burden of proof on the controller.
- **Action:** No engineering action. Awareness only.
- Refs: https://insightplus.bakermckenzie.com/bm/data-technology/south-africa-amendments-to-the-popia-regulations-key-changes-you-need-to-know

### 9. UAE — PDPL Executive Regulations status unclear (flagged for follow-up, not alerted)
- **Status:** Secondary sources conflict: several SEO/compliance-guide sites claim "Executive Regulations issued in 2026," while more established trackers (DataGuidance, Baker McKenzie) reference Cabinet Decision No. 33 of 2024 as the operative Executive Regulation, already in force since 2024. Could not confirm a genuine new 2026 UAE PDPL regulatory action this run.
- **Action:** No alert issued — insufficient corroboration to treat as a confirmed 2026 change. Flagged for a targeted re-check next Tier 2 cycle rather than included as a LOW digest "real" item; listed here for visibility only.
- Refs: https://www.dataguidance.com/jurisdictions/united-arab-emirates-federal ; https://itsecnow.com/regulators/pdpl-executive-regulations-2026 (lower-confidence source)

### 10. Mexico — LFPDPPP further revision rumored, not yet published
- **Status:** Mexico enacted a wholesale new LFPDPPP on 2025-03-20/21 (post-INAI-dissolution, oversight moved to the Ministry of Anti-Corruption and Good Governance). Rumors of a further new law in 2026; implementing regulations not yet published as of this scan.
- **Action:** No engineering action. Continue monthly watch for implementing regulations, which would be the actual trigger for engineering-relevant detail (cookie/tracking specifics).
- Refs: https://www.whitecase.com/insight-alert/mexico-enacts-new-data-protection-regime ; https://practiceguides.chambers.com/practice-guides/data-protection-privacy-2026/mexico/trends-and-developments

### 11. Argentina — Personal Data Protection Bill reform (still in Congress)
- **Status:** AAIP-drafted bill (successor to the 2023 draft sent to Congress 2023-06-29) remains under legislative discussion; AAIP separately launched a Program for Strengthening Personal Data Protection in the National Public Administration (Resolution 145/2025, Official Gazette 2025-08-04). No passage date confirmed for 2026.
- **Action:** No engineering action. Continue monthly watch.
- Refs: https://www.lexology.com/library/detail.aspx?g=f5ce9cc0-2598-453b-920e-11954ae9b32d ; https://www.jurist.org/commentary/2025/12/why-argentinas-pioneering-privacy-law-is-now-playing-defense-against-ai/

### 12. Peru / Colombia — no material near-term trigger identified this run
- **Status:** Peru's secondary regulations already impose tight breach-notification and cross-border restrictions covering biometric/neurodata (no new 2026 change identified this run). Colombia has draft reforms addressing neurodata/AI, still in early stages, no confirmed date.
- **Action:** No engineering action. Continue monthly watch.
- Refs: https://solucionesetech.com/en/blog/data-protection-compliance-latin-america-2026/

### 13. MENA — Bahrain, Qatar, Saudi Arabia PDPL: no new 2026 binding change identified
- **Status:** Saudi PDPL Implementing Regulations remain in force (since 2024); SDAIA enforcement committees issued 48 violation decisions across 2025-2026 (ongoing enforcement activity, not a new rule). Bahrain (Law No. 30 of 2018) and Qatar (2016 law) show no new 2026 regulatory action in this scan.
- **Action:** No engineering action. Awareness only.
- Refs: https://www.sgc.consulting/sdaia-saudi-personal-data-protection-law-pdpl-compliance-guide/

---

*Digest compiled 2026-07-17 by the privacy-regulation-watcher subagent (Tier 2 weekly scan). Orchestrator: consolidate and send as the Monday weekly digest email, then clear this file per routines.md.*
