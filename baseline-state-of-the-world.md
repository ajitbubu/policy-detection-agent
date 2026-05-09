# Baseline State of the World — Cookies & Consent Regulation

**Prepared by:** Privacy Regulation Intelligence Agent (initial activation)
**For:** Ajit, Director of Engineering, DataSafeguard — ID-PRIVACY®
**Date generated:** 2026-05-09
**Window covered:** 2026-05-09 → 2027-05-09 (next 12 months)
**Method:** Web search + targeted source verification. WebFetch was blocked (HTTP 403) for many official domains in this run; primary URLs are listed as surfaced in indexed search results and labelled accordingly. Each item below should be re-verified by counsel before any code change is shipped.

Items are ordered by combined **severity × imminence** for an ID-PRIVACY-relevant CMP build. This is a watchlist, not legal advice.

---

## 1. IAB Europe TCF v2.3 — mandatory CMP transition

- **Jurisdiction:** EU/EEA (industry framework, applied across all 27 EU MS + UK adopters)
- **Instrument:** IAB Europe Transparency & Consent Framework v2.3 (Policies and Technical Specifications)
- **Issuing body:** IAB Europe
- **Published / Announced:** 2025-06-19
- **Effective (mandatory):** **2026-02-28** (already past — but enforcement, validator sweeps, and Google certification revalidation are ongoing through 2026)
- **Primary source URL:** https://iabeurope.eu/all-you-need-to-know-about-the-transition-to-tcf-v2-3/ (IAB Europe official; verified via search index, WebFetch was blocked)
- **What changed / why it matters:** TCF 2.3 introduces a mandatory **Disclosed Vendors** segment in the TC string and tightens UI/transparency requirements (vendor counts on layer 1, plain-language purpose examples, weekly Global Vendor List sync, bitfield consistency between UI and string). Google has confirmed its DSPs accept TCF 2.3 strings as of 2025-10-17 and will treat 2.2 strings as invalid post-deadline — meaning publishers running stale CMPs lose monetization. Automated IAB Europe validators are actively sweeping CMP implementations and can revoke certification.
- **Severity:** **HIGH** (revenue / certification exposure for any customer relying on TCF; in-window enforcement)
- **Confidence:** **HIGH** — IAB Europe published timeline; Google alignment confirmed by multiple secondary sources.

---

## 2. EU Digital Omnibus — proposed GDPR Article 88a (cookies into GDPR)

- **Jurisdiction:** EU (proposal stage; will apply to all controllers offering goods/services in EU)
- **Instrument:** Digital Omnibus Package — proposes new GDPR Articles 88a (cookies/terminal-equipment access) and 88b (machine-readable consent signals)
- **Issuing body:** European Commission; co-decision by Parliament and Council
- **Published:** 2025-11-19 (Commission proposal)
- **Effective:** Article 88a → 6 months after entry into force; Article 88b → 24 months after entry into force. Adoption expected mid-to-late 2026 under ordinary legislative procedure (could be accelerated by urgent procedure)
- **Enforcement:** TBD — depends on adoption
- **Primary source URL:** https://digital-strategy.ec.europa.eu/en/faqs/digital-package (Commission Digital Package FAQ, surfaced in search; SECONDARY confirmation via Reed Smith, Bird & Bird, Taylor Wessing, BEUC briefings)
- **What changed / why it matters:** Folds cookie/terminal-storage rules out of the ePrivacy Directive and into the GDPR. Mandates **single-click refusal**, **6-month re-prompt suppression** after a refusal, a closed list of exemptions (transmission, expressly-requested service, aggregated audience measurement, security), and machine-readable browser-level consent signalling. Direct CMP UX, signal handling, and cache/state implications across every EU tenant.
- **Severity:** **HIGH** (transformational for CMP UX and signal handling, but *not* yet enacted; preparatory work only at this stage)
- **Confidence:** **MEDIUM** — proposal text is public and stable, but final form, scope of Article 88b, and timeline are subject to trilogue. Track monthly.

---

## 3. UK DUAA 2025 — PECR amendments + new ICO guidance

