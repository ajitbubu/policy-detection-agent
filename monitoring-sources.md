# Proposed Monitoring Source List

**Prepared by:** Privacy Regulation Intelligence Agent (initial activation)
**For:** Ajit, Director of Engineering, DataSafeguard
**Date:** 2026-05-09

This list operationalises the "REGULATORY SCOPE" and "AUTHORITATIVE SOURCES" sections of the operating prompt. Sources are tiered by impact and grouped per the prompt's tiering. Cadence reflects how often I propose to scan; alert thresholds are independent (any qualifying change becomes an alert, irrespective of cadence).

URLs were surfaced via web search against the official domains. WebFetch was blocked (HTTP 403) for many of the official domains in this run, so URLs are listed but **must be re-confirmed and added to an allow-list before automated scanning begins.**

---

## Tier 1 — Daily/weekly scan, primary source

| Name | URL | What it covers | Cadence | Primary/Secondary |
|---|---|---|---|---|
| EUR-Lex (EU Official Journal) | https://eur-lex.europa.eu | EU legislation publication, ePrivacy, GDPR, Digital Omnibus, adequacy decisions | Weekly | Primary |
| European Data Protection Board (EDPB) | https://www.edpb.europa.eu | EDPB guidelines, opinions, Cookie Banner Taskforce reports, binding decisions | Weekly | Primary |
| CNIL (France) | https://www.cnil.fr/en | French DPA decisions, cookie/tracker recommendations, formal notices, fines | Weekly | Primary |
| ICO (UK) | https://ico.org.uk | UK DPA guidance (incl. PECR / Storage & Access Tech), enforcement actions, DUAA implementation | Weekly | Primary |
| Garante per la protezione dei dati personali (Italy) | https://www.garanteprivacy.it/web/guest/home_en | Italian DPA decisions; active on cookie enforcement | Weekly | Primary |
| AEPD (Spain) | https://www.aepd.es/en | Spanish DPA cookie guidelines and enforcement | Weekly | Primary |
| BfDI (Germany federal) + DSK (state DPAs joint) | https://www.bfdi.bund.de/EN/Home/home_node.html , https://www.datenschutzkonferenz-online.de | German cookie / TTDSG enforcement and joint positions | Weekly | Primary |
| DPC Ireland | https://www.dataprotection.ie | Lead DPA for many US tech firms; binding decisions | Weekly | Primary |
| UK Parliament — legislation.gov.uk | https://www.legislation.gov.uk | Official text of UK Acts incl. DUAA | Weekly | Primary |
| California Privacy Protection Agency (CPPA) | https://cppa.ca.gov | CCPA regulations, ADMT/cybersecurity audit rules, enforcement orders | Weekly | Primary |
| California Attorney General — Privacy | https://oag.ca.gov/privacy/ccpa | CCPA enforcement; AG opinion letters | Weekly | Primary |
| California Legislative Information | https://leginfo.legislature.ca.gov | Bill text (e.g., AB 566), chaptered statutes | Weekly | Primary |
| MeitY (India) | https://www.meity.gov.in | DPDP Act, DPDP Rules, MeitY notifications | Weekly | Primary |
| ANPD (Brazil) | https://www.gov.br/anpd/pt-br | LGPD resolutions, cookie guidance, sanction decisions | Weekly | Primary |
| Texas AG — Consumer Protection / Privacy | https://www.texasattorneygeneral.gov/consumer-protection | TDPSA enforcement actions | Weekly | Primary |
| Connecticut AG — Privacy | https://portal.ct.gov/ag/sections/privacy | CTDPA enforcement and updates | Weekly | Primary |
| Oregon DOJ — Consumer Privacy | https://www.doj.state.or.us/consumer-protection/id-theft-data-breaches/privacy/ | OCPA enforcement; UOOM guidance | Weekly | Primary |
| Colorado AG — Privacy | https://coag.gov/resources/colorado-privacy-act/ | CPA rules, UOOM list, enforcement | Weekly | Primary |
| New Jersey Division of Consumer Affairs | https://www.njconsumeraffairs.gov/ocp/Pages/NJ-Data-Privacy-Law-FAQ.aspx | NJDPA implementing regulations | Weekly | Primary |
| Maryland AG | https://www.marylandattorneygeneral.gov | MODPA enforcement | Weekly | Primary |
| IAPP Daily Dashboard | https://iapp.org/news/daily-dashboard/ | Cross-jurisdiction radar — points to primary stories the same morning | Daily | Secondary |
| IAPP US State Privacy Legislation Tracker | https://iapp.org/resources/article/us-state-privacy-legislation-tracker/ | All 50-state bills and statuses | Weekly | Secondary |
| IAPP Global Legislative Tracker | https://iapp.org/resources/article/global-comprehensive-privacy-law-mapping-chart/ | Global bills/laws map | Weekly | Secondary |

---

## Tier 2 — Monthly scan

