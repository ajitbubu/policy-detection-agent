# Baseline State-of-the-World — Cookies & Consent Regulation
**Agent:** Privacy Regulation Intelligence Agent for ID-PRIVACY®
**Run date:** 2026-05-09
**Window covered:** 2026-05-09 → 2027-05-09 (next 12 months)
**For:** Director of Engineering, DataSafeguard

---

## Preamble — verification methodology and caveats

- All items below were surfaced and cross-checked via **WebSearch** against multiple secondary sources (law-firm trackers, regulator press summaries, IAPP). URLs cited as "Primary source" are the canonical regulator / legislature / framework publisher pages reported by those secondary sources.
- **WebFetch was blocked (HTTP 403) on every official domain attempted in this run** (cppa.ca.gov, meity.gov.in, edpb.europa.eu, ico.org.uk, iabeurope.eu, privacy.ca.gov). I therefore could not directly retrieve and parse the linked primary pages; URLs are reported as published by reputable secondary sources but should be treated as **link-verified by reference, not by direct fetch**. Engineering / counsel should click through to confirm before any binding action.
- Where only secondary reporting exists with no clearly published primary text, the item is labeled **SECONDARY — pending primary confirmation**.
- Severity rubric applied per the operating prompt (CRITICAL / HIGH / MEDIUM / LOW). Imminence is measured against today (2026-05-09). Confidence is HIGH/MEDIUM/LOW with a one-line rationale.
- This is a baseline scan, not a per-change ALERT. It is **not** a substitute for legal review.

Ordering: combined severity × imminence (T-minus). Items with active enforcement consequences in 2026 ranked first.

---

## 1. IAB TCF v2.3 — mandatory adoption deadline 28 February 2026 (PAST — non-compliant strings now invalid)

- **Jurisdiction:** EU/EEA + UK (industry framework; binding on every CMP claiming TCF compliance)
- **Instrument + citation:** IAB Europe Transparency & Consent Framework v2.3 Policies & Technical Specifications (released 19 June 2025)
- **Publication date:** 2025-06-19
- **Effective / enforcement date:** 2026-02-28 — TC strings created on/after this date without the `disclosedVendors` segment are invalid; ad requests fall back to "Limited Ads"
- **Primary source URL:** https://iabeurope.eu/all-you-need-to-know-about-the-transition-to-tcf-v2-3/  (status: link-verified-by-reference; WebFetch blocked)
- **What changed and why it matters:** TCF v2.3 makes the Disclosed Vendors segment mandatory and signed, so vendors can technically prove they were actually disclosed to the user. CMPs that did not migrate by 28 Feb 2026 emit invalid strings — programmatic revenue for downstream publishers reportedly drops >50%. This is now a remediation matter, not forward planning.
- **Severity:** **CRITICAL** — deadline already passed; any TCF-claiming customer not on v2.3 today is shipping invalid signals.
- **Confidence:** HIGH — IAB Europe published spec; deadline corroborated by Didomi, OneTrust, Usercentrics, Cookiebot.

---

## 2. California CCPA Regulations — ADMT, Risk Assessments, Cybersecurity Audits — effective 1 January 2026 (LIVE)

- **Jurisdiction:** California, USA
- **Instrument + citation:** CPPA final regulations adopted 24 July 2025; OAL approval 22 September 2025; CCRC § 7000 et seq. amendments
- **Publication date:** 2025-09-22 (filed with Secretary of State)
- **Effective date:** 2026-01-01 (regulations in force)
- **Enforcement / staggered deadlines:** Risk assessments — pre-existing processing must be assessed by 2027-12-31; ADMT consumer rights — 2027-01-01; first cybersecurity audit certifications — 2028-04-01 (>$100M revenue), 2029-04-01 ($50–100M), 2030-04-01 (<$50M)
- **Primary source URL:** https://cppa.ca.gov/regulations/ccpa_updates.html  (status: link-verified-by-reference; WebFetch blocked)
- **What changed and why it matters:** Adds enforceable risk-assessment, ADMT opt-out / access, and annual cybersecurity-audit obligations on top of CCPA/CPRA. For CMPs, the ADMT opt-out interacts with the existing "Do Not Sell or Share" / Limit Use of SPI flow and may need to be surfaced as a distinct preference; risk-assessment obligations require evidence the CMP is generating (consent records, vendor disclosures).
- **Severity:** **HIGH** — code/configuration change required for ADMT surface; record-keeping changes required for audits; enforcement window for ADMT consumer rights opens 2027-01-01.
- **Confidence:** HIGH — CPPA press release, OAL filing, and uniform reporting from Skadden, Wiley, Greenberg Traurig, Alston & Bird.