- **Jurisdiction:** United Kingdom
- **Instrument:** Data (Use and Access) Act 2025 (DUAA), amending PECR; ICO Guidance on Storage and Access Technologies (final 2026-04-29)
- **Issuing body:** UK Parliament; Information Commissioner's Office
- **Published:** Royal Assent 2025-06-19
- **Effective:** Key data-protection / PECR provisions: **2026-02-05**. Mandatory data-protection complaints procedure: **2026-06-19**.
- **Enforcement:** Live as of 2026-02-05; PECR fines now uplifted to UK GDPR ceilings (£17.5m / 4% global turnover)
- **Primary source URL:** https://www.legislation.gov.uk/ukpga/2025/18/contents (legislation.gov.uk, verified via search; WebFetch blocked) and https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-the-use-of-storage-and-access-technologies/ (ICO official)
- **What changed / why it matters:** Three new categories of cookies become **exempt from prior consent** (statistical/audience-measurement-only first-party, UI personalisation/preferences, emergency assistance) — alongside pre-existing strictly-necessary. CMPs must reclassify many analytics cookies that were previously consent-gated, AND add the operational complaints workflow by June. Fine ceiling increases ~35× (£500k → £17.5m).
- **Severity:** **HIGH** (in-window, live, cookie classification + audit trail changes)
- **Confidence:** **HIGH** — Royal Assent confirmed, commencement order published, ICO guidance final.

---

## 4. India DPDP Act + Rules — staged commencement

- **Jurisdiction:** India
- **Instrument:** Digital Personal Data Protection Act, 2023 + Digital Personal Data Protection Rules, 2025
- **Issuing body:** Ministry of Electronics and Information Technology (MeitY); Data Protection Board of India (DPBI)
- **Published:** Rules notified 2025-11-13 (Gazette 2025-11-14)
- **Effective:** Three-phase rollout — Phase 1 (definitions, Board): 2025-11-14 (already live); **Phase 2 — Rule 4 Consent Managers: 2026-11-14** (in window); **Phase 3 — substantive obligations including notice & consent: 2027-05-13** (just outside 12-month window but customer prep starts now)
- **Enforcement:** DPBI begins functioning 2025-11-14; substantive enforcement aligns with Phase 3
- **Primary source URL:** https://www.meity.gov.in/documents/act-and-policies/digital-personal-data-protection-rules-2025-gDOxUjMtQWa (MeitY official, surfaced in search; WebFetch blocked) — also https://www.dpdpa.com/DPDP_Rules_2025_English_only.pdf (mirror copy of gazetted rules)
- **What changed / why it matters:** Introduces a **registered Consent Manager** intermediary model — a regulated entity that gives data principals a single interface to grant, manage, review, and withdraw consent across multiple Data Fiduciaries. Notice content is prescriptive (itemised data, specific purpose, direct withdrawal/complaint link). For ID-PRIVACY this opens both a compliance obligation (interoperate with Consent Managers) and a potential product positioning (ID-PRIVACY itself as a registered Consent Manager — strategic decision for product/legal).
- **Severity:** **HIGH** (Phase 2 in-window; novel architecture)
- **Confidence:** **HIGH** — gazetted text and dates confirmed via multiple legal trackers.

---

## 5. California — CCPA Regulations Package (Cybersecurity Audits, Risk Assessments, ADMT, Insurance, plus consent/dark-pattern clarifications)

- **Jurisdiction:** California, USA
- **Instrument:** CCPA Regulations (CPPA rulemaking package finalised 2025-09-22 by OAL)
- **Issuing body:** California Privacy Protection Agency (CPPA)
- **Published:** OAL approval 2025-09-22; filed with Secretary of State same day
- **Effective:** **2026-01-01** (most provisions); ADMT pre-use notice / opt-out / access: **2027-01-01**; Cybersecurity audit certifications phased 2028-2030 by revenue
- **Enforcement:** Live 2026-01-01 for the consent/dark-pattern clarifications
- **Primary source URL:** https://cppa.ca.gov/regulations/ccpa_updates.html (CPPA official; surfaced in search, WebFetch blocked) and https://cppa.ca.gov/announcements/2025/20250923.html (CPPA announcement)
- **What changed / why it matters:** Codifies that a consumer **closing or navigating away from a consent pop-up without affirmatively clicking accept does not constitute consent** (per se dark pattern). Adds opt-out, access, and pre-use notice rights against Automated Decisionmaking Technology (effective 2027-01-01 — must be designed in 2026). Triggers risk assessment and cybersecurity audit obligations (longer runway).
- **Severity:** **HIGH** (already in effect; affects all CA-facing customers)
- **Confidence:** **HIGH** — finalised regulations text published.

---

## 6. California AB 566 — "Opt Me Out Act" browser opt-out preference signal

