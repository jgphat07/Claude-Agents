# Opportunity slate #1 (2026-11-03)

Prepared by: vice-president (did the business-development sourcing, research-assistant evidence, and cfo math in this pass; no Agent access).

## Owner constraints used as hard filters
- Technical/IT owner, **5 hrs/week**, **$0 up front** (free tiers only; per-transaction fees OK)
- **Fully automated after launch**: no manual fulfillment, no client services, no calls (async product support via email/tickets is unavoidable for any paid software and is budgeted at ~30 min/week)
- **No paid ads**, so acquisition must come from a marketplace, directory, integration listing, or SEO
- First goal: **$3,000/month recurring**

## Research limits (read this first)
- WebFetch could not reach several sites from this session: trustmrr.com, healthchecks.io, indiehackers.com, www.atlassian.com, marketplace.atlassian.com. Facts from those domains come from **search-result snippets**, not page reads. Before we commit any build hours, `research-assistant` must confirm them directly, and the owner may need to allow those domains.
- Every number marked **(est.)** is a vice-president estimate, not a sourced fact.

## Scoring rubric
Seven criteria, each scored 1-5, where **5 is always good**:
- Demand evidence
- Willingness to pay (WTP)
- Automation potential
- Time to first $ (5 = fastest)
- Startup cost (5 = $0)
- Owner's unfair advantage (IT/technical)
- Risk (5 = lowest risk)

The maximum total is 35.

| # | Candidate | Demand | WTP | Auto | Time | Cost | Edge | Risk | **Total** |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Forge app on Atlassian Marketplace: expiry/renewal automation for Jira Service Management | 3 | 4 | 5 | 2 | 5 | 4 | 3 | **26** |
| 2 | DMARC report monitoring for SMBs/MSPs (Cloudflare Workers + Email Routing) | 5 | 3 | 5 | 2 | 4 | 4 | 2 | **25** |
| 3 | Entra ID app-secret/certificate expiry monitor for MSPs (multi-tenant) | 3 | 4 | 5 | 2 | 4 | 5 | 2 | **25** |
| 4 | SSL/domain/DNS-change monitor for MSPs and agencies (standalone SaaS) | 3 | 4 | 5 | 2 | 4 | 4 | 2 | **24** |
| 5 | Chrome extension with a paid tier for IT admins/devs | 3 | 2 | 5 | 3 | 5 | 3 | 2 | **23** |
| 6 | Cron/heartbeat monitoring SaaS | 4 | 3 | 5 | 2 | 4 | 3 | 1 | **22** |
| 7 | "CVEs for your stack" alert subscription | 3 | 2 | 5 | 2 | 4 | 4 | 2 | **22** |
| 8 | Freemium WordPress plugin (security/ops) sold via Freemius | 4 | 2 | 3 | 2 | 5 | 3 | 3 | **22** |
| 9 | Paid utility API on Rapid (DNS/WHOIS/email-auth checks) | 2 | 2 | 5 | 3 | 4 | 4 | 2 | **22** |
| 10 | Shopify app (store-ops utility) | 3 | 3 | 4 | 2 | 4 | 3 | 2 | **21** |
| 11 | Third-party SaaS status aggregator (IsDown-style) | 4 | 4 | 4 | 2 | 3 | 3 | 1 | **21** |
| 12 | Programmatic-SEO site with recurring SaaS affiliates (IT/MSP tools) | 3 | 2 | 4 | 1 | 4 | 3 | 1 | **18** |

