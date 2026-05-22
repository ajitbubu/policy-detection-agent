<!-- Weekly LOW-severity digest — generated 2026-05-22 by Tier 2 scan -->
<!-- This file is cleared after the Gmail draft is created and committed. -->
<!-- Items below are queued for the Monday weekly email to asahu@datasafeguard.ai -->

# ID-PRIVACY Weekly Regulation Digest — Week of 2026-05-22
## Tier 2 Global Scan | LOW-Severity Items

Scan window: 2026-05-15 to 2026-05-22 (plus ICO backfill from prior-scan recommendation)
Scan type: Tier 2 weekly
Highest severity: LOW (all items informational / horizon)
Alerts emitted to email/Jira this cycle: 0 new HIGH/CRITICAL/MEDIUM
Items in this digest: 7

---

### DIGEST ITEM 1 — UK ICO Final SAT Guidance (Backfill from prior scan)
Jurisdiction: United Kingdom
Instrument: Regulatory guidance (final)
Issuing body: Information Commissioner's Office (ICO)
Published: 2026-04-29
Effective: Immediately (DUAA analytics/preference exemptions in force since 2026-02-05)
Primary source: https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-the-use-of-storage-and-access-technologies/
Secondary: https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/04/final-storage-and-access-technologies-guidance-published/

Summary: The ICO published its final updated guidance on storage and access technologies (cookies, pixels, device fingerprinting, SDKs), replacing the prior cookies guidance. The Data (Use and Access) Act 2025 introduced five new PECR exemptions effective 2026-02-05: (i) transmission of a communication; (ii) service explicitly requested by the user; (iii) collecting statistical information solely for improving the service (analytics exemption — strictly purpose-limited; does NOT apply if analytics feeds ad targeting); (iv) adapting appearance to user preference; (v) identifying users requiring emergency assistance. The guidance adds two new sub-chapters: "what does a simple means of objecting mean?" and "can we use the same SAT for multiple purposes?" Non-exempt SATs still require prior informed consent. Maximum PECR penalty now £17.5m or 4% of annual worldwide turnover (aligned with UK GDPR).

ID-PRIVACY subsystems affected:
- Consent Banner: Verify that UK-gated banners correctly omit consent prompts for SATs falling within the five exemptions; ensure analytics-only SATs with no ad-targeting link are correctly classified as exempt.
- Cookie Classification ML: Analytics cookies that also feed ad targeting must NOT be reclassified as exempt; classifier needs a "dual-purpose" flag.
- Geo/Jurisdiction Routing: UK ruleset update required to reflect new exemption categories.
- Tenant Config: UK clients may need new toggle to indicate whether their analytics pipeline is ad-targeting-linked (determines exemption eligibility).
- Audit/Logging: "Simple means of objecting" requirement must be evidenced in consent logs for non-exempt SATs.

Recommended actions:
  Engineering: Review UK jurisdiction ruleset in geo-routing layer; add analytics-dual-purpose flag to cookie classifier — est. 3 pts — target before 2026-06-30.
  Product/Legal: Update UK-specific consent banner templates to reflect new exemption language; update customer-facing documentation — target 2026-06-30.
  Customer notice: YES — customers with UK operations should be notified that analytics cookies may now qualify for exemption, conditional on purpose-scope review.

Confidence: HIGH (ICO primary URL confirmed via search indexing; WebFetch returned 403 on ico.org.uk — standard standing caveat; substantive content corroborated across 5+ independent secondary sources)

---

### DIGEST ITEM 2 — EDPB Updated Pay-or-Consent Guidelines (May 2026)
Jurisdiction: EU / EEA
Instrument: EDPB guidelines (updated)
Issuing body: European Data Protection Board (EDPB)
Published: 2026-05 (exact date PENDING PRIMARY CONFIRMATION — not yet independently verified on edpb.europa.eu)
Effective: Immediately upon publication (non-binding guidance; member-state DPAs expected to apply)
Primary source: https://www.edpb.europa.eu/our-work-tools/our-documents/topic/consent_en (SECONDARY — pending primary document URL)
Secondary: https://www.auditsocials.com/blog/edpb-pay-or-consent-cookie-walls-may-2026-updated-guidance-consent-validity-advertiser-tracking-workflow

Summary: The EDPB reportedly published refreshed pay-or-consent guidance in May 2026, extending the scope of Opinion 08/2024 beyond large online platforms to all services offering cookie-wall or pay-for-ad-free configurations. The key update: binary pay-or-consent (two choices: accept tracking or pay) is invalid in most consumer-facing configurations because the choice is not freely given. Multi-tier configurations offering at least three meaningful alternatives (accept tracking / pay for ad-free / accept tracking-light alternative with reduced personalisation) can produce valid consent under specific design criteria. The guidance applies four cumulative consent-validity criteria, and failure on any single criterion renders consent invalid. NOTE: This item requires primary-source verification on edpb.europa.eu before escalation. Recommend legal review within 72 hours of primary publication.

