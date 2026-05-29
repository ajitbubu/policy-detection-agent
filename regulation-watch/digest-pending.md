# ID-PRIVACY Weekly Regulatory Digest — Tier 2 Scan
**Scan date:** 2026-05-29
**Scan type:** weekly-tier2
**Prepared for:** Ajit Sahu, Director of Engineering, DataSafeguard
**Email recipient:** asahu@datasafeguard.ai
**Severity window:** LOW items only (MEDIUM+ issued as individual alerts)
**Lookback window:** 2026-05-09 to 2026-05-29 (since last Tier 2 scan)

---

## Executive Summary

Seven LOW-severity regulatory watch items identified across APAC, MENA, Canada, EU,
and Brazil in the Tier 2 weekly scan. No item in this digest requires an immediate code
change or constitutes a standalone MEDIUM/HIGH/CRITICAL alert. Three items are
approaching the threshold where severity will be upgraded at next scan if primary
confirmation arrives or legislative progress accelerates.

Items are ordered by proximity of next material milestone.

---

## ITEM T2-2026-05-29-01
**Jurisdiction:** Australia
**Instrument:** Privacy Act 1988 (Cth) as amended by Privacy and Other Legislation Amendment Act 2024 — Small Business AML/CTF Expansion
**Issuing body:** Attorney-General's Department / OAIC
**Published:** 2024-12-10 (Royal Assent)
**Effective:** 2026-07-01 (T-minus 33 days)
**Primary source:** https://www.oaic.gov.au/privacy/privacy-guidance-for-organisations-and-government-agencies/organisations/small-business
**Secondary refs:** https://www.heliossalinger.com.au/2026/03/12/privacy-reforms-to-impact-over-100000-small-businesses/ ; https://iapp.org/news/a/amending-australias-privacy-act-small-businesses-bigger-responsibilities
**Severity:** LOW (scope expansion does not change CMP technical requirements; banner
behavioural obligations under APPs remain the same as for existing covered entities)
**Confidence:** HIGH

**What changed:** From 1 July 2026, the Privacy Act will apply for the first time to
approximately 100,000 small businesses that become reporting entities under the
Anti-Money Laundering and Counter-Terrorism Financing Act reforms (lawyers,
accountants, conveyancers, real estate professionals, high-value goods dealers). The
existing A$3 million turnover small-business exemption is NOT being removed for
non-AML/CTF businesses — that is a separate tranche 2 reform still in consultation.

**Why it matters for ID-PRIVACY:**
- Net-new customer segment (SMB AML/CTF entities in Australia) will need Privacy
  Act-compliant consent banners and privacy notices from 1 July 2026.
- No new technical consent requirements are introduced; existing Australia/APP ruleset
  in the platform is adequate.
- Geo/Jurisdiction Routing: the AU ruleset should already trigger for these entities;
  confirm the targeting test covers newly in-scope entities (they were not previously
  APP entities).

**Recommended action (LOW — digest only):**
- Product: add Australia SMB AML/CTF scope expansion to customer-facing "what's
  changing" documentation so that newly in-scope tenants know they must deploy a banner.
- Tenant Config / Admin UI: confirm the AU jurisdiction route does not rely on a
  "large entity only" filter that would exclude new SMB tenants.
- No code change required.

---

