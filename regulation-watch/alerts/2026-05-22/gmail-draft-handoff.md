<!-- ORCHESTRATOR HANDOFF FILE — DO NOT COMMIT AFTER USE -->
<!-- Created by: privacy-regulation-watcher subagent, 2026-05-22 -->
<!-- Action required: orchestrator must create Gmail draft from this file, -->
<!-- then post Jira comment to IDP-11488, then open GitHub draft PR. -->
<!-- After Gmail draft is created, update alerts-emitted.json emailDraftId field. -->

TO: asahu@datasafeguard.ai
SUBJECT: ID-PRIVACY Weekly Regulation Digest — Tier 2 Global Scan — Week of 2026-05-22

---BODY START---

ID-PRIVACY WEEKLY REGULATION DIGEST — TIER 2 GLOBAL SCAN
Week of 2026-05-22 | Privacy Regulation Intelligence Agent
Recipient: Ajit Sahu, Director of Engineering

Scan window: 2026-05-15 to 2026-05-22 (plus ICO backfill from prior-scan recommendation)
Highest severity this week: LOW (all items informational / horizon)
CRITICAL/HIGH/MEDIUM alerts this week: 0
LOW items in this digest: 7
Deduplication: No overlap with prior alert RW-2026-05-09-01 (FTC v. Kochava)

Note: LOW-severity items are informational. No immediate engineering action is
required unless noted. Items marked PENDING PRIMARY CONFIRMATION require legal
review of the primary source before acting.

═══════════════════════════════════════════════════════════════════════
ITEM 1 — UK ICO FINAL STORAGE AND ACCESS TECHNOLOGIES (SAT) GUIDANCE
[BACKFILL — published 2026-04-29; recommended from prior scan]
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       United Kingdom
Instrument:         Regulatory guidance (final)
Issuing body:       Information Commissioner's Office (ICO)
Published:          2026-04-29
Effective:          Immediately (DUAA analytics/preference exemptions in
                    force since 2026-02-05)
Primary source:     https://ico.org.uk/for-organisations/direct-marketing-and-privacy-and-electronic-communications/guidance-on-the-use-of-storage-and-access-technologies/
Secondary:          https://ico.org.uk/about-the-ico/media-centre/news-and-blogs/2026/04/final-storage-and-access-technologies-guidance-published/

WHAT CHANGED
The ICO finalised its updated guidance on storage and access technologies
(cookies, pixels, device fingerprinting, SDKs), replacing the previous
cookies guidance. The Data (Use and Access) Act 2025 introduced five new
PECR exemptions from the consent requirement, effective 2026-02-05:
(i) transmission of a communication; (ii) service explicitly requested by
the user; (iii) collecting statistical information solely for improving the
service — strictly purpose-limited, does NOT apply if analytics also feeds
ad targeting; (iv) adapting appearance to user preference; (v) identifying
users requiring emergency assistance. The guidance adds two new sub-chapters:
"what does a simple means of objecting mean?" and "can we use the same SAT
for multiple purposes?" Non-exempt SATs still require prior informed consent.
Maximum PECR penalty is now £17.5m or 4% of annual worldwide turnover.

ID-PRIVACY SUBSYSTEMS AFFECTED
  Consent Banner:          UK-gated banners should omit consent prompts for
                           SATs falling within the five exemptions.
  Cookie Classification ML: Analytics cookies that ALSO feed ad targeting
                           must NOT be reclassified as exempt; dual-purpose
                           flag needed.
  Geo/Jurisdiction Routing: UK ruleset update required for new exemptions.
  Tenant Config:           UK clients may need toggle to indicate whether
                           analytics pipeline is ad-targeting-linked.
  Audit/Logging:           "Simple means of objecting" must be evidenced
                           in consent logs for non-exempt SATs.

