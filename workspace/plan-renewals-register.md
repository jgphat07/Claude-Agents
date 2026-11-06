# Plan: Renewals Register for Jira/JSM (working name)

Status: PROPOSED. Owner approval is needed before any account is created, anything is published, or anyone is contacted.
Owner of plan: vice-president. Created 2026-11-06. Source scoring: `workspace/opportunities.md`, slate #2, candidate C (26/35).
**This plan supersedes `workspace/plan-jira-expiry-guard.md`.** It keeps the same platform and technical spike, but the offer is broader and the price anchor is higher, following the research brief's reshape recommendation (`workspace/research/jira-expiry-guard.md`).

Numbers marked (est.) are vice-president estimates. Numbers marked [S] are from search snippets. Atlassian install and price figures come from the verified Marketplace API pull dated 2026-11-03.

## 1. Offer
A Forge app for Jira Cloud and Jira Service Management. It is **one register for everything the company renews or that expires**: SaaS subscriptions, software licences, support contracts, warranties, domains and TLS certificates. **Upcoming deadlines become Jira work items automatically.**

It is a copy-and-improve product: we copy features and ideas only, never code, names, screenshots or listing text.

**Differentiators, each answering a gap or complaint in the competitors:**
1. **Cancel-by and notice dates, not just expiry.** Many contracts auto-renew unless cancelled 30-90 days before the end date. The expiry tracker (License Manager, 94 installs) focuses on domains, certs and licence end dates.
2. **Visible delivery log.** Every reminder and ticket the app created, or failed to create, is listed with its reason. This answers the "does not work" and "reminders never sent" complaints on License Manager and My Reminders for Jira [S].
3. **Annual cost per item plus a 12-month renewal-spend view.** This is a procurement and budget hook that pure reminder apps lack.
4. **Lighter and cheaper than full asset-management suites.** devsamurai and conelike charge $562.50-712.50/yr at 25 users.

**MVP (sellable after about 20 build hours):**
- Admin page with CRUD for items: type, vendor, owner, end date, notice period, cost, linked project. Plus CSV import.
- A daily scheduled trigger computes deadlines. At configurable thresholds (default 60/30/14/7/1 days before the *cancel-by* date) it creates or updates one Jira/JSM work item per item, with deduplication.
- Domain expiry is auto-filled via RDAP **if the spike passes**. Otherwise it is entered manually. **TLS auto-check is not in the MVP.** Certs are manual items until the spike proves raw TLS works.
- An overview page sorted by "next deadline", with the 12-month spend total.
- The delivery log.

