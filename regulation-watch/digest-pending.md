# Weekly LOW-Severity Digest — Tier 2 Scan
**Scan date:** 2026-05-09
**Scan type:** Weekly Tier 2 (APAC, MENA/Africa, LatAm, global cross-border, frameworks)
**Compiled by:** Privacy Regulation Intelligence Agent
**Recipient:** asahu@datasafeguard.ai
**To be emailed:** As Gmail draft (weekly cadence, Monday 08:00 ET)

---

## ITEM 1 — Japan APPI Amendment Enacted (Tier 2: APAC)

**Jurisdiction:** Japan
**Instrument:** Amendment to the Act on the Protection of Personal Information (APPI)
**Issuing body:** National Diet of Japan
**Published / Enacted:** 2026-04-14 (Cabinet approval 2026-04-07; Diet enactment 2026-04-14)
**Effective:** Within 2 years of promulgation — estimated by 2028 at the latest
**Primary source:** https://www.ppc.go.jp (Japan PPC; link-verified-by-reference)
**Secondary refs:** https://www.fisherphillips.com/en/insights/insights/japanese-cabinet-approves-appi-amendments | https://www.morihamada.com/en/insights/newsletters/138006 | https://iapp.org/news/a/japan-s-appi-amendment-bill-would-open-narrow-lane-for-some-ai-uses-tighten-rules-elsewhere | https://techjacksolutions.com/ai-brief/japan-amends-appi-to-allow-ai-training-on-sensitive-data-wit/

**What changed:** The Diet enacted an APPI amendment on 2026-04-14 that closes a gap in cookie/tracking governance by adding "contactable personally referable information" as a new protected category — explicitly including cookie IDs, email addresses, and phone numbers that allow direct contact with a specific individual. These items must now comply with APPI's prohibitions on improper use and unauthorised acquisition. The amendment also broadens consent exemptions for statistical/AI-development processing and adds parental-consent requirements for children under 16. The amendment enters force within 2 years of promulgation (i.e., by approximately April 2028).

**ID-PRIVACY impact:** LOW. The cookie-ID reclassification as "contactable personally referable information" means Japanese-targeting tenants must ensure cookie IDs linked to contact data are treated as personal information under APPI. The current consent-gate framework for Japan should already capture this, but the cookie classification taxonomy should be reviewed to ensure cookie IDs are not inadvertently classified as non-personal when combined with contact fields. No banner change required now; a classifier tag review is recommended in the next ML sprint cycle.

**Severity:** LOW — effective by ~2028; no immediate engineering action required. Place on 12-month watch.

**Confidence:** HIGH — IAPP, Fisher Phillips, Mori Hamada & Tsurumoto, Tech Jacks Solutions all corroborate enactment date and 2-year window.

---

## ITEM 2 — IAB GPP: Four New US State Sections Finalized (Tier 3: Framework)

**Jurisdiction:** United States (Maryland, Indiana, Kentucky, Rhode Island)
**Instrument:** IAB Tech Lab Global Privacy Platform (GPP) — new state sections for MD, IN, KY, RI published to production
**Issuing body:** IAB Tech Lab
**Published:** Fall 2025 (public comment closed 2025-12-01); sections finalized / pushed to production Q1 2026
**Effective:** Sections available for CMP implementation now; underlying state laws effective 2025-10-01 (MD) and 2026-01-01 (IN, KY, RI)
**Primary source:** https://iabtechlab.com/gpp/ | https://iabtechlab.com/press-releases/iab-tech-lab-expands-global-privacy-frameworks-with-gpp-updates-and-ddrf-v2-release/
**Secondary refs:** https://www.prnewswire.com/news-releases/iab-tech-lab-expands-global-privacy-frameworks-with-gpp-updates-and-ddrf-v2-release-302592077.html | https://martech.org/iab-tech-lab-pushes-privacy-standards-forward-with-gpp-and-ddrf-updates/

**What changed:** IAB Tech Lab finalized four new US state sections in the Global Privacy Platform (GPP) specification for Maryland (effective 2025-10-01), Indiana, Kentucky, and Rhode Island (all effective 2026-01-01). These match the underlying state privacy laws already in the ID-PRIVACY baseline (Indiana SEA 5, Kentucky HB 15, Rhode Island DTPPA, and Maryland MODPA). The update also includes a rearchitecture of the US section header / subsection structure to improve signal transparency and proposes two options (A and B) for communicating CMP-supported sections to downstream vendors — a gap that currently means some vendors cannot reliably determine which states a CMP has assessed.

