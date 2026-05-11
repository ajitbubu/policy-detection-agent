# Weekly LOW Digest — Pending Items

## 2026-05-11 scan additions

### LOW-001 — Alabama Personal Data Protection Act (APDPA) enacted

- **Jurisdiction:** Alabama, USA
- **Instrument:** New law — Alabama HB 351, signed 2026-04-17
- **Issuing body:** Alabama Governor Kay Ivey / Alabama Legislature
- **Published:** 2026-04-17
- **Effective:** 2027-05-01 (T-minus ~355 days)
- **Primary source:** https://alison.legislature.state.al.us/bill-detail?OID=... (SECONDARY — exact Alabama legislature permalink not fetched; corroborated by Hunton, Mayer Brown, WilmerHale, DLA Piper, Troutman)
- **Secondary refs:** https://www.hunton.com/privacy-and-cybersecurity-law-blog/alabama-becomes-21st-state-with-comprehensive-consumer-privacy-law
                    https://www.mayerbrown.com/en/insights/publications/2026/04/alabama-enacts-comprehensive-consumer-data-privacy-law
                    https://www.wilmerhale.com/en/insights/blogs/wilmerhale-privacy-and-cybersecurity-law/20260422-alabama-enacts-nations-twenty-first-state-comprehensive-privacy-law

**Summary for engineering:** Alabama becomes the 21st comprehensive US state
privacy law. Effective May 1, 2027. Thresholds: controllers processing data of
>25,000 Alabama residents OR deriving >25% of revenue from data sales. Standard
US-style framework: opt-out right for targeted advertising/sale; opt-in for
sensitive data (includes precise geolocation, biometric, health, racial/ethnic
origin, religious beliefs, sexual orientation, children's data); no universal
opt-out signal (GPC) recognition requirement (Senate removed that provision);
no private right of action; AG enforcement only.

**ID-PRIVACY impact (low, >180 days):** Add Alabama to jurisdiction routing
table; configure opt-out banner variant; add sensitive-data opt-in gate.
This is additive to the existing US state template — no novel consent
architecture required. Recommend including in the next quarterly US-state
template sweep alongside any remaining 2026/2027 effective-date states.

**Effort estimate:** 2-3 pts (routing rule + privacy-notice text variant)
— no rush; target Q1 2027 implementation sprint.

---

*Digest to be emailed Monday 2026-05-18 and file cleared.*