## ITEM T2-2026-05-29-02
**Jurisdiction:** Australia
**Instrument:** Privacy (Children's Online Privacy) Code 2026 — Exposure Draft
**Issuing body:** Office of the Australian Information Commissioner (OAIC)
**Published:** 2026-03-31 (exposure draft)
**Consultation closes:** 2026-06-05 (T-minus 7 days)
**Target registration date:** 2026-12-10 (T-minus ~195 days)
**Primary source:** https://www.oaic.gov.au/privacy/privacy-registers/privacy-codes/childrens-online-privacy-code ; https://www.oaic.gov.au/__data/assets/pdf_file/0020/262631/Exposure-Draft-Childrens-Online-Privacy-Code.pdf
**Secondary refs:** https://www.bakermckenzie.com/en/insight/publications/2026/05/australia-childrens-online-privacy-code-exposure-draft ; https://privacymatters.dlapiper.com/2026/04/australia-exposure-draft-of-childrens-online-privacy-code-signals-tougher-standards/
**Severity:** LOW (pre-binding; exposure draft only; not yet registered)
**Confidence:** HIGH for publication fact; MEDIUM for final form (consultation ongoing)

**What changed:** The OAIC published an exposure draft of a mandatory Children's Online
Privacy Code applying to social media, electronic services, and designated internet
services covered by the Privacy Act. Key provisions include: consent required before
using children's personal information for targeted advertising; children must be notified
when parents consent on their behalf; deletion rights for children must be enabled;
geolocation tracking of children requires explicit notification.

**Why it matters for ID-PRIVACY:**
- Consent Banner: once the Code is registered (target 10 December 2026), any tenant
  operating a social media or online service in Australia that is accessible to children
  must enforce child-consent flows and age-gating before enabling advertising cookies.
- Vendor / SDK Governance: advertising and tracking SDKs must be blocked for child-
  identified sessions in Australian-routed journeys.
- Cookie Classification ML: targeted advertising category must be surfaced as requiring
  separate, non-bundled consent for under-18 users.
- This is architecturally similar to the UK Children's Code (Age Appropriate Design Code)
  and US COPPA — if those are implemented, the Australian variant has the same pattern.

**Recommended action (LOW — digest only):**
- Product / Legal: monitor OAIC final Code publication (expected Q4 2026). Promote to
  MEDIUM at registration.
- Engineering: review existing UK/COPPA child-safe mode implementation for
  portability to AU jurisdiction routing.
- No code change required today.

---

## ITEM T2-2026-05-29-03
**Jurisdiction:** Australia
**Instrument:** Privacy Act 1988 (Cth) — Automated Decision-Making (ADM) Transparency Obligation
**Issuing body:** Attorney-General's Department
**Published:** 2024-12-10 (Royal Assent, Privacy and Other Legislation Amendment Act 2024)
**Effective:** 2026-12-10 (T-minus ~195 days)
**Primary source:** https://www.oaic.gov.au/privacy/australian-privacy-principles/australian-privacy-principles-guidelines/chapter-1-app-1-open-and-transparent-management-of-personal-information
**Secondary refs:** https://www.twobirds.com/en/insights/2026/australia/australias-new-adm-transparency-obligation-oaic-signals-a-broad-reading-ahead-of-december-2026 ; https://mk.com.au/automated-decision-making-current-privacy-obligations-and-whats-in-the-pipeline-for-2026/
**Severity:** LOW (documentation / privacy policy change; no banner code change)
**Confidence:** HIGH

**What changed:** From 10 December 2026, APP entities must include in their privacy
policy a description of (a) the kinds of personal information used in automated
decision-making processes and (b) the kinds of decisions made substantially or solely
by automated means if those decisions could significantly affect individual rights or
interests. The OAIC has signalled a broad reading of "significantly affect." Applies
to any decision made on or after 10 December 2026, retroactively applied to existing
systems.

**Why it matters for ID-PRIVACY:**
- Documentation / DPIA / RoPA: consent-management decisions driven by ML scoring
  (e.g., cookie classification, consent signal routing) may trigger the disclosure
  obligation for tenants that rely on the platform's output.
- Tenant Config / Admin UI: if ID-PRIVACY generates or assists in generating
  privacy-notice text for Australian tenants, the ADM disclosure field needs to be
  surfaced as a required field for AU jurisdictions from December 2026.
- Not a banner change; this is a privacy-policy document-generation and tenant-guidance
  obligation.

**Recommended action (LOW — digest only):**
- Product: design an "ADM disclosure" field in the AU privacy-notice template for
  release before 10 December 2026.
- Legal: confirm whether the platform's own ML classifier outputs (used to gate
  consent) constitute ADM under the broad OAIC reading.

---

## ITEM T2-2026-05-29-04
**Jurisdiction:** South Korea
**Instrument:** PIPA (Personal Information Protection Act) Amendment — 10% Turnover Fines + CEO Accountability
**Issuing body:** National Assembly of Korea / PIPC
**Published:** 2026-02-12 (National Assembly passage); 2026-03-10 (promulgation)
**Effective:** 2026-09-11 (T-minus ~105 days)
**Primary source:** https://www.pipc.go.kr/eng/user/ltn/new/noticeDetail.do?bbsId=BBSMSTR_000000000001&nttId=2488
**Secondary refs:** https://iapp.org/news/a/south-korea-overhauls-pipa-and-ties-fines-to-ceo-accountability ; https://www.hunton.com/privacy-and-cybersecurity-law-blog/south-korea-amends-privacy-law-to-authorize-fines-of-up-to-10-of-total-revenue
**Severity:** LOW (no change to cookie/consent technical requirements; penalty structure
and governance change only)
**Confidence:** HIGH for passage and effective date; MEDIUM for downstream consent-
specific guidance (not yet published)