- **Jurisdiction:** California, USA
- **Instrument:** AB 566 (2025), amending CCPA — opt-out preference signal in browsers
- **Issuing body:** California Legislature; signed by Governor (2025)
- **Published:** Signed 2025
- **Effective:** **2027-01-01**
- **Enforcement:** From effective date; CPPA + AG
- **Primary source URL:** https://leginfo.legislature.ca.gov/faces/billNavClient.xhtml?bill_id=202520260AB566 (official CA legislative info; verified via search, WebFetch blocked)
- **What changed / why it matters:** Requires **all browsers operating in California** (desktop and mobile) to ship native, easy-to-use opt-out preference signal functionality (OOPS) by 2027-01-01. Although the obligation is on browser vendors, it dramatically expands the population of users sending GPC-equivalent signals. CMPs must be hardened to honor signals from a much wider variety of sources (mobile in-app browsers, OS-integrated signals, etc.), not just desktop GPC extensions, and must not display banners that contradict an inbound signal.
- **Severity:** **HIGH** (large population impact, 8-month preparation window)
- **Confidence:** **HIGH** — bill enacted and chaptered.

---

## 7. Multi-state US — Universal Opt-Out becomes mandatory in Connecticut, Oregon (and amendments tightening Colorado, NJ rules)

- **Jurisdiction:** Connecticut, Oregon, Colorado, New Jersey (USA — multi-state)
- **Instrument:** CTDPA, OCPA, CPA, NJDPA + their implementing regs / amendments
- **Issuing body:** State legislatures; State AGs (CT, OR, NJ); Colorado AG; NJ Division of Consumer Affairs
- **Published / Effective dates relevant in window:**
  - **OR OCPA UOOM mandatory: 2026-01-01** (already live)
  - **OR cure period removed: 2026-01-01** (live)
  - **NJ proposed regulations adoption deadline: 2026-06-02**
  - **NJ cure period sunsets: ~2026-07-15**
  - **CT amendment lowering thresholds: 2026-07-01**
- **Enforcement:** Live (OR), imminent (NJ, CT)
- **Primary source URLs:**
  - OR DOJ: https://www.doj.state.or.us/consumer-protection/id-theft-data-breaches/privacy/
  - CT AG: https://portal.ct.gov/ag/sections/privacy/the-connecticut-data-privacy-act
  - CO AG (UOOM): https://coag.gov/opt-out/
  - NJ Consumer Affairs: https://www.njconsumeraffairs.gov/ocp/Pages/NJ-Data-Privacy-Law-FAQ.aspx
- **What changed / why it matters:** Ten-plus US states now require recognition of universal opt-out signals (GPC). Several lose their cure-period safe harbor in 2026, exposing CMP customers to direct enforcement. Geo-routing rules and signal-handling code paths must be precise: which states require the signal to act as an opt-out from sale only vs. sale+share+targeted advertising; which require deduplication with prior banner choices; which require user prompt to confirm.
- **Severity:** **HIGH** (multiple in-window dates, multi-state surface area)
- **Confidence:** **HIGH** — all dates confirmed via state AG / DOJ pages.

---

## 8. Maryland Online Data Privacy Act (MODPA) — applicability date