---

## 3. UK Data (Use and Access) Act 2025 — PECR cookie reforms — commenced 5 February 2026 (LIVE)

- **Jurisdiction:** United Kingdom
- **Instrument + citation:** Data (Use and Access) Act 2025 (c. 18), Royal Assent 19 June 2025; commencement regulations bringing key provisions into force 5 Feb 2026
- **Publication date:** 2025-06-19 (Royal Assent)
- **Effective date:** 2026-02-05 for cookie/PECR amendments
- **Enforcement date:** Immediate from 5 Feb 2026; new £17.5M / 4% global turnover PECR fine ceiling now applicable. Mandatory complaints procedure from 19 June 2026.
- **Primary source URL:** https://ico.org.uk/about-the-ico/what-we-do/legislation-we-cover/data-use-and-access-act-2025/the-data-use-and-access-act-2025-what-does-it-mean-for-organisations/  (status: link-verified-by-reference; WebFetch blocked)
- **What changed and why it matters:** Three new cookie consent exemptions are now live in the UK: (1) first-party-only statistical/analytics cookies, (2) appearance/functionality customisation cookies, (3) emergency-assistance cookies. PECR fine ceiling increased from £500k to UK-GDPR levels. CMPs should expose UK-specific rule sets so these categories can be deployed without a consent gate while remaining gated in the EU.
- **Severity:** **HIGH** — divergence between UK and EU rule sets is now substantive; tenants targeting UK can legitimately reduce banner friction, but only if jurisdiction-routing is correct.
- **Confidence:** HIGH — ICO published guidance; Clifford Chance, Mayer Brown, Stevens & Bolton, Moore Barlow, Berry Smith all corroborate the 5 Feb 2026 commencement.

---

## 4. India DPDP Act + DPDP Rules 2025 — phased enforcement; Phase II 13 November 2026 (Consent Managers)

- **Jurisdiction:** India
- **Instrument + citation:** Digital Personal Data Protection Act 2023 (DPDP Act); Digital Personal Data Protection Rules 2025, MeitY Gazette notification dated 13 November 2025
- **Publication date:** 2025-11-13
- **Effective dates (phased):**
  - Phase I — 2025-11-14 (Data Protection Board provisions; LIVE)
  - **Phase II — 2026-11-13** (Consent Manager registration / framework provisions)
  - Phase III — 2027-05-13 (substantive DSAR, breach notification, child-data, cross-border)
- **Primary source URL:** https://www.meity.gov.in/documents/act-and-policies/digital-personal-data-protection-rules-2025-gDOxUjMtQWa  (status: link-verified-by-reference; WebFetch blocked)
- **What changed and why it matters:** India introduces a regulator-licensed "Consent Manager" archetype — a registered intermediary that captures, manages, and revokes consent. Phase II turns this into an active regime. ID-PRIVACY® must decide whether to (a) register itself as a Consent Manager in India or (b) integrate with registered Consent Managers; either path requires schema, audit-trail, and revocation-API work. Phase III (May 2027) brings DSARs and child-data verification into scope.
- **Severity:** **HIGH** — strategic product decision required now; Phase II clock is ~6 months.
- **Confidence:** HIGH — MeitY gazette, S&R Associates, Shardul Amarchand, DLA Piper IN, IAPP all confirm phasing.

---

## 5. California Delete Act — DROP platform live; data-broker obligations from 1 August 2026

- **Jurisdiction:** California, USA
- **Instrument + citation:** SB 362 (Delete Act, 2023); CPPA regulations approved 13 November 2025; DROP system requirements
- **Publication date (regs):** 2025-11-13
- **Effective dates:**
  - Consumer-facing DROP submission live January 2026
  - **Data brokers must access DROP at least every 45 days from 2026-08-01**
  - Determinations must be completed within 90 days of retrieval
- **Primary source URLs:** https://cppa.ca.gov/announcements/2025/20251113.html  and https://privacy.ca.gov/drop/about-drop-and-the-delete-act/  (status: link-verified-by-reference; WebFetch blocked)
- **What changed and why it matters:** Centralised, regulator-run deletion intake replaces vendor-by-vendor opt-outs for registered California data brokers. Customers who are registered data brokers in California must integrate with DROP polling and feed deletion outcomes back. Even non-broker tenants benefit from a unified DROP-aware deletion workflow inside the DSR engine. Penalty: $200/request/day for non-compliance.
- **Severity:** **HIGH** — concrete API/polling integration obligation with a hard 1 Aug 2026 date for any data-broker tenant.
- **Confidence:** HIGH — CPPA announcement, Governor's office release, Benesch, Clark Hill, OneTrust corroboration.