**What changed:** South Korea's most significant PIPA overhaul since 2023 introduces:
(1) administrative fines up to 10% of total global revenue (up from fixed amounts) for
intentional or grossly negligent violations affecting 10M+ individuals or repeat within
3 years; (2) the CEO/representative is now the designated "ultimate person responsible"
for personal information protection; (3) breach notification scope expanded to include
forgery, alteration, and destruction; (4) enhanced consent requirement where cookie
data is combinable to identify individuals (explicit opt-in required).

**Why it matters for ID-PRIVACY:**
- Consent Signals / Geo Routing: the combinability-to-identification threshold for
  explicit opt-in may require the KR jurisdiction ruleset to tighten from opt-out
  analytics cookies to opt-in where cross-site identifiers are in use.
- Audit / Logging: the higher fine ceiling and CEO liability mean tenants with Korean
  operations will place greater demand on audit-trail completeness and exportable proof-
  of-consent records.
- No immediate code change required before legal review of the combinability standard.

**Recommended action (LOW — digest only):**
- Legal: review whether the combinability-to-identification standard in the amended
  PIPA creates a gap vs. the current KR ruleset (which may treat analytics cookies as
  requiring only opt-out).
- Engineering: ensure the KR consent proof-of-consent log exports are fully available;
  this is a high-fine jurisdiction from 11 September 2026.
- Promote to MEDIUM if PIPC issues interpretive guidance on the combinability standard
  before the effective date.

---

## ITEM T2-2026-05-29-05
**Jurisdiction:** China (PRC)
**Instrument:** (a) Cybersecurity Law Amendment (effective 2026-01-01); (b) Personal Information Outbound Certification Measures / GB/T 46068-2025 national standard (effective 2026-03-01)
**Issuing body:** Cyberspace Administration of China (CAC) / SAMR
**Published:** 2025-10-28 (CSL amendment); 2025-10-14 (Certification Measures Decree No. 20)
**Effective:** 2026-01-01 (CSL amendment); 2026-03-01 (GB/T 46068-2025)
**Primary source:** https://www.cac.gov.cn/ (SECONDARY — pending direct-fetch confirmation; corroborated by Mayer Brown, Latham, Reed Smith, DLA Piper)
**Secondary refs:** https://www.mayerbrown.com/en/insights/publications/2025/12/china-finalises-amendments-to-the-cybersecurity-law-what-businesses-need-to-know-before-1-january-2026 ; https://www.lw.com/en/insights/chinas-cybersecurity-law-amendments-increase-penalties-broaden-extraterritorial-enforcement ; https://www.reedsmith.com/articles/china-approves-major-amendments-to-cybersecurity-law/
**Severity:** LOW (both items already effective; no new consent-banner change triggered;
cross-border transfer tightening is primarily an SCCs / certification track issue)
**Confidence:** HIGH for legislative facts; SECONDARY label retained for primary URL

**What changed:**
(a) CSL Amendment: amended Article 42 explicitly requires network operators to comply
with the PIPL for personal information processing, eliminating prior interpretive
ambiguity. Penalty ceiling raised to RMB 10M for network operators.
(b) Certification Measures + GB/T 46068-2025: new pathway for cross-border personal
information transfer via CAC-approved certification institutions; technical standard
provides interoperability and security certification criteria.

**Why it matters for ID-PRIVACY:**
- Cross-border Transfer Mechanism: tenants routing consent data or user profiles outside
  China must now consider the certification pathway alongside the existing CAC security
  assessment route. If ID-PRIVACY processes consent records for users in China and
  transfers them to non-China infrastructure, a transfer mechanism must be in place.
- Consent Capture & Storage: the explicit PIPL compliance overlay means Chinese-
  operation tenants must ensure consent records meet PIPL's format, retention, and
  revocability requirements — not just the generic platform defaults.
- No banner UI change required; architecture/data-flow documentation change.

**Recommended action (LOW — digest only):**
- Legal: confirm whether ID-PRIVACY's data processing for China-targeted tenants
  triggers CBDT obligations and, if so, which transfer mechanism applies.
