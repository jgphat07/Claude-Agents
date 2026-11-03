# Research brief: Jira Expiry Guard (Forge expiry/renewal app)

Prepared by: research-assistant, 2026-11-03. Covers R1, R2 and part of R3 in `workspace/plan-jira-expiry-guard.md`.

## IMPORTANT: verification level
- **The Atlassian sites were still not reachable from this session.** WebFetch returned `getaddrinfo ENOTFOUND` for `marketplace.atlassian.com` (including the `/rest/2/addons` API), `developer.atlassian.com` and `www.atlassian.com` on 2026-11-03.
  - The owner must allow these domains in the session network settings before anyone can do a true primary-source read.
  - Following the proxy guidance, I stopped trying further hosts after these failures.
- **So every fact below comes from search-engine result snippets** that quote those pages. No page was read in full.
  - Tag **[S]** = snippet of the cited page. It is probably accurate but was not read in full.
  - Tag **[S-conflict]** = the snippets disagree with each other.
  - Tag **(est.)** = my estimate.
- **Install counts and prices still need a live read**, especially per-user cloud tiers, ratings and last-update dates. Run Test 0 below.

---

## 1. Verdict: TEST FIRST (leans NO-GO as the *only* route to $3k MRR)

| Question | Finding |
|---|---|
| Is there a gap? | Yes. The two direct apps are tiny: License Manager has **~102–110 installs** [S] and Certificate Renewal has **4 installs** [S]. |
| Is there demand? | Users keep asking for this. But the questions are mostly answered with **free native Jira Automation / JSM Assets rules** (see §4). The incumbent's ~100 installs after several years on the Marketplace suggest **a small paying market** (est.). |
| Can it hit $3k MRR alone? | **Unlikely.** The plan needs about 1,000–1,500 cumulative installs. The category leader has about 100 [S]. Its aggregator-listed starting price of $37.50/yr [S] is far below the plan's $30/site/month ARPU assumption. |
| Is it technically feasible on Forge? | Partly. Domain (RDAP over HTTPS) and manual items are feasible via backend fetch, with wildcard or customer-managed egress. **TLS cert reading is unproven.** `fetch` does not expose the peer certificate, and raw `tls.connect` in the Forge runtime is undocumented. It needs the spike. |
| Is the pick wrong? | **Not wrong as a cheap first Marketplace bet. Wrong as the $3k plan on its own.** |