ID-PRIVACY subsystems affected:
- Consent Banner: Pay-or-consent banner templates must support three-tier choice architecture for EU deployments.
- Tenant Config: New toggle for "consent-or-pay" tier configuration; price-reasonableness check workflow.
- Vendor/SDK Governance: Third-party vendors integrated via TCF may be affected if their consent string relies on binary wall patterns.

Recommended actions:
  Legal: Monitor edpb.europa.eu for primary document publication; confirm scope and effective date — within 72 hours of this digest.
  Engineering: Audit EU banner templates for binary pay-or-consent patterns; prepare three-tier config option — est. 5 pts — target before 2026-07-31.
  Product: Update guidance documentation for EU customers using pay-or-consent configurations — target 2026-07-31.
  Customer notice: CONDITIONAL — only customers using pay-or-consent / cookie-wall patterns; after primary source confirmation.

Confidence: MEDIUM — PENDING PRIMARY CONFIRMATION (reported by multiple secondary sources; primary edpb.europa.eu URL not independently verified in this scan run)

---

### DIGEST ITEM 3 — South Korea PIPA Amendment (Enacted 2026-03-10, Effective 2026-09-11)
Jurisdiction: South Korea
Instrument: Legislative amendment
Issuing body: National Assembly of the Republic of Korea / Personal Information Protection Commission (PIPC)
Published / Enacted: 2026-03-10
Effective: 2026-09-11 (T-minus 112 days from 2026-05-22)
Primary source: https://pipc.go.kr/eng/ (SECONDARY — Korean Official Gazette primary citation pending; PIPC English site)
Secondary: https://iapp.org/news/a/south-korea-overhauls-pipa-and-ties-fines-to-ceo-accountability | https://www.consentstack.io/regulations/kr-pipa

Summary: South Korea's National Assembly amended the Personal Information Protection Act on 2026-03-10. Most provisions take effect 2026-09-11. Key changes: (1) Maximum administrative fine raised from 3% to 10% of total annual revenue for egregious violations (repeated misconduct within 3 years; incidents affecting 10 million or more individuals; failure to comply with a corrective order). (2) The CEO / business owner is now the designated "ultimate person responsible" for personal data protection — creating boardroom-level statutory accountability. (3) Explicit opt-in consent is required when cookie data is combinable with other data to identify individuals; privacy policies must disclose automatic data collection devices (cookies, pixels, SDKs). (4) ISMS-P certification (privacy management system) transitions from voluntary to mandatory for qualifying entities; enforcement commences 2027-07-01. This is primarily a governance and enforcement-escalation amendment; the underlying cookie consent opt-in rule is not new, but the penalty ceiling amplifies the risk profile.

ID-PRIVACY subsystems affected:
- Geo/Jurisdiction Routing: KR ruleset penalty-risk metadata should be updated to reflect 10% revenue ceiling.
- Cookie Classification ML: Ensure classifier flags cookies that are individually non-identifying but combinable (pseudonymous identifiers combined with session data) — KR requires opt-in for these.
- Audit/Logging: Korean-jurisdiction consent logs must be capable of demonstrating opt-in prior to setting cookies.
- Tenant Config: Documentation for KR customers should flag CEO accountability requirement.

Recommended actions:
  Engineering: Update KR jurisdiction metadata (penalty ceiling); review combinability flag in classifier for KR — est. 2 pts — by 2026-08-01.
  Product/Legal: Brief KR-operating customers on CEO accountability provision and updated fine ceiling — by 2026-08-15.
  Customer notice: YES — customers with Korean operations; by 2026-08-01.

Confidence: HIGH (amendment date and effective date corroborated by IAPP and PIPC-citing secondary sources; primary Korean gazette URL not retrieved but facts consistent across 4+ sources)

---

### DIGEST ITEM 4 — Australia OAIC Children's Online Privacy Code (Exposure Draft Consultation)
Jurisdiction: Australia
Instrument: Exposure draft / consultation
Issuing body: Office of the Australian Information Commissioner (OAIC)
Published: 2026-03-31
Consultation closes: 2026-06-05 (T-minus 14 days)
Expected registration: 2026-12-10
Primary source: https://www.oaic.gov.au/privacy/privacy-registers/privacy-codes/childrens-online-privacy-code
Secondary: https://www.bakermckenzie.com/en/insight/publications/2026/05/australia-childrens-online-privacy-code-exposure-draft | https://privacymatters.dlapiper.com/2026/04/australia-exposure-draft-of-childrens-online-privacy-code-signals-tougher-standards/