- Engineering: flag to the data-residency working group; no code change today.

---

## ITEM T2-2026-05-29-06
**Jurisdiction:** Brazil
**Instrument:** ANPD 2026-2027 Enforcement Priorities — Targeted Advertising / Profiling
**Issuing body:** Autoridade Nacional de Proteção de Dados (ANPD)
**Published:** 2026-02 (ANPD independence + enforcement plan announced)
**Effective:** Ongoing enforcement posture — five thematic investigations initiated
**Primary source:** https://www.gov.br/anpd/ (SECONDARY — direct fetch not available; corroborated by CADE Project, ZwillGen, ICLG)
**Secondary refs:** https://cadeproject.org/updates/brazils-data-protection-authority-sets-enforcement-priorities-for-2026-2027/ ; https://iclg.com/practice-areas/data-protection-laws-and-regulations/brazil
**Severity:** LOW (no new rule; enforcement priority announcement; existing LGPD cookie
guidance from October 2022 remains the operative standard)
**Confidence:** MEDIUM — enforcement priorities confirmed by multiple secondary sources;
no primary ANPD gazette publication URL confirmed

**What changed:** The ANPD became a fully independent regulatory agency in February 2026
and published enforcement priorities that explicitly target secondary use of personal
data for targeted advertising and profiling. Five thematic investigations are underway.
The ANPD is recruiting 200 new specialist staff. Brazil's ANPD is now operationally
comparable to a mid-tier EU DPA in terms of enforcement capacity.

**Why it matters for ID-PRIVACY:**
- Consent Capture & Storage: BR tenants using behavioural advertising SDKs without
  clear LGPD-compliant consent records are now at elevated enforcement risk.
- Vendor / SDK Governance: the ANPD has signalled advertising/profiling SDKs are a
  target category; prior-consent gating for these SDKs in the BR ruleset should be
  reviewed for completeness.
- Cookie Classification ML: the ANPD's characterisation of cross-site behavioural
  profiles as personal data means the classifier must mark third-party advertising
  and profiling cookies as requiring consent (not relying on legitimate interest) in BR.

**Recommended action (LOW — digest only):**
- Legal / Product: review whether the BR jurisdiction ruleset correctly defaults to
  consent (not legitimate interest) for all advertising and profiling cookies.
- No new code change triggered; this is a risk-elevation notice.

---

## ITEM T2-2026-05-29-07
**Jurisdiction:** EU/EEA
**Instrument:** EU Digital Omnibus — Proposed new GDPR Articles 88a and 88b (cookie/tracking rules transferred from ePrivacy Directive)
**Issuing body:** European Commission
**Published:** 2025-11-19 (Commission proposal entered ordinary legislative procedure)
**Effective:** NOT YET — proposal only; Art. 88a would apply 6 months after entry into force; Art. 88b within 24 months
**Primary source:** https://commission.europa.eu/ (SECONDARY — pending primary URL; corroborated by Taylor Wessing, Osborne Clarke, Loyens & Loeff, Kennedy's Law, iubenda)
**Secondary refs:** https://www.taylorwessing.com/en/global-data-hub/2026/the-digital-omnibus-proposal/gdh---the-digital-omnibus---cookies ; https://www.osborneclarke.com/insights/digital-omnibus-reshapes-eu-cookie-rules-leaves-banner-fatigue-largely-intact ; https://www.loyensloeff.com/insights/news--events/news/digital-omnibus-what-the-proposed-changes-mean-for-gdpr-privacy-and-cookies/
**Severity:** LOW (proposal; not adopted law; but architecturally significant)
**Confidence:** HIGH for proposal content; LOW for final form and timeline

**What changed (proposal as drafted):**
- Art. 88a: Consent remains the default for cookies/tracking. New requirements if
  adopted: (1) refusal must be achievable via a single click; (2) if user refused,
  controller may not re-request consent for the same purpose for 6 months; (3) closed
  exemption list (transmission of communication, user-requested service, limited
  audience measurement, security). The ePrivacy Directive would be repealed.
- Art. 88b: Machine-readable consent signals must be technically supported; automated
  browser-level signals that express refusal are legally equivalent to manual refusal.
  This could significantly reduce the role of cookie banners for users who configure
  their browser to signal non-consent.

