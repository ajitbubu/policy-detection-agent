# Regulation Watch -- Pending Weekly Digest Items

Items below are LOW severity or watch-list items queued for the Monday weekly digest email.

---

## Item 1 -- Connecticut CTDPA SB 1295: LLM Training Disclosure Requirement
**Added:** 2026-05-14 | **Scan:** tier1-daily | **Severity:** LOW (borderline MEDIUM at T-48 days)
**Jurisdiction:** Connecticut, United States
**Instrument:** Amendment to Connecticut Data Privacy Act (SB 1295, enacted June 24, 2025)
**Effective:** July 1, 2026 (T-48 days from 2026-05-14)
**Primary source:** https://portal.ct.gov/ag/sections/privacy/the-connecticut-data-privacy-act (SECONDARY -- pending primary confirmation of enacted text)
**What changed:** Effective July 1, 2026, controllers subject to the CTDPA must include a "clear and conspicuous" statement in their consumer-facing privacy notice disclosing whether they collect, use, or sell personal data for LLM training -- including by vendors acting on their behalf. Connecticut will be the first US state to mandate this disclosure. The requirement does not directly change the cookie consent banner but does require privacy-notice updates.
**ID-PRIVACY impact:** Documentation / DPIA / RoPA output subsystem (privacy notice templates must include LLM training disclosure for CT tenants). Tenant Config / Admin UI (new CT-specific privacy notice field). Low banner/consent mechanism impact.
**Action needed by:** June 25, 2026 (customers need updated privacy notice live before July 1). Recommend engineering adds a Connecticut LLM-disclosure toggle to tenant config and updates the CT privacy-notice template.
**Note:** The CTDPA amendment also includes AI-related automated decision-making provisions (effective July 1, 2026) but those are outside cookies/consent scope for this digest.

---

## Item 2 -- EDPB CEF 2026: Coordinated Enforcement on GDPR Transparency (Articles 12-14)
**Added:** 2026-05-14 | **Scan:** tier1-daily | **Severity:** LOW (watch only; enforcement sweep underway)
**Jurisdiction:** EU/EEA (25 participating DPAs)
**Instrument:** EDPB Coordinated Enforcement Framework 2026 (launched March 19, 2026)
**What:** 25 national DPAs are conducting coordinated enforcement on GDPR Articles 12-14 transparency and information obligations throughout 2026. DPAs will contact controllers from different sectors via enforcement actions or fact-finding exercises. Consolidated report expected in H2 2026. This is a watch item: when DPAs start contacting specific sectors/companies, that may be a HIGH trigger event.
**ID-PRIVACY impact:** Privacy notice transparency, consent banner layering, and vendor disclosure adequacy are all directly in scope for Articles 12-13 (information provided at collection point). This enforcement sweep is likely to generate individual DPA enforcement actions later in 2026 that will require specific alerts.
**Action needed:** Monitor DPA announcements for sector-specific targeting; ensure all EU tenants have complete, current Articles 13-14 disclosure in their ID-PRIVACY privacy notice output. No code change required today.

---

## Item 3 -- India DPDP Act: Consent Manager Phase II (November 13, 2026)
**Added:** 2026-05-14 | **Scan:** tier1-daily | **Severity:** LOW (T-183 days)
**Jurisdiction:** India
**Instrument:** DPDP Rules 2025, Rule 4 (Consent Manager), notified November 13, 2025 by MeitY; Phase II effective November 13, 2026
**What:** Consent Manager registration opens November 13, 2026. Only India-incorporated entities with INR 2 crore minimum net worth qualify. Foreign-incorporated CMPs (including DataSafeguard if not India-incorporated) cannot operate as registered Consent Managers. Data Principals must be able to give, manage, review, and withdraw consent via a single Consent Manager interface registered with the DPBI.
**ID-PRIVACY impact:** Depends on DataSafeguard's India go-to-market strategy. If ID-PRIVACY operates as a Consent Manager in India, corporate structure and registration planning is needed immediately. If ID-PRIVACY provides the underlying technology to a registered Indian Consent Manager partner, the API/integration design is the priority. Engineering lead time is significant.
**Action needed:** Business/legal decision on India Consent Manager posture required by July 2026 (to allow registration prep by November 2026 if applicable).

---

## Item 4 -- SECURE Data Act (US federal privacy bill, introduced April 22, 2026)
**Added:** 2026-05-14 | **Scan:** tier1-daily | **Severity:** LOW (watch only; bill not enacted)
**Jurisdiction:** United States (federal)
**Instrument:** SECURE Data Act (Securing and Establishing Consumer Uniform Rights and Enforcement over Data Act), introduced by House Republicans to House Energy & Commerce Committee
**What:** Proposed comprehensive federal privacy framework with opt-out for targeted advertising, consent for sensitive data, and federal preemption of state laws. If enacted, would significantly simplify ID-PRIVACY's US multi-state jurisdiction routing. Does not include private right of action or universal opt-out mechanism requirements. Legislative prospects uncertain.
**Action needed:** Monitor legislative progress. If the bill advances to committee vote, escalate to MEDIUM and assess impact on US-state jurisdiction routing and state-law preemption assumptions.