Summary: The OAIC published an exposure draft of the Children's Online Privacy Code under the Privacy Act, with consultation open until 2026-06-05. The draft Code requires agencies and organisations to: consider children's best interests before collecting, using, or disclosing personal information; obtain consent before using children's personal information for targeted advertising; and enable children to request deletion of their personal information. This is a consultation draft, not yet in force. If adopted on schedule (2026-12-10), it would impose opt-in consent requirements for any behavioural-advertising or profiling cookies/trackers applied to users where a service is directed to or likely used by minors. This also aligns with the separately commencing Privacy Act automated decision-making disclosure requirement (2026-12-10).

ID-PRIVACY subsystems affected:
- Consent Banner: AU jurisdiction banners may require age-gate layer or separate children's consent flow for behavioural advertising cookies.
- Cookie Classification ML: "Targeted advertising" and "profiling" cookie categories must be flaggable for AU child-audience context.
- Vendor/SDK Governance: Third-party ad tech vendors deployed on AU child-directed sites will need to be gated pending child-safe consent.
- Tenant Config: AU customers may require a "child-directed service" toggle.

Recommended actions:
  Legal: Submit or monitor consultation submissions; assess draft Code applicability to CMP customers with AU child-directed services — by 2026-06-05.
  Engineering: Begin scoping age-gate / child-consent flow for AU jurisdiction — est. 8 pts — target design complete by 2026-09-30 ahead of 2026-12-10 registration.
  Customer notice: NO at this stage (still a draft); YES on Code registration (expected 2026-12-10).

Confidence: HIGH (OAIC primary URL confirmed; consultation close date and registration target corroborated by OAIC and multiple law firm secondary sources)

---

### DIGEST ITEM 5 — India DPDP Consent Manager Framework (T-175 Days Horizon)
Jurisdiction: India
Instrument: Implementing rules under DPDP Act 2023 (DPDP Rules 2025)
Issuing body: Ministry of Electronics and Information Technology (MeitY)
Published: 2025-11-14 (gazette notification)
Phase 2 effective (consent managers): 2026-11-13 (T-minus 175 days from 2026-05-22)
Primary source: https://www.meity.gov.in/ (SECONDARY — official gazette at egazette.gov.in; MeitY primary URL historically returns 403)
Secondary: https://www.india-briefing.com/news/india-dpdp-compliance-timeline-enforcement-2026-27-44740.html/ | https://www.fisherphillips.com/en/insights/insights/indias-new-data-privacy-rules-are-here

Summary: Horizon reminder. The DPDP Rules 2025 (notified 2025-11-14) activate the Consent Manager registration framework on 2026-11-13. From that date, only DPDP-registered "Consent Managers" (locally incorporated entities, minimum INR 20 million net worth, independent certification for interoperability) can serve as intermediaries between Data Principals and Data Fiduciaries for managing consent across digital services. This directly affects how ID-PRIVACY operates in the Indian market: the platform must either register as a Consent Manager or integrate with a registered Consent Manager to route Indian user consent signals. Between June and August 2026, MeitY is expected to operationalise the registration process. No additional gazette notification has been issued in the 2026-05-15 to 2026-05-22 scan window; this is a standing horizon item.

ID-PRIVACY subsystems affected:
- Consent Signals (GPC/TCF/GPP): Must align with Consent Manager interoperability protocol once specifications are published by MeitY.
- Vendor/SDK Governance: CMP must integrate with registered Consent Manager intermediary layer for IN-jurisdiction users.
- Geo/Jurisdiction Routing: IN ruleset must be updated with consent manager gating logic.
- Tenant Config: IN customers need guidance on whether to self-register as Consent Manager or rely on ID-PRIVACY registration.
- Cross-border Transfer: Separate MeitY notification on cross-border restrictions still pending; watch list.

Recommended actions:
  Engineering: Begin design for Consent Manager integration/registration module for IN jurisdiction — est. 13 pts — design by 2026-08-31, build by 2026-10-31.
  Product/Legal: Monitor MeitY registration portal launch (expected June–August 2026); assess whether DataSafeguard should register as Consent Manager — decision needed by 2026-07-31.
  Customer notice: YES — IN-market customers should be notified of Consent Manager framework timeline — by 2026-07-01.

Confidence: HIGH (gazette notification date and Consent Manager effective date corroborated by multiple primary-tier secondary sources citing official gazette; MeitY primary URL historically blocked)

---