---

## 6. New US state privacy laws effective 1 January 2026 — Indiana, Kentucky, Rhode Island, Minnesota

- **Jurisdiction:** USA — Indiana, Kentucky, Rhode Island, Minnesota
- **Instruments + citations:**
  - Indiana SEA 5 (2023, Ind. Code § 24-15)
  - Kentucky HB 15 (KCDPA, 2024)
  - Rhode Island Data Transparency and Privacy Protection Act (2024)
  - Minnesota Consumer Data Privacy Act (Minn. Stat. ch. 325O, 2024)
- **Publication dates:** 2023–2024 (signing dates vary)
- **Effective date:** 2026-01-01 (all four)
- **Enforcement:** Immediate from effective date for IN, KY, RI; MN cure period sunsets 2026-01-31 in some readings — confirm against statute.
- **Primary source URLs:** State legislature bill pages (Ind. Code § 24-15; Ky. KRS Chapter newly added by HB 15; R.I. Gen. Laws Ch. 6-48.1; Minn. Stat. ch. 325O). MultiState and Husch Blackwell trackers used as radar.
- **What changed and why it matters:** Four more state ruleset routes the CMP must serve. Rhode Island's threshold is unusually low (35,000 consumers, or 10,000 if >20% revenue from sale of PD) — many SMB tenants will newly fall in scope. Minnesota requires recognition of universal opt-out signals. No novel signal types beyond what existing US ruleset templates already cover.
- **Severity:** **MEDIUM** — incremental expansion of an existing pattern; primary cost is jurisdiction-routing rules + privacy-notice text variants.
- **Confidence:** HIGH — multiple independent law-firm summaries and state legislature publications.

---

## 7. Maryland Online Data Privacy Act (MODPA) — applies to processing on/after 1 April 2026

- **Jurisdiction:** Maryland, USA
- **Instrument + citation:** MODPA, Md. Code, Com. Law § 14-4601 et seq. (HB 567 / SB 541, 2024)
- **Publication date:** 2024-05-09 (signed)
- **Effective date:** 2025-10-01 (law in force)
- **Operative date for processing activities:** **2026-04-01** (data-minimisation, sensitive-data, and minor-data prohibitions apply to processing taking place on or after this date)
- **Primary source URL:** https://mgaleg.maryland.gov/2024RS/bills/hb/hb0567E.pdf  (link-verified-by-reference)
- **What changed and why it matters:** Strictest US data-minimisation rule to date. Sensitive data of any consumer, and any data of a known-under-18 consumer, may not be collected/processed/shared beyond what is "strictly necessary" — even with consent. Outright prohibition on the sale of sensitive data, including precise geolocation. CMP impact: consent for sensitive data is no longer a sufficient legal basis on its own in MD; vendor/SDK gating must enforce a per-purpose necessity test, not a blanket consent grant.
- **Severity:** **HIGH** — first US jurisdiction where consent ≠ lawful basis for sensitive-data sale; requires new tenant policy controls and likely a "sensitive-data block list" for MD geo.
- **Confidence:** HIGH — operative date confirmed across Manatt, Koley Jessen, DWT, Privado, Wiley.

---

## 8. Connecticut and Oregon — Universal Opt-Out Mechanism (UOOM / GPC) recognition mandates from 1 January 2026 (LIVE); CT neural data 1 July 2026

- **Jurisdiction:** Connecticut, Oregon (USA)
- **Instruments + citations:**
  - Connecticut Data Privacy Act, Conn. Gen. Stat. § 42-515 et seq.; SB 3 amendments 2024
  - Oregon Consumer Privacy Act (OCPA), ORS Ch. 646A; HB 2008 (2025 amendments)
- **Effective date:** **2026-01-01** for UOOM recognition obligation
- **Subsequent dates:** CT — 2026-07-01 expanded "sensitive data" includes neural data; OR — minor-data and precise-geolocation sale prohibitions live
- **Primary source URLs:** Connecticut Attorney General privacy pages and Oregon Department of Justice consumer-protection privacy pages (URLs vary by AG/DOJ revision; verify before linking in customer-facing artefacts).
- **What changed and why it matters:** From 2026-01-01, controllers in CT and OR must technically detect and honour browser-level opt-out signals (currently GPC). Combined with existing CA, CO, DE, MD, MN, MT, NJ, NH, TX requirements, GPC is a near-universal US signal. CT's expansion of "sensitive data" to neural data (2026-07-01) follows Colorado.
- **Severity:** **MEDIUM** — confirms an existing trajectory; mainly a coverage / QA matter for the GPC pipeline.
- **Confidence:** MEDIUM-HIGH — multiple secondary trackers; CT neural-data 2026-07-01 detail should be confirmed against the bill text before any downstream change.