**Phase 2 (only after 3 or more paying sites):**
- A JSM Assets date-field import.
- A second listing, "Reminders on any date field", built on the same engine (target C2).
- Entra ID secret and certificate expiry (opportunity #3 from slate #1).

**Not in scope:** onboarding calls, custom work, Data Center, auto-checkout, and anything that requires us to touch customer systems by hand.

## 2. Buyer
- IT, ops and finance/procurement admins at companies on Jira Cloud or JSM with **11-250 users**. They already pay for Marketplace apps and currently track renewals in spreadsheets or improvised Automation rules.
- MSPs running JSM for clients.
- **Where they look:** Marketplace search and categories ("asset management", "reminders", "license"), and Atlassian Community threads on expiry and renewal reminders (14 listed in the research brief, section 4).

## 3. Price (cfo to confirm)
- **Billing:** paid via Atlassian, with per-user tiers. Atlassian bills, collects and handles sales tax. 0% revenue share on eligible Forge earnings until $1M lifetime ([Atlassian, 2026](https://www.atlassian.com/blog/developer/updates-to-marketplace-revenue-share-2026)).
- **Proposed annual list prices**, positioned between License Manager and the asset suites:

| Users | License Manager | **Ours (proposed)** | Asset suites (devsamurai / conelike) |
|---|---|---|---|
| 1-10 | Free | **Free** (discovery via the "free up to 10 users" filter) | Free / $100 |
| 25 | $137.50 | **$250** | $562.50 / $712.50 |
| 50 | $275 | **$450** | n/a |
| 100 | $550 | **$800** | $2,250 / $2,850 |

### Customers needed for $3,000 MRR
| Blended ARPU per paying site (est.) | Paying sites needed |
|---|---|
| $15/mo (mostly about 25-user sites) | 200 |
| **$25/mo (base)** | **120** |
| $40/mo | 75 |

**Funnel (est.):** 8-12 installs per paying site, so about **1,000-1,400 cumulative installs**.
- **Reality check:** the two category leaders have about 1,350-1,550 installs after years on the Marketplace. One app reaching $3k MRR is the optimistic case.
- The realistic route is **this app plus the C2 sister listing** on the same codebase.

## 4. Free stack
| Need | Choice | Cost | Gotcha |
|---|---|---|---|
| Compute, scheduling | Forge functions plus a daily scheduled trigger | $0 within the per-app free allowance | Usage-based since Jan 2026. The allowance is [S-conflict] at 100k vs 200k GB-s/month. Dev-environment usage counts. No retry if the function throws. ([Forge pricing](https://developer.atlassian.com/platform/forge/forge-platform-pricing/)) |
| Storage | Forge KVS / custom entities | $0 within allowance | Stored-data pricing is "later in 2026" [S]. Keep items small. |
| Domain lookups | RDAP over HTTPS | $0 | Needs wildcard or customer-managed egress, which very likely costs the Runs-on-Atlassian badge (est.). RoA is not needed for 0% revenue share. **Decide the egress model before listing**, because changing it later forces re-consent. |
| Billing | Paid via Atlassian, with license-context checks | 0% | Must stay pure Forge, with no Connect modules |
| Alerts | Jira work items and their native notifications | $0 | No email provider needed |
| Docs, privacy, support | GitHub Pages plus a free email inbox or free JSM desk | $0 | Async-only support, stated on the listing |
| Dev site | Free Atlassian Cloud developer site | $0 | |

## 5. Smallest version that can take money within 14 days of listing approval
Build time is 4 weeks at 5 hrs/week. Marketplace review time is unknown (est. 1-4 weeks). The first $ can arrive within 14 days of approval because Atlassian trials convert automatically when the customer has billing on file.

**Week 1 (5 h): accounts, spike, gate**
- (1 h) **OWNER, after approving:** create an Atlassian developer account and a free cloud dev site, install the Forge CLI, and deploy hello-world.
- (2 h) **OWNER spike**, with results written to `workspace/build/renewals-register/spike.md`:
  - (a) A scheduled trigger creates a Jira work item.
  - (b) An RDAP lookup works for .com/.net/.org plus 2 ccTLDs, using wildcard vs customer-managed egress.
  - (c) License-context gating can be read in a function.
  - (d) Optional: does `tls.connect().getPeerCertificate()` work?
- (2 h) Data model plus the admin page skeleton (UI Kit).
- **Gate V1:** the vice-president decides go or switch, based on the spike and R1.

**Week 2 (5 h):** item CRUD, CSV import, deadline engine (notice-period math), daily trigger.

**Week 3 (5 h):** work-item creation with dedup and per-project settings, delivery log, license gating, error handling. Usage is batched to one run per site per day.

**Week 4 (5 h):** listing assets (name, icon, 3 screenshots, docs and privacy pages, security/data questionnaire), pricing tiers, and **submission (owner approval required)**.

## 6. Acquisition (no ads, near-zero ongoing effort)
1. **Marketplace listing SEO.** The title and highlights use buyer words: "renewal", "contract", "license", "subscription", "expiry", "reminder", "SaaS spend".
2. **Free up to 10 users**, to rank in the free filter and collect reviews.
3. **Atlassian Community.** One genuinely helpful answer per existing renewal/expiry thread, with vendor disclosure, plus one App Central article. **The owner approves each post first.**
4. **Ask for reviews in-app.** One unobtrusive prompt after 30 days of successful runs. No incentives, no fake reviews.
5. **Sister listing (C2)** for cross-discovery once the first app has paying sites.

## 7. Targets and timeline (est.)
| Milestone | Optimistic | Base | Conservative |
|---|---|---|---|
| Listed | Mid Dec 2026 | Jan 2027 | Feb 2027 |
| First $ | Jan 2027 | Feb-Mar 2027 | May 2027 |
| $1k MRR | Jul 2027 | Q1 2028 | Maybe never |
| $3k MRR | ~Nov 2027 (with the sister app) | Q3 2028 to 2029 | Plateau of $200-800 MRR |

**Candid odds (est.):**
- About 50% chance of some recurring revenue within 6 months of listing.
- About 10% chance of $3k/mo within 12 months.
- About 25-30% within 24 months.

These odds are low in absolute terms but still the best of the four options compared: A ~3%, B(i) ~2% (and not recurring), B(ii) ~1-2%.

## 8. Kill / iterate criteria
- **Gate V1 (end of Week 1):** if the scheduled trigger plus work-item creation fails on Forge, stop and reassess.
  - RDAP failing is **not** a kill. Domains become manual items.
  - If the owner does not approve account creation, nothing proceeds.
- **90 days after listing:** fewer than 30 installs means rewrite the listing and keywords once. Still under 30 installs after another 60 days means kill or pivot to C2.
- **6 months after listing:** zero paying sites means kill.
- **9 months after listing:** under $300 MRR means stop new features and maintain only, then build C2 on the codebase or stop.
- **Cost:** if Forge usage leaves the free allowance before $200 MRR, re-architect or kill. Costs must never exceed revenue.
- **Time:** support over 1 hr/week before $1k MRR means cut features. Over 2 hrs/week at any point means revisit.

## 9. Task list
| ID | Task | Owner | When | Needs owner approval? |
|---|---|---|---|---|
| O0 | Allow `marketplace.atlassian.com`, `developer.atlassian.com` and `www.atlassian.com` in session network settings (WebFetch still fails) | OWNER | Now | Yes (settings) |
| R1 | Pull 1-3 star reviews and feature lists for License Manager (1227641), devsamurai and conelike asset apps, My Reminders (1212778) and teamlead Reminder (1217030). Summarise complaint themes into `workspace/research/renewals-register.md` | research-assistant | Week 1 | No |
| R2 | Marketplace review requirements and typical approval time. Individual-partner payout path and tax forms (thread 102404) | research-assistant | Week 1 | No |
| O1 | Create the Atlassian developer account and free dev site, install the Forge CLI | OWNER | Week 1 | **Yes (account)** |
| O2 | Run the technical spike (section 5) and write `spike.md` | OWNER | Week 1 | No |
| V1 | Go/switch decision after O2 and R1 | vice-president | End of Week 1 | No |
| B1 | Functional spec plus differentiation matrix, based on R1 complaints. Features only, no copied text. Write to `workspace/build/renewals-register/spec.md` | business-development | Weeks 1-2 | No |
| O3 | Build the MVP (Weeks 2-3 scope) | OWNER | Weeks 2-3 | No |
| C1 | Confirm the tier prices and ARPU table against R1, and confirm the Forge free allowance figure (100k vs 200k GB-s) against projected usage | cfo | Week 2 | No |
| B2 | Listing copy: name, tagline, highlights, keywords | business-development | Week 3 | No |
| M1 | Name and trademark check (no "Jira" at the start of the name), icon, 3 screenshots, docs-site structure | marketing-social-media-manager | Week 3 | No |
| C2 | Create `workspace/metrics.md` (installs, trials, paying sites, MRR, support minutes/week, Forge usage). Tax flags: payouts are income, W-9/W-8 forms, sole-proprietor question | cfo | Week 4 | No |
| O4 | Marketplace partner profile, GitHub Pages docs and privacy policy, submit the listing | OWNER | Week 4 | **Yes (account + publishing)** |
| M2 | Draft the App Central article and 5 Community answers with vendor disclosure. **Not posted** until the owner approves each one | marketing-social-media-manager | Week 4+ | **Yes (publishing)** |
| V2 | Weekly review in `workspace/reviews/<date>.md` | vice-president | Weekly | No |

## 10. Unavoidable costs
- **None required.** Forge, the dev site, GitHub Pages and Marketplace billing are $0 at our scale.
- **Possible costs:**
  - A payment method on file for Forge overages (expected $0).
  - An optional custom domain, about $10-15/yr, after first revenue.
  - Income tax on payouts.
