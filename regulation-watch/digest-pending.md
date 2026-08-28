# Digest Pending — LOW-severity items awaiting Monday weekly digest email

Items below are awareness-only (LOW severity per rubric: effective >180 days, pre-binding/draft status, or guidance clarifying already-implemented behavior). No alert file / Jira story created for these. Orchestrator: consolidate and email as the weekly digest, then clear this file.

> **2026-08-28 orchestrator note:** this run could NOT draft the weekly digest email — the Gmail MCP connector available to this session exposes no draft-creation tool (only `update_draft`, which requires an existing draft ID; `send_message`/`reply` would send immediately, which the DELIVERY rubric forbids for a digest that must ship as a draft). File intentionally left uncleared so these 8 items aren't lost. Once Gmail draft creation is available (or an existing draft ID is supplied), consolidate all items below into one digest email to asahu@datasafeguard.ai and then clear this file.

---

## Tier 2 scan — 2026-08-28

- **Jurisdiction:** EU/EEA (cross-border, global)
  **Instrument:** EDPB letter to European Commissioner McGrath requesting formal review of the EU-US Data Privacy Framework adequacy decision, following the US Supreme Court's ruling in *Trump v. Slaughter* (FTC commissioner-independence case)
  **Summary:** EDPB Chair Anu Talus sent a letter (Commission ref. Ares(2026)7540711) on 2026-07-31 asking the Commission to assess whether the Supreme Court ruling undermines FTC independence, a factual predicate for the DPF adequacy decision. This is a request for review, not a suspension or invalidation — DPF remains in force. Watch for the Commission's response; if it triggers even a partial re-review, cross-border transfer mechanism (DPF-certified vendor reliance) becomes materially at risk for US-EU tenant data flows and this should be promoted to at least MEDIUM/HIGH.
  **Primary source:** EDPB (edpb.europa.eu) — SECONDARY, pending primary confirmation (WebFetch blocked on edpb.europa.eu)
  **Secondary refs:** https://www.hunton.com/privacy-and-cybersecurity-law-blog/edpb-calls-for-review-of-eu-u-s-data-privacy-framework-after-u-s-supreme-court-decision-on-ftc-independence , https://iapp.org/news/a/edpb-requests-review-of-eu-us-data-privacy-framework-following-trump-v-slaughter
  **Published:** 2026-07-31

- **Jurisdiction:** Mexico
  **Instrument:** SABG (Secretaría Anticorrupción y Buen Gobierno) — first published sanction under Mexico's new data protection regime (LFPDPPP 2025), against the Mexican Football Federation over a biometric stadium-access registration system
  **Summary:** First enforcement action by Mexico's new privacy authority (SABG, which replaced the dissolved INAI in March 2025). Signals SABG's enforcement posture is now active. Primarily a biometric/physical-access consent case, not web cookies, but relevant as the first data point on how the new regime enforces consent generally.
  **Primary source:** SABG (gob.mx) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://practiceguides.chambers.com/practice-guides/data-protection-privacy-2026/mexico/trends-and-developments
  **Published:** 2026-07-12

- **Jurisdiction:** Japan
  **Instrument:** Act on the Protection of Personal Information (APPI) — 2026 amendment bill, promulgated
  **Summary:** Amendment bill passed the House of Representatives (2026-05-26) and House of Councillors (2026-07-10), promulgated 2026-07-17. Introduces expanded PPC enforcement/fining powers, a new "Specific Biometric Personal Information" category with heightened transparency/deletion rights, and parental-consent requirements for children under 16. Full effect expected within 2 years of promulgation (by ~2028); exact effective date to be set by Cabinet order. Effective date is >180 days out — LOW per rubric — but flag for re-scan once the Cabinet order sets the specific effective date, given the biometric-category and children's-consent implications for Vendor/SDK Governance and Consent Banner age-gating.
  **Primary source:** Personal Information Protection Commission of Japan (ppc.go.jp) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://www.morihamada.com/en/insights/newsletters/138006 , https://www.bakermckenzie.com/en/insight/publications/2026/05/japan-appi-reform-key-changes
  **Published:** 2026-07-17 (promulgation)