**Recommended reshape:** lead with a broader **"renewals register"** that turns renewal dates into Jira/JSM tickets. It would cover SaaS subscriptions, licences, contracts and warranties, plus JSM Assets dates. Domain and SSL become features rather than the headline.
- Of the adjacent apps, only Cadence (SaaS renewals) clearly covers renewal tickets (see §3).
- The DMARC runner-up (#2) is **not** obviously better. It is crowded and depends on SEO (`workspace/opportunities.md`).
- Keep #3 (Entra secrets) as the phase-2 differentiator, as planned.

### Cheapest validation tests
| # | Test | Cost / time | Success threshold |
|---|---|---|---|
| 0 | Allow `marketplace.atlassian.com`, then pull `/rest/2/addons?text=expiry`, `?text=renewal`, `?text=certificate`, `?text=contract`, and `/rest/2/addons/{key}` plus `/pricing/cloud/live` for every app in §3 | $0, 15 min | Continue only if (a) any expiry/renewal app has **≥500 installs**, or (b) the combined direct and adjacent installs are **≥2,000**. If the best app is under 300 installs, the $3k-from-one-app target is not credible, so reshape or treat it as a portfolio app. |
| 1 | Forge spike (plan O2): `fetch` to a customer-entered host with `*` backend egress and with customer-managed egress; `tls.connect().getPeerCertificate()`; RDAP via `rdap.org` redirects | $0, 2 h (owner) | TLS readable **and** arbitrary-host fetch works. Otherwise reshape to RDAP plus manual items. |
| 2 | Ship a minimal paid listing that is free for ≤10 users (manual items + RDAP + ticket creation) | $0, ~15 h | **≥30 installs and ≥3 paying sites within 90 days of listing.** This matches and tightens the plan's kill rule. |

---

## 2. Buyer

| Who pays | Where they gather |
|---|---|
| IT/ops admins on Jira Cloud / JSM. Sites with more than 10 users, because the app is billed on the **host product's total user count** [S] ([Community](https://community.atlassian.com/forums/Jira-questions/Could-you-please-confirm-if-the-pricing-to-use-the-plugin-can-be/qaq-p/2820015)) | Atlassian Community: Jira questions, JSM, Automation questions, App Central ([community.atlassian.com](https://community.atlassian.com)) |
| MSPs running JSM for clients | r/jira, r/atlassian, r/msp, r/sysadmin (not verified in this pass) |
| Procurement/IT asset owners tracking vendor renewals | JSM Assets threads (see §4) |

**Market size hints**
- Atlassian has **>350,000 customers** (CEO, Q2 FY26) [S] and **57,334 customers with >$10k Cloud ARR** at Q4 FY26 [S] ([10-K FY26](https://www.sec.gov/Archives/edgar/data/0001650372/000165037226000036/team-20260630.htm), [Q3 FY26 release](https://secure.businesswire.com/news/home/20260430534706/en/Atlassian-Announces-Third-Quarter-Fiscal-Year-2026-Results)).
- **JSM: >65,000 organizations** (Q2 FY26) [S] ([BusinessWire](https://www.businesswire.com/news/home/20260205386782/en/Atlassian-Announces-Second-Quarter-Fiscal-Year-2026-Results)).
- "Marketplace and other" revenue was **$330.7M in FY26**, up 10%. Marketplace is not broken out separately [S] ([10-K](https://www.sec.gov/Archives/edgar/data/0001650372/000165037226000036/team-20260630.htm)).

---

## 3. Competitors

Install, rating and price figures are [S] unless noted. "?" means the figure was not found in snippets, so pull it with Test 0.

### Direct: domain/SSL/licence expiry turned into Jira issues
| App | Vendor | Installs | Rating | Price | Last version | Notes / weaknesses |
|---|---|---|---|---|---|---|
| [License Manager – Domain and SSL Cert Expiration Monitoring](https://marketplace.atlassian.com/apps/1227641/license-manager-domain-and-ssl-cert-expiration-monitoring) | Softlist (founded 2004) | **~102–110** [S] (snippets vary) | **3.8/5, 6 cloud reviews** [S] | Paid via Atlassian. "Starting at **$37.50/yr**" per [Software Advice](https://www.softwareadvice.com/license-management/license-manager-for-jira-profile/) / [GetApp](https://www.getapp.com/it-management-software/a/license-manager-for-jira) [S]. Per-user tiers ? | 2.0.72, Feb 2026 [S] | Creates Jira issues, 1–90 day window, renewal calendar, CSV import, data in entity properties [S]. **Weaknesses:** a May 2023 review says it "does not work" [S]. A community thread reports missed notifications and ccTLD gaps. .gov/.edu/.uk etc. are not in public WHOIS, so they must be added manually [S] ([App Central post](https://community.atlassian.com/t5/App-Central/Monitor-Domain-amp-SSL-Certificate-Expiry-from-Jira/ba-p/1978551)). Forge or Connect ? |
| [Certificate Renewal](https://marketplace.atlassian.com/apps/1235426/certificate-renewal) | Adattada AG [S] | **4** [S] | ? | Paid via Atlassian, price ? | **3.17.0, Jun 20 2026** [S] (another snippet said 3.15.0, Apr 2026) | TLS only. Creates an issue or JSM request before expiry and re-checks public endpoints for renewal. Data stays in Jira [S]. Weakness: TLS-only, almost no traction. |

### Adjacent: renewals, contracts, assets, generic reminders
| App | Vendor | What overlaps | Price / installs | Last version |
|---|---|---|---|---|
| [Cadence: License Management & Inactive Users for Jira](https://marketplace.atlassian.com/apps/2729885846/cadence-license-management-inactive-users-for-jira) | Stackedboost | Tracks SaaS subscriptions and renewal dates. "Daily check turns each upcoming renewal into an assignable Jira task", with Slack/Discord posts [S] | ? / ? | 5.4.0, Aug 2 2026 [S] |
| [Vendor & Contract Management](https://marketplace.atlassian.com/apps/139435857/vendor-contract-management) | ? | Contract end dates and renewal alerts [S] | Paid via Atlassian / ? | 2.5.0, Mar 4 2026 [S] |
| [Support Contract Management](https://marketplace.atlassian.com/apps/2683916354/support-contract-management) | Arribatt | Contract renewals and expirations [S] | ? / ? | 2.2.0, Jul 9 2026 [S] |
| [Appvibe Contract Management](https://marketplace.atlassian.com/apps/1236504/appvibe-contract-management) | Appvibe | Renewal-date alerts [S] | **Free** [S] | 2.1.0, Feb 3 2025 [S] |
| [Asset Management for Jira (IT Assets & License Manager)](https://marketplace.atlassian.com/apps/1222692/asset-management-for-jira-it-assets-license-manager) | ? | Licence and asset tracking. A 2026 reviewer cites expiry notifications [S] | ? / ? | Nov 2024 [S] |
| [Asset Maintenance Reminder](https://marketplace.atlassian.com/apps/2709202033/asset-maintenance-reminder) | ? | Date-based asset reminders (inferred from the name; not verified) | ? | ? |
| [Reminders for Jira](https://marketplace.atlassian.com/apps/1212665/reminders-for-jira) | ? | Relative and repeating reminders on any date field. Community partners recommend it for renewal dates [S] | ? | ? |
| [OpenLM Alerts for Jira](https://marketplace.atlassian.com/apps/1237582/openlm-alerts-for-jira) | OpenLM | Licence-expiry warnings. **Free, unsupported** [S] | Free | ? |
| **Native substitute:** Jira Automation scheduled rule + JQL/AQL on a date field (JSM Assets) | Atlassian | The most common answer on Community (see §4) | Included in Jira/JSM | n/a |

### Corrections to the plan and opportunity file
| Plan claim | Correction |
|---|---|
| "Two direct competitors" | There are 2 direct apps plus **at least 7 adjacent apps**. The free **Jira Automation/Assets** workaround is the real competitor. |
| Certificate Renewal "v3.15.0 (Apr 2026)" | One snippet shows **3.17.0 (Jun 20 2026)** [S-conflict]. |
| Kill rule: "2,000+ installs = dominance" | The opposite risk applies. The leader has only about 100 installs, which signals **a small market, not an open one**. Add a "category too small" check (Test 0). |
| Blended ARPU $30/site/month (est.) | The only price found is **$37.50/yr starting** for License Manager [S]. The cfo should model a much lower ARPU until per-user tiers are pulled. |
| "1–10 users are free by Marketplace convention" | This is **optional**. Since Dec 2021, partners *may* set the 1–10 tier to $0. It is not a rule, and a "Free up to 10 users" filter exists [S] ([dev community](https://community.developer.atlassian.com/t/introducing-a-new-0-price-point-for-your-1-10-cloud-app-user-tier/54225)). |
| Forge free compute allowance (not stated) | [S-conflict]: **100,000 GB-s/month** per the Jan 2026 blog snippet, and **200,000 GB-s** per the pricing-page snippet ([pricing](https://developer.atlassian.com/platform/forge/forge-platform-pricing/)). The cfo must verify (C2). |

---

## 4. Demand evidence (Atlassian Community)
Thread titles and summaries come from search snippets. I did not invent any quotes.

| # | Thread | What it shows |
|---|---|---|
| 1 | [Best way to get notified on soon licence expiration](https://community.atlassian.com/forums/Jira-questions/Best-way-to-get-notified-on-soon-licence-expiration/qaq-p/2292550) | Wants reminders at 4/3/2/1 weeks and 1 day before expiry, then daily [S] |
| 2 | [jira alert by email certificat date expiration](https://community.atlassian.com/t5/Jira-questions/jira-alert-by-email-certificat-date-expiration/qaq-p/1695002) | Certificate expiry alerts |
| 3 | [Automation rule that sends an email reminder X days before the…](https://community.atlassian.com/forums/Automation-questions/Automation-rule-that-sends-an-email-reminder-Xdays-before-the/qaa-p/3185253) | Answer: renewal work item 45 days before the renewal date [S] |
| 4 | [Need help with Jira Automation for expiry date reminders](https://community.atlassian.com/forums/discussion/3263588/need-help-with-jira-automation-for-expiry-date-reminders) | Recent (2026) expiry-reminder request |
| 5 | [Tracking our vendor applications, especially when renewal dates…](https://community.atlassian.com/forums/Jira-Service-Management/Tracking-our-vendor-applications-especially-when-renewal-dates/qaq-p/3108882) | JSM vendor renewal tracking |
| 6 | [We currently track our customers' license expiry dates in a…](https://community.atlassian.com/forums/Jira-Service-Management/We-currently-track-our-customers-license-expiry-dates-in-a/qaq-p/2697538) | Moving licence expiry tracking into JSM/Assets |
| 7 | [Issue with Automating Asset Expiration Email Notification](https://community.atlassian.com/t5/Jira-questions/Issue-with-Automating-Asset-Expiration-Email-Notification-in/qaq-p/2805674) | DIY pain: empty smart values [S] |
| 8 | [Send email when asset expires](https://community.atlassian.com/forums/Jira-Service-Management/Send-email-when-asset-expires/qaa-p/3128052) | Oct 2025 working AQL + lookup recipe. **The free substitute works** [S] |
| 9 | [Notification via email or in-app notification for license…](https://community.atlassian.com/t5/Confluence-questions/Notification-via-email-or-in-app-notification-for-license/qaq-p/1643218) | Licence notification |
| 10 | [Plugin expiry notification mail](https://community.atlassian.com/t5/Jira-Software-questions/Plugin-expiry-notification-mail/qaq-p/1137241) | Marketplace-app licence expiry |
| 11 | [Asset Management for Jira – Alerts](https://community.atlassian.com/t5/Jira-Service-Management/Asset-Managment-for-Jira-Alerts/m-p/2334102) | Alerts on asset dates |
| 12 | [How to Use Jira Automation to Manage License and Certificate…](https://community.atlassian.com/forums/New-to-Jira-articles/How-to-Use-Jira-Automation-to-Manage-License-and-Certificate/ba-p/3194872) | A tutorial exists, so the DIY route is documented |
| 13 | [Stop Paying for Ghost Licenses: 3 Ways to Manage IT Subscriptions](https://community.atlassian.com/forums/App-Central-articles/Stop-Paying-for-Ghost-Licenses-3-Ways-to-Manage-IT-Subscriptions/ba-p/3238154) | A vendor is marketing in the same space |
| 14 | [Monitor Domain & SSL Certificate Expiry from Jira](https://community.atlassian.com/t5/App-Central/Monitor-Domain-amp-SSL-Certificate-Expiry-from-Jira/ba-p/1978551) | Incumbent's 2022 marketing post |

**Read-out:** demand is real but recurring. Most answers point to free Automation/Assets recipes, and the paid incumbents are tiny.
- R2 asked for 20+ threads. I found 14 relevant ones. **Evidence that buyers will pay for this is thin.**
- **Search interest and trend data:** none found in this pass. Google Trends was not fetched.

---

## 5. Atlassian terms

| Topic | Finding | Source |
|---|---|---|
| Revenue share, Forge | **Confirmed [S]: 0% on eligible Forge earnings until $1M lifetime Forge revenue**, starting **1 Jan 2026**. It is counted **per partner company, not per app** (subsidiaries roll up). It is **temporary and may change**. Connect-on-Forge apps are **not** eligible. | [Atlassian blog: Updates to Marketplace Revenue Share 2026](https://www.atlassian.com/blog/developer/updates-to-marketplace-revenue-share-2026); [dev community 91727](https://community.developer.atlassian.com/t/marketplace-revenue-share-updates-2026/91727) |
| Runs on Atlassian (RoA) early start | Apps with the RoA badge got the 100% take-home **early, from Oct 2025**. Non-RoA Forge apps get it from 1 Jan 2026 [S]. **RoA is not required for 0%.** | [Atlassian blog](https://www.atlassian.com/blog/developer/runs-on-atlassian-apps-can-now-take-home-100-of-marketplace-revenue) |
| Rates after $1M | Forge 15%→16% on **1 Apr 2026**, 16%→17% on **1 Oct 2026**. Connect 15%→20% (Apr 2026), then 25% (Oct 2026). Changes come with at least 6 months' notice [S] | [Extended timelines blog](https://www.atlassian.com/blog/developer/extended-timelines-for-marketplace-revenue-share-changes) |
| Pre-2026 revenue counting | [S-conflict]: the FAQ snippet says pre-2026 Forge revenue counts; another page says migrated Connect apps start at $0. **Irrelevant to us as a new partner.** | [pricing FAQ](https://developer.atlassian.com/market/faqs/pricing-payment-billing) |
| 1–10 users free | **Optional** for the partner. There is no rule. Billing is based on the host product's user count [S] | [dev community 54225](https://community.developer.atlassian.com/t/introducing-a-new-0-price-point-for-your-1-10-cloud-app-user-tier/54225) |
| Payouts | Monthly Paid-via-Atlassian payouts to a bank account (wire/EFT). Non-US partners use W-8BEN or W-8BEN-E; without one, 30% US withholding applies. **No official minimum payout threshold found.** Individuals without a company: open question ([thread 102404](https://community.developer.atlassian.com/t/individual-developer-no-registered-company-whats-the-minimum-verification-needed-to-publish-a-paid-via-atlassian-app/102404)) [S, community only] | [Canada thread](https://community.developer.atlassian.com/t/is-canada-a-supported-payout-country-for-marketplace-partners/103113), [Ukraine thread](https://community.developer.atlassian.com/t/marketplace-payouts-for-a-partner-based-in-ukraine-sole-proprietor/103157) |
| Forge pricing (from 1 Jan 2026) | Compute: **100k or 200k GB-s/month free** [S-conflict], then $0.000025/GB-s. KVS reads/writes: 0.1 GB free, then reads $0.055/GB and writes $1.090/GB. KVS stored data: not charged at launch, "pricing later in 2026". SQL: 730 GB-hours free. Logs: 1 GB free. Allowances are per app and monthly [S] | [Forge pricing](https://developer.atlassian.com/platform/forge/forge-platform-pricing/), [Jan 2026 blog](https://www.atlassian.com/blog/developer/updates-to-forge-pricing-effective-january-2026) |
| Review time | **Not found.** Still open (R3). | n/a |

---

## 6. Forge technical feasibility

| Question | Answer | Confidence and source |
|---|---|---|
| Can backend `fetch` reach **arbitrary customer-entered hosts**? | **Yes, two ways.** (1) A wildcard `*` under `permissions.external.fetch.backend` works, but Forge warns about global wildcards. (2) **Customer-managed egress**: admins add domains at runtime through `@forge/bridge` permissions. There is no blanket "accept" option by design. | [S] [egress docs](https://developer.atlassian.com/platform/forge/add-content-security-and-egress-controls/), [community 63287](https://community.developer.atlassian.com/t/proxy-support-in-calling-external-api-in-forge/63287), [customer-managed egress](https://developer.atlassian.com/platform/forge/customer-managed-egress-and-remotes/), [RFC-94](https://community.developer.atlassian.com/t/rfc-94-configurable-egress-and-remotes/92393) |
| Status of customer-managed egress | A changelog snippet says it became **GA on 15 Oct 2026**. The API reference (updated 4 Jun 2026) still says Preview. It is not supported on Government Cloud. | [S-conflict] [API ref](https://developer.atlassian.com/platform/forge/apis-reference/customer-managed-egress-and-remotes-api/) |
| Changing egress later | Needs a new version, and existing installs must re-consent (the snippet said "uninstall and reinstall"; verify). **Decide the egress model before listing.** | [S] [egress docs](https://developer.atlassian.com/platform/forge/add-content-security-and-egress-controls/) |
| Does `fetch` expose certificate info? | **No.** The Fetch API has no peer-certificate access. This is a general runtime fact, also stated for other fetch runtimes ([bunny.net](https://bunny.net/docs/scripting/node-tls)). | High for fetch |
| Raw TLS (`tls.connect`/`getPeerCertificate`)? | **Undocumented.** The Node.js runtime page says it is a "full Node.js environment" with some `https`/`console` methods replaced so that traffic routes through Forge. Nothing says whether `net`/`tls` sockets are allowed or blocked by egress. **This is the deciding spike item (O2b).** | [S] [Node.js runtime](https://developer.atlassian.com/platform/forge/function-reference/nodejs-runtime/) |
| Scheduled triggers | Intervals: **fiveMinute, hour, day, week**. They share the normal function invocation limits. **No retry if the function throws.** Exact timeout figure not retrieved. | [S] [add scheduled trigger](https://developer.atlassian.com/platform/forge/add-scheduled-trigger), [limits](https://developer.atlassian.com/platform/forge/platform-quotas-and-limits) |
| Runs on Atlassian impact | RoA requires **no egress of in-scope data** (analytics excepted), Atlassian-hosted compute and storage, and data residency. Sending customer hostnames to RDAP servers or customer endpoints **very likely disqualifies the badge** (est.). Whether customer-managed egress keeps RoA is [S-conflict]. Run `forge eligibility`. **RoA is not needed for 0% revenue share.** | [RoA docs](https://developer.atlassian.com/platform/forge/runs-on-atlassian/), [community 102219](https://community.developer.atlassian.com/t/runs-on-atlassian-eligibility-do-inbound-ci-pushes-and-customer-initiated-import-export-count-as-egress/102219) |
| WHOIS / RDAP | **WHOIS (TCP port 43) needs raw sockets, so assume it is unavailable.** RDAP is HTTPS. The `rdap.org` bootstrap answers with a 302 to the registry's RDAP server, and registries may 307 to a registrar's server. **So the egress list must include many registry and registrar hosts, which practically means a wildcard.** Alternatively, embed the IANA bootstrap list and accept registry-level data only. Some ccTLDs have no RDAP. | [S] [simplified.guide](https://www.simplified.guide/whois/rdap-query), [IETF referrals draft](https://datatracker.ietf.org/doc/draft-ietf-regext-rdap-referrals/), [intodns](https://intodns.ai/tools/whois-lookup) |
| Usage cost (est.) | One daily run per site with tens of RDAP/TLS checks is far inside 100k GB-s/month at low install counts (est.). The cfo should confirm in C2. | est. |

---

## 7. Pricing benchmarks (for the cfo)
| App | Model | Price found | Status |
|---|---|---|---|
| License Manager (Softlist) | Paid via Atlassian | "Starting at $37.50/yr" | [S] aggregator. Marketplace tiers not read |
| Certificate Renewal | Paid via Atlassian | ? | Not found |
| Vendor & Contract Management | Paid via Atlassian | ? | Not found |
| Appvibe Contract Management | Free | $0 | [S] |
| OpenLM Alerts | Free (unsupported) | $0 | [S] |
| Cadence, Reminders for Jira, Asset Mgmt for Jira | Paid via Atlassian (assumed) | ? | Run Test 0 |

**Thin evidence.** Per-user cloud tiers could not be read. Test 0 fills this table in 15 minutes once the domain is allowed.

---

## 8. Risks
| Risk | Detail |
|---|---|
| **Small market** | The best direct app has ~100 installs [S], and free native recipes satisfy most askers. |
| Free substitutes | Jira Automation + Assets recipes work ([thread 3128052](https://community.atlassian.com/forums/Jira-Service-Management/Send-email-when-asset-expires/qaa-p/3128052)). Free apps also exist (Appvibe, OpenLM). |
| Technical | TLS reading on Forge is unproven. A wildcard egress may lower customer trust and loses RoA (est.). Egress changes after launch force re-consent. |
| Platform | The 0% revenue share is "temporary and may change" [S]. Forge has charged for usage since Jan 2026. |
| Payout/legal | An individual (non-company) partner's path to paid listing is unclear ([thread 102404](https://community.developer.atlassian.com/t/individual-developer-no-registered-company-whats-the-minimum-verification-needed-to-publish-a-paid-via-atlassian-app/102404)). Tax forms are needed. |
| Trademark | Avoid "Jira" at the start of the app name (M1 to verify against Atlassian brand guidelines; not fetched). |

---

## Verified Marketplace data (pulled directly via Marketplace REST API, 2026-11-03)

Source: `https://marketplace.atlassian.com/rest/2/addons?text=<query>&hosting=cloud` and
`/rest/2/addons/<key>/pricing/cloud/live`. The research agent's fetch tool could not resolve these hosts;
the shell could. These numbers supersede the snippet-based estimates above.

### Direct competitors (expiry / certificate / domain tracking)
| App | Key | Installs | Rating | Cloud price (annual) |
|---|---|---|---|---|
| License Manager – Domain and SSL Cert Expiry | pl.softlist.lic-manager | 94 | 3.75 (6) | free ≤10 users; 25u $137.50; 50u $275; 100u $550 |
| Certificate Renewal | com.adattada.maintenance.certificate | 4 | — | — |
| Licenses Tracker | com.moy.jira.plugins.lt | 6 | 3.75 (1) | — |
| Vendor & Contract Management | com.arribatt.plugins.vcm | 22 | — | — |
| License Radar / License Sentinel | — | 1 each | — | — |

**Finding:** the pure "expiry tracker" category is tiny: the leader has 94 installs after years on the market.

### Adjacent, proven categories (much larger)
| App | Installs | Rating | Cloud price (annual) |
|---|---|---|---|
| IT Assets, License – Asset Management (devsamurai) | 1,541 | 4.72 (71) | free ≤10u; 25u $562.50; 100u $2,250 |
| Asset Management for Jira (conelike) | 1,350 | 4.38 (67) | 10u $100; 25u $712.50; 100u $2,850 |
| My Reminders for Jira (Atlassian) | 3,427 | 3.55 (79) | — |
| Reminder for Jira (teamlead) | 1,177 | 4.53 (32) | 10u $20; 25u $87.50; 100u $350 |
| Reminders for Jira (deniz) | 713 | 4.38 (20) | free ≤10u; 25u $100; 100u $400 |

**Implication (estimate):** asset/license management apps charge roughly 4–5× what the expiry tracker charges and have
~15× the installs. "Expiry + renewals" works better as a feature of a lightweight IT asset/licence/renewals register
than as a standalone app. The original plan's ~$30/site/mo ARPU only holds at roughly 75–100+ user sites at
asset-management pricing; at License Manager pricing it is ~$11–46/mo per site.