Considered and excluded:
- **GitHub Marketplace paid app.** Paid plans require a verified-publisher org and, per GitHub docs, a minimum of 100 installations, so time to first $ is too long ([GitHub docs](https://docs.github.com/en/apps/github-marketplace/creating-apps-for-github-marketplace/requirements-for-listing-an-app)).
- **Paid AI-written newsletter.** It is a quality and deception risk, and it needs audience building we can't fund.
- **Uptime monitoring and status pages.** These are saturated.

---

## Free-tier stack facts and gotchas (they apply to every candidate)
| Item | Fact | Source |
|---|---|---|
| Vercel Hobby | **Non-commercial personal use only**, so it can't be used for anything that charges money | [Vercel fair use](https://vercel.com/docs/limits/fair-use-guidelines) |
| Supabase Free | 500 MB DB. **Projects pause after 1 week of inactivity**, and free projects have no backups | [simplebackups](https://simplebackups.com/blog/supabase-free-tier-paused), [jetadmin](https://www.jetadmin.io/blog/supabase-pricing-2026-guide-to-plans-limits-and-real-world-costs/) |
| Cloudflare Workers Free | 100k requests/day. **5 Cron Triggers per account**. Very low CPU time per invocation. D1 is included (around 5M rows read/day per secondary sources). Workers' `fetch` does **not** expose peer TLS certificates, so SSL-expiry checks need another runtime (est., verify) | [CF limits](https://developers.cloudflare.com/workers/platform/limits), [CF pricing](https://developers.cloudflare.com/workers/platform/pricing/) |
| Cloudflare Email Routing to Email Workers | Can receive mail on a domain and parse attachments in a Worker. Our only "free" claim is from a third-party page, so verify | [flaviocopes](https://flaviocopes.com/cloudflare-email-workers/) |
| Resend Free | **100 emails/day**, 3,000/month | [Resend docs](https://resend.com/docs/knowledge-base/resend-sending-limits) |
| Lemon Squeezy / Paddle (merchant of record) | 5% + 50c per transaction. Surcharges are reported on international and subscription payments | [dodopayments](https://dodopayments.com/blogs/lemonsqueezy-review) |
| Stripe direct | Not a merchant of record, so the owner handles sales tax/VAT (tax flag for cfo) | n/a |
| Atlassian Forge | Usage-based pricing since **Jan 2026**, with a **free monthly allowance per app**. Forge LLMs and Containers have **no** free allowance. Usage in dev environments counts. Atlassian advises adding a payment method to avoid interruption | [Atlassian blog](https://www.atlassian.com/blog/developer/updates-to-forge-pricing-effective-january-2026), [Forge pricing](https://developer.atlassian.com/platform/forge/forge-platform-pricing/) |
| Atlassian Marketplace revenue share | **0% on eligible Forge earnings until $1M lifetime** (2026). Apps with Connect modules don't qualify | [Atlassian blog](https://www.atlassian.com/blog/developer/updates-to-marketplace-revenue-share-2026), [community thread](https://community.developer.atlassian.com/t/marketplace-revenue-share-updates-2026/91727) |
| Shopify App Store | 0% on the first $1M **lifetime** (changed in 2025), 15% after that | [Shopify changelog](https://shopify.dev/changelog/update-to-shopifys-app-developer-revenue-share) |
| Rapid (RapidAPI) | **25%** marketplace fee from Nov 15, 2025 | [Rapid docs](https://docs.rapidapi.com/docs/payouts-and-finance) |
| Freemius (WP) | 7% for the WordPress package, plus gateway fees of about 3% + 30c | [Freemius](https://freemius.com/help/documentation/getting-started/our-pricing/) |
| ExtensionPay | Free per its own site. One secondary source says 5% + Stripe | [ExtensionPay](https://extensionpay.com/articles/add-stripe-payments-to-chrome-extensions), [fungies guide](https://fungies.io/?p=39126) |
| SEO as a channel | AI Overviews cut organic CTR. Pew: 15% to 8% on AI-Overview SERPs. Seer: -61% on informational queries | [ppc.land/Seer](https://ppc.land/google-ai-overviews-reduce-organic-ctr-61-paid-traffic-68/), [Search Engine Land](https://searchengineland.com/google-ai-overviews-drive-drop-organic-paid-ctr-464212) |

**Implication:** with no ads and 5 hrs/week, a channel the owner doesn't have to operate (a marketplace that already has buyer traffic and handles billing) is worth more than a slightly better product idea that depends on SEO.

---

## Candidate detail

### 1. Forge app: expiry and renewal automation for Jira Service Management (score 26, PICK)
- **Buyer:** IT and ops teams that already run Jira Service Management or Jira Cloud (in-house IT, MSPs on JSM).
- **Offer:** A register of everything that expires (domains, TLS certs, software licenses, contracts, and in phase 2, Entra app secrets). It auto-checks what it can (domain expiry via RDAP, TLS where the runtime allows) and **auto-creates Jira/JSM tickets** at 30/14/7 days.
- **Price:** Atlassian per-user tiers, free for 1-10 users (the Marketplace norm, [Atlassian dev community](https://community.developer.atlassian.com/t/introducing-a-new-0-price-point-for-your-1-10-cloud-app-user-tier/54225)), with paid tiers above that. Blended ARPU target is **about $30/paying site/month (est.)**.
- **Stack:**
  - Hosting, DB, and scheduling: Forge functions, Forge storage, and scheduled triggers, all inside the free allowance.
  - Payments: Atlassian bills, collects, and handles tax, at 0% revenue share.
  - Email: Jira notifications, so no email provider is needed.
  - Docs/privacy page: GitHub Pages or a free Confluence site.
  - **No domain required.**
- **Gotchas:**
  - Forge egress must be declared in the manifest. Whether arbitrary customer hosts can be fetched, and whether raw TLS inspection works, is an **unverified technical spike**.
  - A Forge payment method on file is advised.
  - Marketplace approval plus a security/privacy questionnaire.
  - Cloud only.
- **Acquisition without ads:**
  - Atlassian Marketplace search and category browsing. Atlassian cites 5,700+ apps and about 20,000 app installs/week across the Marketplace ([Atlassian community](https://community.atlassian.com/t5/App-Central/Things-you-might-not-know-about-the-Atlassian-Marketplace/ba-p/2326712)).
  - The "free up to 10 users" filter.
  - Answering the recurring Atlassian Community questions on expiry reminders.
- **Evidence:**
  - Competitors exist and are actively maintained, which validates demand: "License Manager - Domain and SSL Cert Expiration Monitoring" (v2.0.72, Feb 2026) ([listing](https://marketplace.atlassian.com/apps/1227641/license-manager-domain-and-ssl-cert-expiration-monitoring)) and "Certificate Renewal" (v3.15.0, Apr 2026) ([listing](https://marketplace.atlassian.com/apps/1235426/certificate-renewal)). Their install counts and prices are **not yet verified** because the domain was blocked.
  - Users repeatedly ask how to get expiry reminders in Jira ([community 1](https://community.atlassian.com/forums/Jira-questions/Best-way-to-get-notified-on-soon-licence-expiration/qaq-p/2292550), [community 2](https://community.atlassian.com/t5/Jira-questions/jira-alert-by-email-certificat-date-expiration/qaq-p/1695002), [community 3](https://community.atlassian.com/forums/Automation-questions/Automation-rule-that-sends-an-email-reminder-Xdays-before-the/qaa-p/3185253)).
  - An indie Atlassian app reportedly reached $4,149 MRR ([Indie Hackers title, unverified](https://www.indiehackers.com/post/reaching-4149-mrr-in-the-atlassian-marketplace-a3cc93a067)). Atlassian's own case study cites a founder who went full-time at about $10k MRR ([Atlassian blog](https://www.atlassian.com/blog/developer/developer-turned-atlassian-marketplace-app-entrepreneur)).
- **Risks:**
  - Two direct competitors already exist.
  - Atlassian platform/policy risk (revenue share and Forge pricing have both changed recently).
  - Small sites stay free forever.
  - Marketplace ranking is opaque.

### 2. DMARC report monitoring for SMBs/MSPs (score 25, runner-up)
- **Buyer:** Small businesses and MSPs managing client domains.
- **Offer:** Point the `rua=` address at us. We parse aggregate XML and send weekly digests and alerts.
- **Price:** $9-15/domain/month (est.), positioned under Postmark's $14/domain.
- **Stack:**
  - Cloudflare Email Routing to an Email Worker for parsing, D1 for storage, and Workers Cron.
  - Resend free tier, where the 100/day limit caps digests.
  - Payments via Lemon Squeezy.
  - Needs a domain: **about $10/yr, the only real cost**.
- **Acquisition:** A free DMARC/SPF/DKIM checker tool page (SEO plus link magnet) and comparison pages.
- **Evidence:**
  - Mandates create demand. Google/Yahoo require DMARC from bulk senders, and Microsoft Outlook has required SPF+DKIM+DMARC for >5k/day senders since May 5, 2025 ([Slashdot/BetaNews](https://tech.slashdot.org/story/25/05/05/1817247/), [InboxAlly](https://docs.inboxally.com/support/microsoft-outlook-changes-for-bulk-senders-in-2025)).
  - Competitor prices: dmarcian Basic $24/mo, Plus $240, Enterprise $600, with a free personal tier ([dmarcian](https://dmarcian.com/pricing/)). Postmark DMARC Digests is $14/domain/mo ([Palisade](https://www.palisade.email/postmark-dmarc-alternative)). EasyDMARC has an MSP program with quoted pricing ([EasyDMARC MSP](https://easydmarc.com/pricing/easydmarc/msp)).
- **Why not #1:**
  - The space is very crowded, with many funded vendors running programmatic comparison pages (suped.com, palisade.email, dmarcreport.com).
  - Free tiers anchor SMB prices low.
  - The SEO channel is weakened by AI Overviews.

### 3. Entra ID app-secret and certificate expiry monitor for MSPs (score 25)
- **Buyer:** MSPs and M365 admins. Expired app-registration secrets break integrations silently.
- **Offer:** A multi-tenant app (admin consent, Graph read-only) that alerts at 60/30/7 days and posts to a PSA, Teams, or a webhook.
- **Price:** $29-99/mo per MSP (est.).
- **Stack:** Cloudflare Workers + D1 + Cron, Resend, and Lemon Squeezy.
- **Acquisition:** Microsoft Marketplace/AppSource listing, plus SEO for "client secret expiry alert".
- **Evidence:**
  - Paid tools cover this inside larger suites: Turbo360 ([blog](https://turbo360.com/blog/azure-app-registration-client-secret-expiration-notification-monitoring)), Site24x7 ([docs](https://www.site24x7.com/help/azure/entra-id-monitoring.html)), PIM.Plus ([kb](https://kb.pim.plus/docs/event-monitors/microsoft-azure-event-monitors/entra-id-app-registration-event-monitor)).
  - DIY scripts are common ([demiliani](https://demiliani.com/2022/01/28/azure-ad-app-registration-secrets-a-quick-script-to-check-who-expires-soon/)). Vigil Key Vault expiry monitor is flat $49 ([Capterra](https://www.capterra.in/software/1106983/Key-Vault-Expiry-Monitor)).
- **Risks:**
  - Holding Graph tokens for many tenants is a security-trust burden.
  - MSPs buy on trust and referrals, which means outreach this owner can't do.
- **Better use:** make it a phase-2 module of #1.

### 4. SSL/domain/DNS-change monitor for MSPs and agencies (score 24)
- **Price benchmark:** TrackSSL is free for 2 certs, with paid tiers of about $19/$39/$79/$149 per month per third-party listings ([SoftwareFinder](https://softwarefinder.com/cybersecurity/trackssl), [TrackSSL](https://trackssl.com/)).
- **Stack gotcha:** Workers can't inspect certificates (est.). Options are GitHub Actions cron (2,000 free minutes/month on private repos) or an always-free VM, which adds reliability risk.
- **Acquisition:** SEO plus a free checker tool.
- **Verdict:** Proven willingness to pay, but crowded, and the owner would have to run the SEO channel. Its engine overlaps with #1, so it can be sold standalone later.

### 5. Chrome extension with a paid tier (score 23)
- **Offer:** A browser tool for IT admins, for example a DNS/headers/cert inspector with saved checks and alerts.
- **Price:** $3-5/mo (est.).
- **Stack:** ExtensionPay + Stripe ([ExtensionPay](https://extensionpay.com/articles/extensionpay-is-the-chrome-web-store-payments-replacement)).
- **Acquisition:** Chrome Web Store search.
- **Problem:** Low ARPU means about 600-1,000 paying users are needed (est.). Consumer-style WTP and many free alternatives.

### 6. Cron/heartbeat monitoring (score 22)
- **Benchmarks:** Healthchecks.io has a free tier of 20 checks and Business at about $20/mo ([Capterra](https://www.capterra.ca/reviews/1028488/healthchecksio)). Cronitor is about $21-25/mo, and Dead Man's Snitch about $5-49 ([cron-crew comparison](https://cron-crew.pages.dev/blog/pillar-cron-monitoring-pricing-compared)).
- **Risk = 1:** Search results are full of fresh clones (cronpeek, cronsignal, cronping, cron-crew).

### 7. "CVEs for your stack" alerts (score 22)
- **Context:** The NVD data is free. OpenCVE offers a free plan plus paid cloud plans ([OpenCVE](https://opencve.io/)), and NotCVE also sells plans ([NotCVE](https://notcve.org/pricing/)).
- **Verdict:** A strong free incumbent caps willingness to pay.

### 8. Freemium WordPress plugin via Freemius (score 22)
- **Pros:** wp.org gives real organic distribution.
- **Cons:** About 10% all-in fees ([Freemius](https://freemius.com/wordpress/pricing/)), and the wp.org support forum load is the highest of any option, which conflicts with "fully automated".

### 9. Paid utility API on Rapid (score 22)
- **Cons:** 25% fee ([Rapid docs](https://docs.rapidapi.com/docs/payouts-and-finance)) on a commodity product with low ARPU.

### 10. Shopify app (score 21)
- **Pros:** 0% revenue share on the first $1M lifetime ([Shopify](https://shopify.dev/changelog/update-to-shopifys-app-developer-revenue-share)) and real App Store traffic.
- **Cons:** It needs external hosting (Vercel Hobby is not allowed), a strict review, and high merchant support volume. The owner's IT edge is weaker here.

### 11. Third-party SaaS status aggregator (score 21)
- **Benchmarks:** IsDown is about $27-179/mo ([Capterra](https://www.capterra.co.uk/software/1031094/isdown)). StatusGator is $89-399/mo per a 2026 roundup ([DEV](https://dev.to/shibley/7-best-isdown-alternatives-in-2026-after-the-price-hike-dj3)).
- **Verdict:** Proven model, but the incumbents' head start in programmatic SEO is insurmountable at 5 hrs/week.

### 12. Programmatic SEO plus recurring affiliates (score 18)
- **Verdict:** Slowest to first $. It depends entirely on Google amid AI-Overview CTR losses ([ppc.land](https://ppc.land/google-ai-overviews-reduce-organic-ctr-61-paid-traffic-68/)) and carries scaled-content policy risk.

---

## Decision
- **Pick:** #1, the Forge expiry/renewal app for Jira Service Management. Plan: `workspace/plan-jira-expiry-guard.md`.
- **Why:** It is the only candidate where:
  - **(a)** the channel already exists and costs nothing to operate (Marketplace search),
  - **(b)** billing, tax, and hosting are handled by the platform at $0 (0% revenue share and the Forge free allowance), and
  - **(c)** buyers are businesses used to paying for add-ons.

  It also fits the owner's IT background.
- **Runner-up:** #2 DMARC monitoring. Revisit only if #1 fails its research gate or its 9-month kill criterion.
- **Phase-2 module:** #3 Entra secrets, folded into #1 rather than built as a separate business.
- **Gate before build:** research-assistant must verify competitor installs, prices, and reviews on the two existing Marketplace apps, and the Forge egress/TLS capability (see plan, Week 1).

---

# Opportunity slate #2: owner's three-way comparison (2026-11-06)

Prepared by: vice-president. I did the business-development sourcing and cfo math in this pass; there was no Agent access. The owner asked for a side-by-side of A (restock alerts), B (legal YouTube Shorts: i = paid clipping, ii = faceless AI channel) and C ("copy and improve" apps). Constraints are unchanged: technical/IT owner, 5 hrs/week, $0 up front, fully automated, $3k/month recurring.

**Research limits for this pass**
- walmart.com, reddit.com and whop.com are blocked. `marketplace.atlassian.com` also failed in WebFetch this session (`ENOTFOUND`). Atlassian numbers come from the shell-verified table in `workspace/research/jira-expiry-guard.md` (2026-11-03).
- Tag **[S]** = search-snippet only, not a page read. Tag **(est.)** = vice-president estimate.
- Product and competitor lists for A belong to research-assistant's `workspace/research/out-of-stock-products.md`. They are not repeated here.

## Scores (same rubric: 1-5 each, 5 = good, max 35)

| # | Candidate | Demand | WTP | Auto | Time | Cost | Edge | Risk | **Total** |
|---|---|---|---|---|---|---|---|---|---|
| C | Copy-and-improve: B2B marketplace app. Best target is the Forge **renewals and reminders register** for Jira/JSM | 4 | 4 | 4 | 2 | 5 | 4 | 3 | **26** |
| B(i) | Paid clipping campaigns (owner works as a clipper) | 4 | 2 | 1 | 4 | 4 | 1 | 2 | **18** |
| A | Restock-alert paid Discord/Telegram plus affiliate links | 4 | 3 | 2 | 3 | 2 | 3 | 1 | **18** |
| B(ii) | Automated faceless AI Shorts channel (original content) | 3 | 1 | 4 | 1 | 3 | 2 | 1 | **15** |

## Side-by-side economics and operations

| | A. Restock alerts | B(i). Clipping | B(ii). AI Shorts | C. Renewals register (Forge) |
|---|---|---|---|---|
| Realistic automation | **Low to medium.** Monitors break whenever a retailer changes its site or bot defences. A Discord community needs moderation, refunds and "why did I miss it" support. | **None.** Each clip is hand-picked, edited, captioned and posted. Income scales only with hours worked. | **Medium.** Script, TTS, stock footage and upload can be piped together. Human input is still needed to avoid the "inauthentic content" demonetisation. | **High.** Atlassian hosts the app, bills, collects and handles tax. Forge scheduled triggers do the work. Only async support remains. |
| Hours/week after launch | 5-10 (est.), which is over budget | All 5, with output capped by those hours | 2-4 for QA and topic work (est.) | 0.5-1 for support, plus a few hours a quarter for updates (est.) |
| Time to first $ | 1-3 months. A paid tier needs an audience first, and the owner has none. | 1-4 weeks, if a clip clears a campaign's minimum-view threshold | 6-18 months. The YPP ad-revenue gate is 1,000 subscribers plus 4,000 watch hours, or 10M Shorts views in 90 days [S] ([vidIQ](https://vidiq.com/blog/post/monetize-youtube-guide/), [SEJ](https://searchenginejournal.com/youtube-shorts-monetization-how-revenue-sharing-works/478652/)). | About 8-12 weeks: 4 weeks to build plus Marketplace review. First $ around Feb-Mar 2027 (est.). |
| Price / rate | Paid groups charge about $6-25/mo [S] ([Plugged Inn/Whop review page](https://sites.google.com/view/whopreviews/pluginn), [Lunchmoney](https://sites.google.com/view/whopreviews/lunchmoney)). Walmart affiliate pays 1-4% by category (electronics/games 1%), with a short cookie (3 days per one source) [S] ([argil](https://argil.ai/blog/walmart-affiliate-program-cd8f1), [nichepursuits](https://www.nichepursuits.com/walmart-affiliate-program/)). | Median about **$1 per 1,000 views**, with a range of about $0.20-6. Reported 7% platform fee on payouts. Each clip has a minimum payout and a cap [S] ([builtbyfoundry](https://www.builtbyfoundry.io/blog/what-is-clipping-1-dollar-per-1000-views-50-campaigns), [opus.pro](https://www.opus.pro/blog/whop-content-rewards), [Whop docs](https://docs.whop.com/manage-your-business/growth-marketing/content-rewards)). | Shorts RPM about **$0.03-0.07 per 1,000 views** (wider range $0.01-0.30). Creators get 45% of the pooled revenue [S] ([vidIQ](https://vidiq.com/blog/post/youtube-shorts-monetization/), [shortsync](https://www.shortsync.app/resources/how-much-do-youtube-shorts-pay-2026)). | Atlassian per-user tiers. Comparable asset/licence apps charge **$562.50-712.50/yr at 25 users** and $2,250-2,850/yr at 100 users. Reminder apps charge **$87.50-100/yr at 25 users** (verified Marketplace API pull, `research/jira-expiry-guard.md`). 0% revenue share on Forge until $1M. |
| Fees | Whop about 3% + 2.7% + 30c (6-7% all-in) [S] ([dodopayments](https://dodopayments.com/blogs/whop-fees-explained)). Discord Server Subscriptions take 10%, **US-based owners only** [S] ([Shacknews](https://www.shacknews.com/article/133327/discord-server-subscription-revenue), [Discord](https://discord.com/blog/server-and-creator-subscriptions)). | About 7% [S] | YouTube keeps 55% of the Shorts pool | 0% (Forge, eligible) |
| **Needed for $3k/mo** | **About 330 members at $10/mo**, or 220 at $15, net of about 8% fees. Affiliate-only would need **$75k-300k/mo in Walmart sales** at 1-4%. | **About 3.2M paid views every month**, net of the 7% fee, and it has to be re-earned from new campaigns each month | **About 43M-100M monetised Shorts views every month** from ads alone | **About 120 paying sites at about $25/mo blended** (est.). That is roughly 1,000-1,400 cumulative installs at 8-12 installs per paying site (est.). |
| Is it recurring? | Yes (memberships) but churn is high: demand is hype-driven and tied to drops (est.) | **No.** It is piece-rate work, and campaign budgets run out. | Partly. Ad revenue follows views, which decay. | Yes. Annual and monthly Marketplace subscriptions renew automatically. |
| Odds of $3k/mo within 12 months (est.) | ~3% (compliant version) | ~2%, and it would not be passive | ~1-2% | ~10% (25-30% within 24 months) |

## Platform and legal risks

**A. Restock alerts (Risk = 1)**
- **ToS:** Walmart's Terms of Use reportedly require *express prior written consent* for any automated or manual tool used to scrape or gather site materials, with no small-scale exception [S] ([ConductAtlas summary](https://conductatlas.com/platform/walmart/walmart-terms-of-use/prohibition-on-automated-data-scraping/)). Our rules ban ToS-violating scraping, so **a Walmart page monitor is excluded unless Walmart grants API access.**
- **Compliant data paths are gated:**
  - The Walmart affiliate API (Walmart I/O) requires an application and approval [S] ([webscraping.ai FAQ](https://webscraping.ai/faq/walmart-scraping/can-i-use-walmart-s-api-instead-of-scraping-the-site)).
  - The Best Buy Developer API exists, but commercial use reportedly needs Best Buy's approval, caching is restricted, and gaming titles are excluded unless you have an affiliate or signed agreement [S] ([Best Buy API terms](https://developer.bestbuy.com/legal)).
- **Cost:** Retailer bot defences mean that, in practice, competitors pay for proxies and servers, which breaks the $0 rule (est.).
- **Competition:** Free Discord servers have 20k-67k members [S] ([tcgdropradar](https://tcgdropradar.com/), [pagecrawl](https://pagecrawl.io/blog/pokemon-tcg-restock-new-set-drop-alerts)). Free apps such as HotStock and NowInStock, and retailers' own "notify me" buttons, already exist [S] ([visualping](https://visualping.io/blog/walmart-in-stock-alerts)).
- **Reputation:** Some buyers see paid alert groups as scams [S]. Groups also face pressure to add auto-checkout bots, which are a ToS problem and which we would refuse.
- **Payout and tax:** Affiliate income is taxable. Discord Server Subscriptions are US-only [S].

**B(i). Clipping (Risk = 2)**
- **Copyright is fine** when the creator authorises the campaign.
- **Platform and payout risks:**
  - Short-form platforms may throttle new accounts that post many similar clips.
  - Campaign budgets end without notice, and the campaign owner can reject submissions.
  - Views must be organic. Buying views is fraud, and we will not do it.
- **Fit:** It breaks the owner's "fully automated, no client services" rule. It is a gig, not a business asset.

**B(ii). Faceless AI Shorts (Risk = 1)**
- **Policy:** YouTube's July 15, 2025 "inauthentic content" update targets mass-produced, repetitive content. AI is allowed, but monetisation needs meaningful human input [S] ([Net Influencer](https://www.netinfluencer.com/youtube-clarifies-july-15-policy-update-repetitious-content-rebranded-as-inauthentic-content/), [The Week](https://www.theweek.in/news/sci-tech/2025/07/10/youtube-rolls-out-new-rules-to-curb-ai-content-who-is-affected-and-who-is-safe.amp.html)). A fully automated channel is exactly what the policy targets.
- **Disclosure:** Realistic synthetic content must be labelled.
- **Monetisation gate may rise:** One report says the Shorts threshold may rise to 20M views/90 days from Feb 2027. Sources conflict and this is unverified [S] ([lilachbullock](https://www.lilachbullock.com/youtube-shorts-monetisation-requirements-explained/)).
- **Cost:** LLM and TTS APIs cost money beyond small free tiers.

**C. Renewals register on Forge (Risk = 3)**
- **Platform dependence:** Atlassian's 0% revenue share is temporary [S], and Forge has charged for usage since Jan 2026.
- **Free substitutes:** Native Jira Automation and JSM Assets recipes do part of the job.
- **Ranking:** Marketplace ranking is opaque.
- **IP:** Copy features only. No code, names, screenshots or copy from competitors. Avoid "Jira" at the start of the app name (trademark).
- **Low legal risk otherwise.**

## C: specific "copy and improve" targets

| # | Store | Target app (verify live) | Installs/users | Price | Review complaints | Our improved version | Fit |
|---|---|---|---|---|---|---|---|
| C1 | Atlassian | **License Manager: Domain and SSL Cert Expiry** (Softlist) plus the asset/licence category | 94 installs, 3.75 (6 reviews). **Category comparables: IT Assets & License (devsamurai) 1,541 installs, 4.72; Asset Management for Jira (conelike) 1,350 installs, 4.38** (verified API pull, 2026-11-03) | License Manager is free for ≤10 users, $137.50/yr at 25 users, $550/yr at 100. Asset apps are $562.50-712.50/yr at 25 users. | A review says it "does not work". A Community thread reports missed notifications and ccTLD gaps [S] ([App Central](https://community.atlassian.com/t5/App-Central/Monitor-Domain-amp-SSL-Certificate-Expiry-from-Jira/ba-p/1978551)) | **Renewals register:** SaaS subscriptions, licences, contracts, warranties, domains (RDAP) and certs. Tracks **cancel-by/notice deadlines** and annual cost. Auto-creates Jira/JSM work items, and shows a visible delivery log so no reminder is silently missed. | **Best.** Highest price point in the slate, and it fits the owner's IT background. |
| C2 | Atlassian | **My Reminders for Jira** (free, Atlassian Labs) and the paid **Reminder for Jira** (teamlead) | My Reminders: 3,427 installs, **3.5-3.55 (79 reviews)**. Teamlead: 1,177 installs, 4.53 (32) | My Reminders is free. Teamlead is $20/yr at 10 users, $87.50 at 25, $350 at 100. | Saved reminders "never produced an email" [S] ([Community thread](https://community.atlassian.com/forums/Jira-questions/My-Reminders-for-Jira-not-sending-reminder-emails/qaq-p/2629172)) | Reliable relative/recurring reminders on any date field, with a delivery log. **Same engine as C1**, so it can be a second listing from one codebase. | Strong, as a sister app |
| C3 | Chrome Web Store | **ModHeader: Modify HTTP headers** | 800k-900k users, **rating about 3.0-3.2 from about 1,100 ratings** [S] ([extscope](https://extscope.org/extension/idgpnmonknjnojddfkpgkljpfnnfcklj)) | Free, ad-supported. Paid from about $2/mo [S] ([toolradar](https://toolradar.com/tools/modheader)) | Ad injection ("ADWARE"), pop-up tabs, login required for paid features [S] ([Requestly comparison, a competitor page](https://requestly.com/modheader/), [Firefox reviews](https://addons.mozilla.org/ru/firefox/addon/modheader-firefox/reviews/)) | A no-ads, no-login, privacy-first header tool with a small paid tier for profile sync | Medium. Huge funnel, but WTP is about $2/mo, free rivals (Requestly, Postman) exist, and it would need about 1,500 payers |
| C4 | Shopify | **Back-in-stock alert apps** (Swym, Notify!, Stok). This is the legal, merchant-side version of idea A. | Leader "Notify Me!" has 3,894 reviews at 4.9. Weaker apps carry 1-star clusters [S] ([appnavigator](https://appnavigator.io/app/watchlist/)) | From about $14.99/mo [S] ([digismoothie](https://digismoothie.com/app/back-in-stock-product-alerts)) | Notifications not sent, slow inventory sync, price hikes, push to $200+/yr plans, billing disputes [S] ([Shopify reviews 1966276](https://apps.shopify.com/reviews/1966276), [1374650](https://apps.shopify.com/reviews/1374650), [1451311](https://apps.shopify.com/reviews/1451311)) | A simple, reliable, cheap flat-price app | Weak to medium. Crowded, with a 4.9 leader. Needs external hosting and email sending (Resend free tier is 100/day). Merchant support load is high. |
| C5 | Chrome/Firefox | **Distill Web Monitor** | Users not verified | From $15/mo [S] ([Software Advice](https://www.softwareadvice.com/website-monitoring/distill-profile)) | "Too expensive", "getting more restrictive", billing complaints; the Firefox build is called abandoned [S] ([AMO reviews](https://addons.mozilla.org/en-US/firefox/addon/distill-web-monitor-ff/reviews/?page=1)) | A cheaper change monitor | Weak. Commodity product (changedetection.io, Visualping), and a ToS grey zone depending on the sites users monitor |

## Decision (slate #2)
- **Pick: C, via target C1 (with C2 as its sister listing).** The plan is `workspace/plan-renewals-register.md`. It **supersedes** `plan-jira-expiry-guard.md`: same platform and spike, broader offer, higher price anchor.
- **Why C wins:**
  - It is the only option where billing, hosting and discovery are run by the platform at $0.
  - Buyers are businesses that already pay $87-2,850/yr for this type of add-on.
  - It is genuinely automated after launch, and the owner's IT skills are the moat.
- **Why A, B(i) and B(ii) are rejected:**
  - **A as specified** (Walmart monitoring) conflicts with Walmart's ToS and our no-scraping rule. A compliant version depends on gated retailer APIs, needs an audience we don't have, and competes with free 20k+ member servers.
  - **B(i)** is not recurring and not automated.
  - **B(ii)** needs about 43-100M Shorts views/month for $3k and runs straight into the inauthentic-content policy.
- **Revisit triggers:**
  - A: only if Walmart or Best Buy grants written commercial API access.
  - B: not planned.
  - C4 (Shopify back-in-stock): a possible later sister product if C1 succeeds.
- **Candid odds for C (est.):**
  - About 50% chance of some MRR within 6 months of listing.
  - About 10% chance of $3k/mo within 12 months.
  - About 25-30% within 24 months, most likely via 2-3 listings on one codebase rather than one app. Even the category leaders' installs (about 1,350-1,550) imply roughly $2-5k MRR each (est.), so $3k from a single new app is a stretch.