| Name | URL | What it covers | Cadence | Primary/Secondary |
|---|---|---|---|---|
| CAC (Cyberspace Administration of China) | http://www.cac.gov.cn | PIPL implementing rules, cross-border transfer | Monthly | Primary |
| PDPC Singapore | https://www.pdpc.gov.sg | PDPA decisions and guidance | Monthly | Primary |
| OAIC Australia | https://www.oaic.gov.au | Privacy Act reforms, OAIC determinations | Monthly | Primary |
| Office of the Privacy Commissioner of Canada (OPC) | https://www.priv.gc.ca | PIPEDA, federal CPPA progress | Monthly | Primary |
| Commission d'accès à l'information du Québec | https://www.cai.gouv.qc.ca | Quebec Law 25 enforcement | Monthly | Primary |
| ANPD (Argentina) | https://www.argentina.gob.ar/aaip | LPDP reform progress | Monthly | Primary |
| INAI (Mexico) | https://home.inai.org.mx | LFPDPPP reforms | Monthly | Primary |
| UAE Data Office | https://u.ae/en/about-the-uae/digital-uae/data/data-office | UAE PDPL implementation | Monthly | Primary |
| Saudi Data & AI Authority (SDAIA) | https://sdaia.gov.sa/en/default.aspx | KSA PDPL | Monthly | Primary |
| Information Regulator (South Africa) | https://inforegulator.org.za | POPIA enforcement | Monthly | Primary |
| Personal Information Protection Commission (Korea) | https://www.pipc.go.kr/eng/ | PIPA enforcement and amendments | Monthly | Primary |
| Personal Information Protection Commission (Japan) | https://www.ppc.go.jp/en/ | APPI guidance and amendments | Monthly | Primary |
| Future of Privacy Forum (FPF) | https://fpf.org | UOOM analysis, state-law deep dives | Monthly | Secondary |
| NCSL state legislation tracker | https://www.ncsl.org | Bipartisan state-bill tracker | Monthly | Secondary |
| Husch Blackwell US State Tracker | https://www.huschblackwell.com/2024statelegislationtracker | US state privacy bill rollup | Monthly | Secondary |
| OneTrust DataGuidance | https://www.dataguidance.com | Multi-jurisdiction summaries; click through to primary | Monthly | Secondary |

---

## Tier 3 — Watch list (light/quarterly scan, but alert-on-change)

| Name | URL | What it covers | Cadence | Primary/Secondary |
|---|---|---|---|---|
| IAB Europe — TCF | https://iabeurope.eu/transparency-consent-framework/ | TCF policy & technical spec versioning, GVL changes | Monthly | Primary (industry framework) |
| IAB Tech Lab — GPP | https://iabtechlab.com/gpp/ | Global Privacy Platform spec changes | Monthly | Primary (industry framework) |
| Global Privacy Control (W3C-aligned) | https://globalprivacycontrol.org | GPC spec updates | Monthly | Primary |
| W3C Privacy Working Group | https://www.w3.org/Privacy/ | Browser/web standards on consent and tracking | Quarterly | Primary |
| Chrome Privacy Sandbox (third-party cookie deprecation) | https://privacysandbox.com | Chrome-side changes affecting consent flows | Monthly | Primary (vendor) |
| Apple — Safari ITP & WebKit policy | https://webkit.org/tracking-prevention/ | Safari tracking-prevention policy changes | Quarterly | Primary (vendor) |
| Mozilla — privacy & tracking policies | https://wiki.mozilla.org/Security/Anti_tracking_policy | Firefox policy changes | Quarterly | Primary (vendor) |
| ISO/IEC — JTC 1/SC 27 | https://www.iso.org/committee/45306.html | ISO/IEC 27701, 27018 updates | Quarterly | Primary |
| Court of Justice of the EU (CJEU) | https://curia.europa.eu | Cookie/consent/GDPR rulings (e.g., post-Schrems) | Weekly (incl. in Tier 1 effectively) | Primary |
| EU Legislative Train Schedule | https://www.europarl.europa.eu/legislative-train | Track Digital Omnibus and other in-flight files | Monthly | Primary |
| noyb / Max Schrems complaints docket | https://noyb.eu | Bellwether for upcoming DPA action | Monthly | Secondary |

---

## Operational notes for the engineering team

1. **Allow-list for automated WebFetch.** A material number of official domains (including `cppa.ca.gov`, `edpb.europa.eu`, `ico.org.uk`, `meity.gov.in`, `legislation.gov.uk`, `digital-strategy.ec.europa.eu`, `iabeurope.eu`) returned HTTP 403 in this run. Before standing cadence begins, please confirm the agent runtime can fetch these domains (likely an outbound proxy / user-agent / TLS issue).
2. **Per-source last-checked timestamp.** Recommend the agent persist a `last_seen_revision` per source to detect changes deterministically rather than relying on full re-summarisation each run.
3. **Two-source rule for ad-hoc alerts.** Per the operating prompt: ad-hoc alert only when ≥2 primary sources confirm. The Tier 1 Secondary entries (IAPP) are explicitly NOT counted as primary for the two-source rule.
4. **Quarterly source-list review.** Source lists drift; propose adding the agent's monthly run output a "sources I tried but couldn't reach" section so you can quickly fix coverage holes.

---

## For your review

**Director of Engineering — please approve, edit, or extend this list.** Specific decisions I'd value your input on:

- Are there **paid/licensed feeds** (e.g., DataGuidance Pro, Linklaters Privacy & Cybersecurity Tracker, Bird & Bird trackers) you want me to assume access to?
- Should I add **client-jurisdiction-specific** sources beyond the standard set (e.g., specific German Länder DPAs your top customers are exposed to)?
- Do you want **CJEU and national supreme court** rulings monitored at a finer cadence than weekly?
- Should I add a **TCF v3 horizon scan** as a separate watch even though no spec exists yet?