RECOMMENDED ACTIONS
  Engineering (Abhishek's track):
    1. Update UK jurisdiction ruleset in geo-routing layer — est. 2 pts
       — by 2026-06-30
    2. Add analytics-dual-purpose flag to cookie classifier for UK
       — est. 1 pt — by 2026-06-30
  Product/Legal:
    1. Update UK-specific banner templates and customer documentation
       — by 2026-06-30
    2. Notify UK-operating customers of analytics exemption (conditional
       on purpose-scope review) — by 2026-07-15
  Customer notice: YES

Confidence: HIGH (ICO primary URL confirmed via search indexing; WebFetch
on ico.org.uk returned 403 — standing caveat; content corroborated across
5+ secondary sources)

═══════════════════════════════════════════════════════════════════════
ITEM 2 — EDPB UPDATED PAY-OR-CONSENT GUIDELINES (MAY 2026)
[PENDING PRIMARY CONFIRMATION — verify on edpb.europa.eu before acting]
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       European Union / EEA
Instrument:         EDPB guidelines (updated)
Issuing body:       European Data Protection Board (EDPB)
Published:          2026-05 (exact date PENDING PRIMARY CONFIRMATION)
Effective:          Immediately upon publication (non-binding; DPAs expected
                    to apply)
Primary source:     https://www.edpb.europa.eu/our-work-tools/our-documents/topic/consent_en
                    (verify for updated document)
Secondary:          https://www.auditsocials.com/blog/edpb-pay-or-consent-cookie-walls-may-2026-updated-guidance-consent-validity-advertiser-tracking-workflow

WHAT CHANGED (PENDING CONFIRMATION)
The EDPB reportedly published refreshed pay-or-consent guidelines in May
2026, extending the scope of Opinion 08/2024 beyond large online platforms
to all services offering cookie-wall or pay-for-ad-free configurations. Key
update: binary pay-or-consent (two choices: accept tracking or pay) is
invalid under GDPR Art. 4(11) and Art. 7 in most consumer-facing
configurations. Multi-tier configurations offering at least three meaningful
alternatives (accept tracking / pay for ad-free / tracking-light alternative
with reduced personalisation) can produce valid consent under specific design
criteria. Four cumulative consent-validity criteria apply; failure on any
one renders consent invalid.

ID-PRIVACY SUBSYSTEMS AFFECTED (if confirmed)
  Consent Banner:       Pay-or-consent templates must support three-tier
                        choice architecture for EU deployments.
  Tenant Config:        New toggle for three-tier pay-or-consent config.
  Vendor Governance:    Ad-tech vendors using binary cookie-wall patterns
                        may need to be re-gated.

RECOMMENDED ACTIONS
  Legal: Verify primary document on edpb.europa.eu — within 72 hours.
  Engineering: Audit EU banner templates for binary pay-or-consent patterns;
    prepare three-tier config option — est. 5 pts — target 2026-07-31
    (after primary confirmation)
  Customer notice: CONDITIONAL — only customers using pay-or-consent /
    cookie-wall patterns; after primary source confirmation only.

Confidence: MEDIUM — PENDING PRIMARY CONFIRMATION

═══════════════════════════════════════════════════════════════════════
ITEM 3 — SOUTH KOREA PIPA AMENDMENT
Enacted 2026-03-10 | Effective 2026-09-11 | T-112 days
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       South Korea
Instrument:         Legislative amendment to PIPA
Issuing body:       National Assembly / Personal Information Protection
                    Commission (PIPC)
Enacted:            2026-03-10
Effective:          2026-09-11 (T-minus 112 days)
Primary source:     https://pipc.go.kr/eng/
Secondary:          https://iapp.org/news/a/south-korea-overhauls-pipa-and-ties-fines-to-ceo-accountability

WHAT CHANGED
(1) Maximum administrative fine raised from 3% to 10% of total annual
revenue for egregious violations: repeated misconduct within 3 years;
incidents affecting 10 million or more individuals; or failure to comply
with a PIPC corrective order. (2) CEO / business owner designated as
"ultimate person responsible" for personal data protection — boardroom-level
statutory accountability. (3) Explicit opt-in consent required when cookie
data is combinable with other data to identify individuals; privacy policies
must disclose automatic data collection devices (cookies, pixels, SDKs).
(4) ISMS-P certification transitions from voluntary to mandatory for
qualifying entities (enforcement from 2027-07-01).

ID-PRIVACY SUBSYSTEMS AFFECTED
  Geo/Jurisdiction Routing: KR penalty-risk metadata update needed.
  Cookie Classification ML: Combinability flag for KR needed.
  Audit/Logging:            KR consent logs must evidence opt-in prior to
                            cookie-setting.

RECOMMENDED ACTIONS
  Engineering (Abhishek's track):
    1. Update KR jurisdiction metadata (10% penalty ceiling) — est. 1 pt
       — by 2026-08-01
    2. Review combinability flag in cookie classifier for KR — est. 2 pts
       — by 2026-08-01
  Product/Legal:
    1. Brief KR-operating customers on CEO accountability + fine ceiling
       — by 2026-08-15
  Customer notice: YES — for customers with Korean operations

Confidence: HIGH

═══════════════════════════════════════════════════════════════════════
ITEM 4 — AUSTRALIA OAIC CHILDREN'S ONLINE PRIVACY CODE (EXPOSURE DRAFT)
Consultation closes 2026-06-05 — 14 days remaining
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       Australia
Instrument:         Exposure draft / public consultation (not yet in force)
Issuing body:       Office of the Australian Information Commissioner (OAIC)
Published:          2026-03-31
Consultation closes: 2026-06-05 (14 days remaining)
Expected Code registration: 2026-12-10
Primary source:     https://www.oaic.gov.au/privacy/privacy-registers/privacy-codes/childrens-online-privacy-code
Secondary:          https://www.bakermckenzie.com/en/insight/publications/2026/05/australia-childrens-online-privacy-code-exposure-draft

WHAT CHANGED
The OAIC published an exposure draft of the Children's Online Privacy Code
under the Privacy Act. The draft Code requires: considering children's best
interests before collecting, using, or disclosing personal information;
obtaining consent before using children's personal information for targeted
advertising; and enabling children to request deletion of their personal
information. If adopted on schedule (2026-12-10), opt-in consent would be
required for behavioural-advertising or profiling cookies/trackers on
services directed to or likely used by minors in Australia.

ID-PRIVACY SUBSYSTEMS AFFECTED
  Consent Banner:      AU banners may require age-gate / children's consent
                       flow for behavioural advertising.
  Cookie Classification: "Targeted advertising" and "profiling" categories
                       must be flaggable for AU child-audience context.
  Vendor Governance:   Ad-tech vendors on AU child-directed sites need
                       gating pending child-safe consent.
  Tenant Config:       "Child-directed service" toggle needed for AU.

RECOMMENDED ACTIONS
  Legal: Monitor or submit to consultation — closes 2026-06-05.
  Engineering: Scope age-gate / child-consent flow for AU — est. 8 pts
    — design by 2026-09-30; build by 2026-11-30.
  Customer notice: NO at this stage; YES on Code registration (2026-12-10).

Confidence: HIGH

═══════════════════════════════════════════════════════════════════════
ITEM 5 — INDIA DPDP CONSENT MANAGER FRAMEWORK (T-175 DAYS HORIZON)
Phase 2 effective 2026-11-13
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       India
Instrument:         DPDP Rules 2025 — Phase 2 activation
Issuing body:       Ministry of Electronics and Information Technology (MeitY)
Rules notified:     2025-11-14
Phase 2 effective:  2026-11-13 (T-minus 175 days)
Primary source:     https://www.meity.gov.in/
Secondary:          https://www.india-briefing.com/news/india-dpdp-compliance-timeline-enforcement-2026-27-44740.html/

WHAT CHANGED (HORIZON REMINDER)
The DPDP Rules 2025 activate the Consent Manager registration framework on
2026-11-13. From that date, only DPDP-registered Consent Managers (locally
incorporated entities, minimum INR 20 million net worth, independent
interoperability certification) can serve as intermediaries for managing
consent across digital services. MeitY is expected to operationalise the
registration portal between June and August 2026. This directly affects how
ID-PRIVACY operates in the Indian market: the platform must either register
as a Consent Manager or integrate with a registered Consent Manager.

ID-PRIVACY SUBSYSTEMS AFFECTED
  Consent Signals:          Must align with Consent Manager interoperability
                            protocol once MeitY publishes specs.
  Vendor/SDK Governance:    CMP must integrate with or serve as registered
                            Consent Manager for IN-jurisdiction users.
  Geo/Jurisdiction Routing: IN ruleset needs consent manager gating logic.
  Tenant Config:            IN customers need guidance on self-registration
                            vs. reliance on DataSafeguard registration.

RECOMMENDED ACTIONS
  Engineering (Abhishek's track):
    1. Begin design for Consent Manager integration/registration module
       — est. 13 pts — design by 2026-08-31; build by 2026-10-31
  Product/Legal:
    1. Monitor MeitY registration portal launch (June–August 2026)
    2. Assess whether DataSafeguard should self-register as Consent Manager
       — decision needed by 2026-07-31
    3. Brief IN-market customers — by 2026-07-01
  Customer notice: YES — for customers with Indian operations — by 2026-07-01

Confidence: HIGH

═══════════════════════════════════════════════════════════════════════
ITEM 6 — EU DIGITAL OMNIBUS: COOKIE REFORM LEGISLATIVE PROGRESS (WATCH)
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       European Union
Instrument:         Legislative proposal (not yet in force)
Issuing body:       European Commission (proposal); EP + Council (co-decision)
Commission proposal: 2025-11-19
Earliest in force:  2027 (optimistic)
Primary source:     https://digital-strategy.ec.europa.eu/en/faqs/digital-package
Secondary:          https://www.taylorwessing.com/en/global-data-hub/2026/the-digital-omnibus-proposal/gdh---the-digital-omnibus---cookies

WHAT IS PROPOSED (WATCH ONLY)
The Digital Omnibus proposes to embed cookie/tracking consent rules into the
GDPR via new Articles 88a and 88b, replacing the ePrivacy Directive for
personal-data-processing cookies. Key proposed changes: (1) Six-month
minimum gap required after a user declines before re-requesting consent.
(2) Single-click reject-all button required on cookie banners. (3) Browser
signals (GPC and equivalents) must be respected as valid opt-out signals.
(4) Analytics cookies used solely for own-site metrics (not cross-site)
would be exempt. (5) GDPR fines (up to 4% global turnover) would apply to
cookie violations. No material legislative progress in scan window.

RECOMMENDED ACTIONS
  Legal: Monitor EP and Council positions (expected Q3-Q4 2026); escalate
    to HIGH when first-reading position is adopted.
  Engineering: No code changes yet. Log as watch item; begin gap analysis
    against current EU banner config — est. 1 pt — by 2026-08-31.
  Customer notice: NO at this stage.

Confidence: HIGH on proposal content; LOW on timeline.

═══════════════════════════════════════════════════════════════════════
ITEM 7 — BRAZIL ANPD INDEPENDENCE + 2026-2027 ENFORCEMENT PRIORITIES
═══════════════════════════════════════════════════════════════════════

Jurisdiction:       Brazil
Instrument:         Law 15.352/2026 (ANPD independence);
                    Resolution CD/ANPD No. 30 (enforcement priorities)
Issuing body:       Brazilian National Congress (Law); ANPD (Resolution)
Law published:      2026-02
Resolution published: 2025-12-24
Effective:          Immediately
Primary source:     https://www.gov.br/anpd/pt-br
Secondary:          https://cadeproject.org/updates/brazils-data-protection-authority-sets-enforcement-priorities-for-2026-2027/
                    https://www.trenchrossi.com/en/legal-alerts/anpd-publishes-map-of-priority-issues-2026-2027-biennium-and-update-of-the-regulatory-agenda-2025-2026-biennium/

WHAT CHANGED
Two related developments. Law 15.352/2026 grants the ANPD full regulatory
independence with 200 new specialist positions, materially increasing
enforcement capacity. Resolution CD/ANPD No. 30 sets enforcement priorities
for 2026-2027 around four pillars: data subject rights (sensitive data use
in advertising); protection of children and adolescents (age verification,
blocking inappropriate content); public authority compliance; and AI and
emerging technologies. Cookie enforcement is not a listed priority; however,
the advertising-data and children's-data pillars indirectly implicate
behavioural tracking and targeting cookies.

ID-PRIVACY SUBSYSTEMS AFFECTED
  Geo/Jurisdiction Routing: BR enforcement-risk metadata should reflect
                            ANPD's increased independence and capacity.
  Vendor/SDK Governance:    Ad-tech and children's-data vendors in BR
                            deployments warrant closer scrutiny.

RECOMMENDED ACTIONS
  Product/Legal:
    1. Brief BR-market customers on ANPD independence and enforcement
       priorities — by 2026-07-01
  Engineering: No code changes required at this time.
  Customer notice: INFORMATIONAL — for customers with BR operations using
    behavioural advertising or children's-data processing.

Confidence: HIGH on law and resolution; MEDIUM on primary gazette URLs.

═══════════════════════════════════════════════════════════════════════
SCAN METADATA
═══════════════════════════════════════════════════════════════════════

Scan date:                2026-05-22
Scan type:                Tier 2 weekly
Scan window:              2026-05-15 to 2026-05-22
Items in digest:          7
Highest severity:         LOW
New CRITICAL/HIGH alerts: 0
New MEDIUM alerts:        0
Dedup against:            RW-2026-05-09-01 (FTC v. Kochava, HIGH, 2026-05-09)
Scan artefact:            regulation-watch/alerts/2026-05-22/tier2-weekly-scan-2026-05-22.json
Git branch:               claude/regwatch-tier2-2026-05-22

Sources consulted: PIPL/CAC (China), PDPC (Singapore), PDPA (Thailand),
OAIC (Australia), OPC (Canada), PIPC (South Korea), APPI (Japan), ANPD
(Brazil), MeitY/DPDP (India), ICO (UK), EDPB (EU), European Commission
(Digital Omnibus), IAB Europe/TCF, UAE/KSA PDPL, POPIA (South Africa),
NDPA (Nigeria)

WebFetch standing caveat: ico.org.uk, edpb.europa.eu, meity.gov.in, and
gov.br/anpd returned HTTP 403 in this run. All items above are corroborated
across multiple independent secondary sources. Legal counsel should verify
primary source URLs before any externally-binding action.

Next scheduled scans:
  Tier 1 daily:   2026-05-25 (Monday) 08:00 ET
  Tier 2 weekly:  2026-05-29 (Monday) 08:00 ET
  Tier 3 monthly: 2026-06-01 08:00 ET

--
Privacy Regulation Intelligence Agent | ID-PRIVACY(R) Universal Consent Management
DataSafeguard | Monitoring configuration confirmed by Ajit Sahu, 2026-05-09

---BODY END---

JIRA COMMENT (post to IDP-11488):
Weekly Tier 2 Regulation Scan — 2026-05-22. 0 CRITICAL/HIGH/MEDIUM alerts.
7 LOW items in weekly digest (Gmail draft created to asahu@datasafeguard.ai).
Items: (1) UK ICO SAT guidance backfill; (2) EDPB pay-or-consent update
PENDING PRIMARY CONFIRM; (3) KR PIPA amendment eff. 2026-09-11 (T-112d);
(4) AU OAIC children's privacy code consultation closes 2026-06-05 (14d);
(5) IN DPDP consent manager T-175d horizon; (6) EU Digital Omnibus watch;
(7) BR ANPD independence + enforcement priorities.
Action items: (a) Legal: verify EDPB primary URL within 72h; (b) Legal:
AU consultation closes 2026-06-05; (c) Product: IN Consent Manager
registration decision by 2026-07-31.
Scan artefact: regulation-watch/alerts/2026-05-22/tier2-weekly-scan-2026-05-22.json
Branch: claude/regwatch-tier2-2026-05-22

GITHUB PR (create draft PR):
  Repo: ajitbubu/policy-detection-agent
  Head: claude/regwatch-tier2-2026-05-22
  Base: claude/friendly-meitner-8K2iy (or main)
  Title: [RegWatch] Weekly Tier 2 scan 2026-05-22 — 7 LOW-severity digest items
  Draft: true