**ID-PRIVACY impact:** LOW-to-MEDIUM. The underlying state laws were already in the baseline. The GPP sections must be implemented in ID-PRIVACY's GPP string builder to ensure downstream ad-tech vendors receive correctly encoded signals for MD, IN, KY, and RI users. If these four sections are not yet in the GPP string output, this is a gap. Additionally, the new SupportedSections header mechanism (Options A/B) is a forward-looking signal-transparency feature that should be on the engineering backlog.

**Action required:** (a) Confirm whether ID-PRIVACY's GPP string implementation includes sections for MD (section ID TBD per IAB spec), IN, KY, and RI. If not, add them. (b) Review the SupportedSections architecture options and schedule a discovery spike. Estimated: 3-5 engineering points.

**Severity:** LOW — states already in baseline; GPP implementation is a configuration/library update. Recommend targeting the next bi-weekly sprint.

**Confidence:** HIGH — IAB Tech Lab press release (PRNewswire), Martech.org, and PPC.land corroborate.

---

## ITEM 3 — Brazil ANPD Full Independence + Advertising Enforcement Priority (Tier 2: LatAm)

**Jurisdiction:** Brazil
**Instrument:** Administrative reorganisation — ANPD granted full regulatory independence (February 2026); ANPD published 2026-2027 enforcement priorities including advertising/profiling
**Issuing body:** Brazil ANPD (Autoridade Nacional de Proteção de Dados)
**Published:** February 2026
**Effective:** Immediate (institutional change, not a new rule)
**Primary source:** https://www.gov.br/anpd/pt-br (ANPD; link-verified-by-reference)
**Secondary refs:** https://iclg.com/practice-areas/data-protection-laws-and-regulations/brazil | https://securiti.ai/blog/brazil-anpd-guidance-on-cookies/

**What changed:** In February 2026, the ANPD transitioned from a federal autarchy under the Executive to a fully independent regulatory agency with expanded budget authority (200 new specialist positions in hiring). The ANPD simultaneously published its 2026-2027 enforcement priorities, explicitly targeting organisations using personal data for advertising and profiling. The underlying LGPD cookie/consent framework (consent as lawful basis for non-essential cookies; first- and second-layer banner requirement) has not changed. However, the ANPD's enhanced enforcement capacity means that what was previously a low-enforcement-risk jurisdiction is now materially higher risk. The ANPD has not yet brought a cookie-specific enforcement action, but explicitly advertising-focused priorities signal this is imminent.

**ID-PRIVACY impact:** LOW currently. No rule change. However, any Brazilian-market tenants who have deprioritised LGPD cookie compliance on the assumption that the ANPD would not enforce should be advised to review their banners. ID-PRIVACY's Brazilian geo-routing (requiring consent as lawful basis for analytics/advertising cookies) should be verified as active for BR-jurisdiction tenants.

**Action required:** (a) Confirm BR geo-routing is live and correctly gates non-essential cookies. (b) Draft a short customer advisory flagging the ANPD independence and enforcement priority shift to Brazilian-active tenants. No engineering change required.

**Severity:** LOW — no rule change. Watch item elevated from baseline "honourable mention."

**Confidence:** MEDIUM — ANPD independence confirmed; 2026-2027 priorities characterised via secondary sources. Primary ANPD website link-verified-by-reference (WebFetch unavailable). Confirm enforcement-priority document directly.

---

## ITEM 4 — New Zealand Privacy Amendment Act 2025 — IPP 3A Effective 2026-05-01 (Tier 2: APAC)

**Jurisdiction:** New Zealand
**Instrument:** Privacy Amendment Act 2025 — new Information Privacy Principle 3A
**Issuing body:** New Zealand Parliament; Office of the Privacy Commissioner (OPC)
**Published:** 2025 (Royal Assent; exact date to be confirmed against NZ Legislation website)
**Effective:** 2026-05-01 (already in effect as of this scan date)
**Primary source:** https://www.legislation.govt.nz (NZ Legislation; link-verified-by-reference) | https://www.privacy.org.nz (OPC)
**Secondary refs:** https://cookiechimp.com/guides/regulations/nz_privacy_act | https://www.recordinglaw.com/world-laws/world-data-privacy-laws/new-zealand-data-privacy-laws/

**What changed:** The Privacy Amendment Act 2025 adds a new IPP 3A to the New Zealand Privacy Act 2020, effective 2026-05-01. IPP 3A requires organisations to inform individuals when their personal information is collected from a third party (rather than directly from the individual). In the context of online tracking, this is relevant where cookies, pixels, or SDKs collect data about a user that is then shared with or received by a third party (e.g., a DSP or analytics vendor). The amendment does not introduce a new consent requirement; New Zealand continues to operate on an opt-out model. However, it strengthens the transparency obligation at the point of third-party data collection.