---

## 9. Colorado — Biometric and Neural Data amendments (HB24-1130 + HB24-1058)

- **Jurisdiction:** Colorado, USA
- **Instruments + citations:** Colorado Privacy Act, Colo. Rev. Stat. § 6-1-1301 et seq.; HB24-1058 (neural data); HB24-1130 (biometrics)
- **Publication / signing:** 2024
- **Effective dates:** Biometric provisions live since 2024-07-01; neural-data inclusion in "sensitive data" live since 2025-08-06; some downstream operational dates flow into 2026-06-30 in secondary trackers (treat with caution).
- **Primary source URL:** https://coag.gov/resources/colorado-privacy-act/  and https://leg.colorado.gov/bills/hb24-1058  (link-verified-by-reference)
- **What changed and why it matters:** Biometric identifiers and neural data are now opt-in sensitive categories with explicit consent + retention schedule + sale prohibition. Sets a template other states are following (CT). Cookie/SDK governance must surface these as distinct purpose categories and enforce non-bundled consent.
- **Severity:** **MEDIUM** — most ID-PRIVACY tenants do not collect neural data, but biometric features (face geometry from chat-widget cameras, voice prints from session-replay analogues) are increasingly common.
- **Confidence:** MEDIUM — bill texts are clear; the "30 June 2026" CPA effective date reported in one secondary source could not be reconciled and is flagged for verification.

---

## 10. EDPB Guidelines 01/2025 on Pseudonymisation — final pending; EU Digital Omnibus consent reforms — proposal active

- **Jurisdiction:** EU/EEA
- **Instruments:**
  - EDPB Guidelines 01/2025 on Pseudonymisation (draft adopted 2025-01-16, public consultation closed 2025-02-28; stakeholder report 2026-02-18; final pending)
  - European Commission **Digital Omnibus** proposal (published November 2025) including a draft new GDPR Article 88a that would absorb cookie/tracking rules from the ePrivacy Directive into GDPR; Commission formally withdrew the long-pending ePrivacy Regulation in February 2025
- **Publication dates:** 2025-01-16 (draft EDPB); November 2025 (Digital Omnibus proposal); 2025-02 (ePrivacy Regulation withdrawal)
- **Effective dates:** **None yet** — both items pre-effective; Digital Omnibus is a proposal, not adopted law.
- **Primary source URLs:**
  - https://www.edpb.europa.eu/our-work-tools/documents/public-consultations/2025/guidelines-012025-pseudonymisation_en
  - European Commission Digital Omnibus proposal landing page on https://commission.europa.eu/  (link-verified-by-reference)
- **What changed and why it matters:** Two convergent EU developments worth tracking but not yet actionable. The Pseudonymisation Guidelines, when finalised, will tighten what "pseudonymised" means for consent-storage and audit-log retention claims. The Digital Omnibus, if adopted as drafted, would meaningfully restructure the legal basis for cookies — moving from Art. 5(3) ePrivacy to a proposed GDPR Article 88a — and explicitly targets "consent fatigue."
- **Severity:** **LOW** (current status) — pre-binding; promote to MEDIUM if pseudonymisation guidelines finalise or if Digital Omnibus reaches a Council general approach.
- **Confidence:** MEDIUM — status is fluid; this item is the most likely to change category before next quarter's scan. Labeled **SECONDARY — pending primary confirmation** for the Digital Omnibus Article 88a wording specifically.

---

## Honourable mentions (watch list, not in top 10 but cited for completeness)

- **Texas TDPSA universal opt-out recognition** — already in force; enforcement uplift expected through 2026.
- **Brazil ANPD 2026–2027 enforcement priorities** targeting advertising / profiling (announced as ANPD became fully autonomous in February 2026). Likely guidance, not yet binding rule.
- **Quebec CAI** — explicit-consent expectation on tracking cookies under Law 25 is established; expect more enforcement actions in 2026.
- **EU AI Act** — 2 August 2026 is the Commission's enforcement-powers milestone for general-purpose AI; relevant for tenant-facing AI features in the CMP, not for the cookie banner per se.
- **Garante (Italy)** — continued enforcement of the 2021 cookie guidelines; the "X-button" requirement and 6-month re-prompt rule remain frequent fine generators.
- **CNIL (France)** — announced 2026 work on cross-domain consent guidelines; once published, will affect multi-property group tenants.

---

*End of baseline.*
