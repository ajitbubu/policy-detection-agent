# Regulation Watch -- Digest Pending
# Items below are LOW or PENDING CONFIRMATION items awaiting the Monday weekly digest email.
# Each entry is prefixed with the scan date it was added.

---

## 2026-05-20 | WATCH: Connecticut SB 4 (2026) -- CTDPA Amendment + Data Broker Law
**Status:** PENDING PRIMARY CONFIRMATION (awaiting governor signature)
**Jurisdiction:** United States -- Connecticut
**Instrument:** Bill -- An Act Concerning Consumer Privacy and Protection (SB 4, 2026 CT General Assembly)
**Passed legislature:** 2026-05-04 (House 141-6); 2026-04-23 (Senate 31-4)
**Transmitted to Governor:** 2026-05-15
**Governor signature:** Not confirmed as of 2026-05-20
**Primary source (legislative):** https://www.cga.ct.gov/asp/CGABillStatus/cgabillstatus.asp?selBillType=Bill&bill_num=sb4
**Secondary refs:** https://www.wiley.law/alert-Major-Changes-to-Connecticut-Consumer-Privacy-Law-Will-Take-Effect-July-1-2026
                  https://captaincompliance.com/education/connecticut-senate-bill-4-delivers-major-data-broker-crackdown-and-ctdpa-amendments-as-privacy-enforcement-accelerates-nationwide/
**What it does (if signed):**
- Amends the Connecticut Data Privacy Act (CTDPA) to BAN outright the sale, sharing,
  transfer, or granting of access to precise geolocation data (joining MD, OR, VA).
  This is stronger than the prior CTDPA opt-in consent requirement -- no commercial
  transfer of precise geolocation data is permitted regardless of consent.
- Establishes a data broker registry and a centralized deletion mechanism (similar
  to California's Delete Act).
- Restricts algorithmic pricing (surveillance pricing) using personal data.
- Redefines facial recognition technology and adds new employment profiling rights.
**Key effective dates (expected if signed):**
- Precise geolocation ban + CTDPA amendments: October 1, 2026
- Data broker registration: January 1, 2027
**ID-PRIVACY relevance:**
- Vendor/SDK Governance: any SDK transmitting precise geolocation for commercial sale
  must be blocked in CT -- this is a BAN, not a consent flow. Even with affirmative
  consent, sale is prohibited. Affects vendors like Foursquare, SafeGraph, X-Mode
  successors. This is a stronger restriction than the FTC Kochava standard (which
  permits sale with consent) -- for CT tenants, sale of geolocation cannot be enabled
  via any consent mechanism.
- Cookie Classification ML: precise geolocation cookies/SDKs need a "CT-geo-ban"
  flag separate from the "sensitive-location consent required" flag from FTC Kochava.
- Geo/Jurisdiction Routing: CT ruleset must block geolocation-sale vendor firing
  entirely, regardless of consent state.
**Action:** Escalate to HIGH alert with full output format upon confirmed governor
signature. Monitor daily through 2026-06-01.
**Confidence:** MEDIUM (legislative facts confirmed; governor signature not yet
confirmed; effective dates from secondary source analysis pending final text).

---

## 2026-05-20 | WATCH: EDPB CEF 2026 -- Coordinated Enforcement on GDPR Transparency
**Status:** LOW -- ongoing enforcement initiative, already launched, no new regulatory instrument published in scan window
**Jurisdiction:** EU/EEA (25 DPAs)
**Instrument:** Coordinated Enforcement Framework action (not new law/guidance -- enforcement initiative)
**Launched:** 2026-03-19 (EDPB announcement)
**Primary source:** https://www.edpb.europa.eu/news/news/2026/cef-2026-edpb-launches-coordinated-enforcement-action-transparency-and-information_en
**What it is:** 25 EEA DPAs sending questionnaires to controllers across private sector
  assessing compliance with GDPR Articles 12, 13, 14 (transparency and information
  obligations). Scope explicitly includes privacy notices, cookie consent flows,
  data-subject communications. Cookie banner language and consent flows are directly
  in scope.
**ID-PRIVACY relevance (advisory):** Any EU/EEA tenant may receive a DPA questionnaire.
  ID-PRIVACY's consent-banner copy, purpose descriptions, and vendor disclosure
  accuracy will be scrutinised. Ensure banner disclosures match actual vendor lists
  and processing purposes. This is not a new rule but an active enforcement signal
  for 2026.
**Action:** No platform change required. Include in next customer advisory as background
  context. Monitor for national DPA questionnaire publication to understand specific
  questions being asked.

---