**Why it matters for ID-PRIVACY (forward planning):**
- Consent Banner: the 6-month cooling-off period post-refusal would require a
  consent-re-request suppression mechanism keyed to the EU jurisdiction and timed
  to the refusal timestamp (new consent-storage field).
- Consent Signals (GPC/TCF/GPP): Art. 88b is the EU's GPC-equivalent mandate. If
  enacted as drafted, browser-level opt-out signals must be technically honoured for
  EU users, creating a regulatory analogue to the existing US GPC obligation.
- Geo / Jurisdiction Routing: the entire EU cookie ruleset would shift from ePrivacy
  Directive to GDPR Art. 88a; licensing model for CMP claiming TCF compliance may
  change.
- Consent Storage & Proof: a new "refusal timestamp" field and re-request suppression
  logic would be needed.
- This is the single largest potential architectural change to the EU consent layer
  in a decade. Track closely.

**Recommended action (LOW — digest only):**
- Engineering horizon: begin architectural spike on 6-month refusal-suppression
  mechanism and machine-readable signal honoring for EU. No implementation yet.
- Legal / Product: monitor European Parliament and Council positions. Promote to
  MEDIUM when Council general approach is reached.

---

## STANDING WATCH ITEMS (no change since last scan, noted for completeness)

- **India DPDP Phase II (2026-11-13):** Consent Manager registration provisions live
  in ~168 days. No new developments since baseline. HIGH-severity alert RW-2026-05-09-01
  already on record for the Kochava item; DPDP Phase II is tracked in baseline. Remains
  HIGH per the baseline state-of-the-world (item 4). Will be re-examined at next Tier 1
  scan if MeitY issues new guidance.

- **ICO UK SAT Guidance (published 2026-04-29):** Confirmed as a material Tier 1 item
  rejected from the 2026-05-09 daily scan due to publication date outside the lookback
  window. PRIMARY SOURCE CONFIRMED: https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/04/final-storage-and-access-technologies-guidance-published/
  This item was flagged by the prior scan as a candidate for backfill or Tier 2 digest
  inclusion. It is a standalone HIGH-severity item (five new consent exemption categories,
  sub-chapters on "simple means of objecting" and multi-purpose SATs, DUAA fine uplift
  to GBP 17.5M / 4%). RECOMMENDATION: orchestrator should issue this as a separate
  HIGH alert (not a LOW digest item) because it requires a Consent Banner and
  Geo/Jurisdiction Routing code change. It is not included in this digest's LOW digest
  per the severity-routing rule (no MEDIUM+ items in the LOW digest).

- **EDPB Guidelines 01/2025 on Pseudonymisation:** Stakeholder report published
  2026-02-18; final guidelines still pending. Listed in EDPB Work Programme 2026-2027.
  No final publication yet. Remains LOW.

- **EU Digital Omnibus (Art. 88a/88b):** Covered under Item T2-2026-05-29-07 above.

- **Canada Bill C-27 / CPPA:** Killed by Parliament prorogation January 2025; Minister
  Solomon confirmed in June 2025 it will not return in prior form. PIPEDA and Quebec
  Law 25 remain the operative frameworks. No new federal legislative event.

- **Japan APPI amendment (draft 2025, effective est. 2027):** Draft law expected in
  2025; effect date estimated 2027. No enacted text yet. Low-priority watch item;
  Telecommunications Business Act External Data Transmission Rule (June 2023) is already
  the operative cookies/consent instrument in Japan and is covered in baseline.

- **Thailand PDPA — draft amendment bill (late 2025 consultation):** Consultation
  underway; no enacted text. Watch for 2026 developments.

- **UAE PDPL Executive Regulations (2024):** Operational; no new amendment in window.
  Existing consent requirements stable.

---

## Digest metadata

| Field | Value |
|---|---|
| Scan type | weekly-tier2 |
| Run date | 2026-05-29 |
| Lookback start | 2026-05-09 |
| Lookback end | 2026-05-29 |
| Tiers scanned | Tier 2 (APAC, MENA, LatAm, Canada, cross-border) |
| Items qualifying as LOW | 7 |
| Items escalated to standalone alert | 0 (ICO SAT guidance recommended for separate HIGH alert by orchestrator — not emitted here) |
| Highest severity in this digest | LOW |
| Items deduplicated (already in alerts-emitted.json) | 0 |
| Next Tier 2 scan due | 2026-06-05 |