- **Jurisdiction:** South Korea
  **Instrument:** PIPC draft amendment to the PIPA Enforcement Decree (breach-prevention focus)
  **Summary:** PIPC announced a draft amendment to the PIPA Enforcement Decree on 2026-06-02, aimed at strengthening breach-prevention obligations and individual rights. Still in draft/consultation stage — not yet final. Related to, but distinct from, the statutory PIPA amendment (10% revenue fine ceiling) already escalated as RW-2026-08-28-01 (HIGH/CRITICAL, see alert file). Re-scan for finalization.
  **Primary source:** PIPC (pipc.go.kr) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://www.dataguidance.com/news/south-korea-pipc-announces-draft-amendment-pipa
  **Published:** 2026-06-02

- **Jurisdiction:** Thailand
  **Instrument:** PDPC draft PDPA amendments + guideline consultation (legal-basis hierarchy, sensitive-data categories, AI processing; separately, a 6-priority-area guideline consultation opened March 2026)
  **Summary:** Public consultation stage only; no amendment enacted as of this scan. Watch for enactment.
  **Primary source:** PDPC Thailand (pdpc.or.th) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://pacmap.dev/regulation/th-pdpa-enforcement-2026
  **Published:** consultation ongoing since late 2025 / March 2026

- **Jurisdiction:** Australia
  **Instrument:** Privacy Act reform — Tranche 2 (consent-definition tightening) + OAIC Children's Online Privacy Code
  **Summary:** Tranche 2 (which would tighten the statutory definition of consent toward "voluntary, informed, current, specific, unambiguous") is agreed in principle but not yet legislated. OAIC's Children's Online Privacy Code was in industry/stakeholder consultation as of mid-2026 with a draft targeted for early 2026 (status of draft publication not independently confirmed this scan). Both pre-binding — watch for legislation/draft-code publication.
  **Primary source:** OAIC (oaic.gov.au) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://www.biztechlawyers.com/legal-articles/australias-privacy-reform-shaping-the-future-of-data-protection , https://www.pinsentmasons.com/out-law/analysis/privacy-act-reforms-australia
  **Published:** ongoing (Tranche 1 already live per prior baseline; Tranche 2 status as of 2026-08-28)

- **Jurisdiction:** Argentina
  **Instrument:** Comprehensive PDPA reform bills reintroduced to Congress (Bill No. 3397-D-2026, introduced 2026-07-16; related Bill 1751-D-2026, introduced 2026-04-22)
  **Summary:** Full repeal-and-replace proposals for Law 25.326, including a legitimate-interest proportionality test and a minor's independent-consent age set at 16. Both bills remain in committee; no reform enacted as of 2026-07-23. Pre-binding — watch for committee action.
  **Primary source:** Argentine Chamber of Deputies (Honorable Cámara de Diputados) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://allende.com/en/privacy-and-cybersecurity/comprehensive-reform-of-argentinas-personal-data-protection-framework-reintroduced-in-congress-08-12-2026/
  **Published:** 2026-07-16 (latest bill introduction)

- **Jurisdiction:** Colombia
  **Instrument:** Law 2489 of 2025 (safe digital environments for children/adolescents) — draft implementing presidential decree
  **Summary:** MinTIC released a draft implementing decree in December 2025 (comment period) adding a new title to Decree 1078 of 2015, operationalizing shared responsibility for age verification/authentication, parental controls, and age-based classification. Not yet a direct technical mandate for age verification; decree still in draft. Relevant to Consent Banner age-gating and DSR/child-data handling if/when finalized — watch for decree finalization.
  **Primary source:** MinTIC Colombia (mintic.gov.co) — SECONDARY, pending primary confirmation
  **Secondary refs:** https://www.ibanet.org/Colombia-new-frontier-in-online-safety-regulation , https://colombiaone.com/2026/07/23/colombia-child-online-safety-regulation-france-ban/
  **Published:** 2025-07-17 (law); December 2025 (draft decree)