**ID-PRIVACY impact:** LOW. The amendment primarily affects the notice/disclosure layer rather than the consent mechanics. For ID-PRIVACY, this means that where tenants use the platform to disclose third-party SDKs and vendors collecting NZ-user data, those disclosures should now explicitly state that data was or will be received from a third-party source. The Cookie Classification and Vendor Governance subsystems should ensure vendor disclosures for NZ-active tenants include this notice element. No banner consent-gate change required.

**Action required:** Review NZ jurisdiction privacy notice template; add a disclosure line where third-party data collection is involved, per IPP 3A. Estimated: 1-2 hours of content work, no code change. Recommend in next content sprint.

**Severity:** LOW — notice/transparency change only; no new consent requirement.

**Confidence:** MEDIUM — amendment characterised via multiple secondary sources (CookieChimp, RecordingLaw); effective date of 2026-05-01 reported consistently. Primary NZ Legislation website link-verified-by-reference.

---

## ITEM 5 — Canada Bill C-27 (CPPA) Lapsed; Federal Privacy Reform Indefinitely Deferred (Tier 2: Canada)

**Jurisdiction:** Canada (federal)
**Instrument:** Bill C-27 (Consumer Privacy Protection Act + AIDA) — died on Order Paper
**Issuing body:** Parliament of Canada
**Published:** N/A — bill died; no new law
**Effective:** N/A
**Primary source:** https://www.parl.ca/legisinfo/en/bill/44-1/c-27 (Parliament of Canada)
**Secondary refs:** https://iapp.org/news/a/notes-from-the-iapp-canada-loss-of-bill-c-27-presents-an-opportunity | https://gowlingwlg.com/en/insights-resources/articles/2025/federal-privacy-reform

**What changed:** Bill C-27 (which would have introduced the Consumer Privacy Protection Act replacing PIPEDA) died on the Order Paper when Parliament was prorogued in January 2025; a subsequent federal election in April 2025 further deferred reform. As of this scan, Canada's federal data protection framework remains PIPEDA (2000). No new federal privacy legislation is expected in 2026. Quebec's Law 25 (already in the baseline and in force) remains the most stringent Canadian jurisdiction. The absence of Bill C-27 means there is no federal consent-manager framework, no AI-specific data-protection rule, and no cross-sector consent harmonisation at the federal level in Canada.

**ID-PRIVACY impact:** LOW / Informational. No action required. The current PIPEDA-based and Quebec-Law-25-based consent configurations are correct and complete. Remove C-27 from any forward roadmap items that assumed its passage. Canada continues to warrant monitoring for a re-introduced bill under the new government.

**Action required:** None engineering. Update internal roadmap notes to remove C-27 dependency assumptions.

**Severity:** LOW — informational; no rule change.

**Confidence:** HIGH — Parliament of Canada LEGISinfo confirms bill status; IAPP and Gowling WLG confirm reform deferral.

---

## ITEMS NOT QUALIFYING THIS CYCLE

The following Tier 2 items were reviewed and found to be either already in the baseline, pre-trigger, or out of scope for cookies/consent/CMP:

- **China PIPL (2026):** No new regulation in window; existing PIPL enforcement intensity increase is a watch item, not a trigger event. Already in baseline as Tier 2 item.
- **Singapore PDPA (2026):** NRIC authentication change (effective 2026-12-31) is not cookies/consent-touching. No in-window legislative trigger.
- **Thailand PDPA:** August 2025 PDPC fines were pre-window (>30 days); iris-scan enforcement (Nov 2025) is pre-window and not cookies-touching.
- **UAE PDPL:** Child Digital Safety Law (Federal Decree-Law No. 26/2025) is a watch item; behavioural profiling prohibition for under-18s is cookies-adjacent but requires primary source confirmation before triggering alert. Recommend escalation to Tier 1 next week for primary source check.
- **South Africa POPIA:** No in-window binding guidance or enforcement action on cookies. Steady state.
- **Mexico LFPDPPP (2025 reform):** Effective 2025-03-21 and already in the 30-day dedupe window relative to the baseline. Not a new trigger.
- **New US state laws (IN, KY, RI, MN, MD):** Already in baseline items 6-7; no new in-window trigger.
- **Australia Privacy Act:** Privacy and Other Legislation Amendment Act 2024 (Royal Assent 2024-12-10) is pre-window and already in secondary monitoring. Automated-decision-making provisions (Dec 2026 commencement) are on the watch list but not yet a Tier 2 trigger event this cycle.
- **IAB TCF v2.3:** Deadline (2026-02-28) already passed; in baseline as CRITICAL item 1. No new trigger.

---

*End of weekly LOW digest — Tier 2 scan, 2026-05-09.*
*MEDIUM-severity items from this scan (RW-2026-05-09-T2-01 through T2-03) are being emailed separately.*