### DIGEST ITEM 6 — EU Digital Omnibus: Cookie Reform Legislative Progress
Jurisdiction: European Union
Instrument: Legislative proposal (not yet in force)
Issuing body: European Commission (proposal); co-decided by European Parliament and Council of the EU
Published: 2025-11-19 (Commission proposal)
Earliest in force: 2027 (optimistic); more likely 2028
Primary source: https://digital-strategy.ec.europa.eu/en/faqs/digital-package
Secondary: https://www.taylorwessing.com/en/global-data-hub/2026/the-digital-omnibus-proposal/gdh---the-digital-omnibus---cookies | https://datamatters.sidley.com/2025/12/09/eu-digital-omnibus-the-european-commission-proposes-important-changes-to-the-eus-digital-rulebook/

Summary: Horizon / watch item. The EU Digital Omnibus proposal (Commission proposal 2025-11-19) proposes to embed cookie/tracking consent rules directly into the GDPR via new Articles 88a and 88b, effectively replacing the ePrivacy Directive for personal-data-processing cookies. Key proposed changes: (1) Consent must not be re-requested for at least six months after a user declines. (2) Single-click reject-all button required on cookie banners. (3) Browser signals (GPC and equivalents) must be respected and treated as valid opt-out signals. (4) Analytics cookies used solely for the operator's own site metrics (not cross-site) would be exempt from consent. (5) GDPR fines (up to 4% global turnover) would apply to cookie violations. The proposal is in the ordinary legislative procedure; negotiations in the European Parliament and Council are expected to run through mid-to-late 2026 at earliest, with adoption no earlier than end-2026 and implementation likely 2027–2028. No material legislative progress occurred in the 2026-05-15 to 2026-05-22 scan window.

ID-PRIVACY subsystems affected (if enacted as drafted):
- Consent Banner: Reject-all on layer 1; 6-month re-consent lockout after rejection.
- Consent Signals: GPC mandatory honoring; browser-signal handling becomes a legal obligation.
- Cookie Classification ML: Analytics-only exemption (no cross-site) may require a separate classification track.
- Geo/Jurisdiction Routing: Current ePrivacy-based EU ruleset will need migration to GDPR-based ruleset.

Recommended actions:
  Legal: Monitor legislative progress; flag to engineering when Council and Parliament positions are adopted (likely Q3–Q4 2026).
  Engineering: No code changes required yet; log as watch item. Begin gap analysis against current EU banner config — est. 1 pt — by 2026-08-31.
  Customer notice: NO at this stage.

Confidence: HIGH on proposal content; LOW on timeline (legislative negotiations are unpredictable)

---

### DIGEST ITEM 7 — Brazil ANPD Independence + 2026-2027 Enforcement Priorities
Jurisdiction: Brazil
Instrument: Law 15.352/2026 (ANPD independence); Resolution CD/ANPD No. 30 (enforcement priorities)
Issuing body: Brazilian National Congress (Law); ANPD (Resolution)
Law published: 2026-02
Resolution published: 2025-12-24
Effective: Immediately
Primary source: https://www.gov.br/anpd/pt-br (ANPD official site; SECONDARY — specific gazette URLs not retrieved)
Secondary: https://cadeproject.org/updates/brazils-data-protection-authority-sets-enforcement-priorities-for-2026-2027/ | https://www.trenchrossi.com/en/legal-alerts/anpd-publishes-map-of-priority-issues-2026-2027-biennium-and-update-of-the-regulatory-agenda-2025-2026-biennium/

Summary: Two related but distinct developments. First, Law 15.352/2026 (February 2026) formally grants the ANPD full regulatory independence (functional, technical, decision-making, administrative, and financial autonomy), with 200 new specialist positions being filled — materially increasing enforcement capacity. Second, Resolution CD/ANPD No. 30 (December 2025) sets the enforcement priority map for 2026–2027, with four pillars: data subject rights (with special attention to sensitive data use in advertising); protection of children and adolescents (including age verification and blocking inappropriate content); public authority compliance; and AI and emerging technologies. Cookie enforcement per se is not listed as a 2026–2027 priority; the ANPD's 2022 cookie guide remains the operative guidance. However, the advertising-data and children's-data priorities indirectly implicate cookie and tracking practices. No new cookie-specific resolution was issued in the scan window.

ID-PRIVACY subsystems affected:
- Geo/Jurisdiction Routing: BR enforcement-risk metadata should be updated to reflect ANPD's increased independence and capacity.
- Vendor/SDK Governance: Ad-tech and children's-data vendors in BR deployments warrant closer scrutiny given enforcement priorities.

Recommended actions:
  Product/Legal: Brief BR-market customers on ANPD independence and enforcement priorities; note elevated enforcement risk for ad-tech and children's data — by 2026-07-01.
  Engineering: No code changes required at this time.
  Customer notice: INFORMATIONAL — for customers with BR operations using behavioural advertising or children's-data processing.

Confidence: HIGH on ANPD independence law and resolution; MEDIUM on primary gazette URLs (confirmed via multiple law-firm secondary sources; ANPD official site not WebFetch-accessible in this run)