- **Jurisdiction:** Maryland, USA
- **Instrument:** Maryland Online Data Privacy Act (MODPA)
- **Issuing body:** Maryland General Assembly; Maryland AG enforces
- **Published:** Enacted 2024; took legal effect 2025-10-01
- **Effective (applies to processing):** **2026-04-01** (already crossed — but customers still mid-remediation)
- **Enforcement:** Live from 2026-04-01; MD AG
- **Primary source URL:** Maryland AG / EPIC summary (https://epic.org/maryland-online-data-privacy-act-comes-into-effect/ — SECONDARY) — Title 14 Subtitle 38 of the Commercial Law Article (request counsel to pull primary cite).
- **What changed / why it matters:** Strictest US state law on sensitive data: **prohibits sale of sensitive data outright — consent does not override**. Sensitive data includes precise geolocation, biometrics, neural/biological, health, children's data. Requires **data minimisation as a default** ("strictly necessary" test), not just notice-and-consent. CMPs must distinguish MD residents and apply a different processing rule (suppress sale category for sensitive data even if user clicks accept). Affects vendor/SDK governance.
- **Severity:** **HIGH** (in effect; novel "consent does not override" rule changes CMP logic)
- **Confidence:** **MEDIUM** — primary statute citation needs counsel verification; effective dates are well-documented.

---

## 9. EDPB Guidelines 2/2023 — Article 5(3) ePrivacy (final, in active enforcement)

- **Jurisdiction:** EU/EEA
- **Instrument:** EDPB Guidelines 2/2023 on the Technical Scope of Article 5(3) of the ePrivacy Directive (final version)
- **Issuing body:** European Data Protection Board
- **Published:** Adopted final version **2024-10-07**
- **Effective:** Immediately (interpretive guidance); national DPAs have been actively enforcing on this expanded scope through 2025-2026 (CNIL Google €325M, Shein €150M)
- **Primary source URL:** https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-22023-technical-scope-art-53-eprivacy-directive_en (EDPB official; surfaced in search, WebFetch blocked)
- **What changed / why it matters:** Confirms that the cookie consent rule applies far beyond cookies — to **pixels, URL/link decoration tracking, IP-only tracking, fingerprinting, IoT identifiers, mobile SDK identifiers, and local-processing-then-exfiltration**. Forces ID-PRIVACY's classification ML to widen its taxonomy and forces vendor governance to capture non-cookie tracking technologies. EDPB Cookie Banner Taskforce report was updated 2026-04-30 reaffirming "minimum threshold" positions on dark patterns and reject-all parity.
- **Severity:** **HIGH** (binding interpretive force across DPAs; enforcement is active and large)
- **Confidence:** **HIGH** — EDPB final adoption; Taskforce report update widely covered.

---

## 10. France CNIL — sustained enforcement of dark-pattern / reject-all parity

- **Jurisdiction:** France (with broad EU influence)
- **Instrument:** CNIL Guidelines and Recommendations on Cookies and Other Trackers (2020) + sustained 2025–2026 enforcement actions
- **Issuing body:** CNIL
- **Recent enforcement dates:** Google €325M (Sept 2025), Shein €150M (Sept 2025), Free Mobile €27M (Jan 2026), Free €15M (Jan 2026)
- **Effective:** Continuous enforcement; CNIL has stated cookie banners remain a 2026 priority
- **Primary source URL:** https://www.cnil.fr/en/dark-patterns-cookie-banners-cnil-issues-formal-notice-website-publishers (CNIL official) — and CNIL annual control plan page on cnil.fr
- **What changed / why it matters:** CNIL operationalises EDPB principles into concrete CMP UI rules: **same number of clicks** to reject as to accept, **equal visual weight** (size, color, contrast), no pre-checked boxes, no nudging copy. The size of the 2025 fines signals that pattern-level non-compliance now carries 9-figure exposure. Even US-headquartered DataSafeguard customers with .fr traffic are in scope.
- **Severity:** **HIGH** (precedent-setting fine sizes; immediate exposure for customers shipping non-parity banners)
- **Confidence:** **HIGH** for the enforcement actions themselves; **MEDIUM** for any specific 2026 CNIL guidance update — recheck within 30 days.

---

## Items considered but ranked below the top 10 (watchlist)

- **Brazil ANPD** — Operational independence achieved Feb 2026 and reported EU mutual adequacy decision Jan 2026. Cookie guidance is from 2022; no new binding rule confirmed. **Track for fresh resolution.**
- **Quebec Law 25** — Substantive provisions live since 2023-09-22. No new 2026-2027 effective date detected. Maintenance-mode enforcement.
- **Australia Privacy Act Tranche 2** — Politically signalled but **no introduced bill / no fixed timeline** as of activation. Watch-list only.
- **Texas TDPSA** — Live and being enforced aggressively by AG. No new in-window legislative date; included implicitly under multi-state UOOM monitoring.
- **EU AI Act** — Provisions on AI systems used in CMPs (e.g., consent-flow personalisation) may intersect with consent law in 2026; not currently a cookie rule per se.
- **Tennessee TIPA** — Effective 2025-07-01, in-effect but already past the in-window threshold for "imminent change."
- **EU–Brazil mutual adequacy decision** — Reported Jan 2026; pending primary confirmation in EU Official Journal.

---

## Notes on source verification

WebFetch returned HTTP 403 for many official `.gov`, `.europa.eu`, and `.gov.uk` domains in this run, likely due to environment-level egress controls. URLs above are taken from the surfaced search-result indexes against those primary domains and have not been individually re-fetched in this session. Before any external client-facing communication, **engineering/legal must independently re-verify every URL and date.**
