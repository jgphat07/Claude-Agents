# Plan: Jira Expiry Guard (working name)

Status: SUPERSEDED on 2026-11-06 by `workspace/plan-renewals-register.md` (broader renewals register, same Forge platform). Kept for history.
Owner of plan: vice-president. Created 2026-11-03. Source scoring: `workspace/opportunities.md` (#1, 26/35).

Numbers marked (est.) are vice-president estimates, not sourced facts.

## 1. Offer
A Forge app for Jira Cloud / Jira Service Management that keeps a register of everything that expires and **turns upcoming expirations into Jira tickets automatically**.

**MVP (sellable within the first 20 hours):**
- Admin page to add items: domains, TLS endpoints, and manual items (software licenses, contracts, warranties) with an expiry date and owner.
- Daily scheduled check:
  - Domain expiry is pulled automatically via RDAP.
  - TLS expiry is pulled automatically **if the Week-1 spike proves Forge can do it**. Otherwise TLS is entered manually in v1.
- At 30/14/7/1 days before expiry, the app creates or updates a Jira issue or JSM request in a chosen project, with deduplication.
- Simple overview page sorted by "expires soonest".

**Phase 2 (only after the first paying customers):**
- Entra ID app-secret and certificate expiry via Microsoft Graph (opportunity #3).
- Bulk CSV import.
- Asset links to JSM Assets.

**Not in scope:** anything that needs us to touch customer systems by hand, calls, onboarding sessions, or custom work.

## 2. Buyer
IT/ops teams and MSPs already paying for Jira Cloud or JSM. These are companies used to buying Marketplace add-ons. The sites that pay are those with more than 10 users, since 1-10 users are free by Marketplace convention.

## 3. Price (cfo to finalize after the research gate)
- **Billing:** paid via Atlassian, with Atlassian's per-user tier model.
- **Tiers:** free for 1-10 users. Paid tiers start at 11 users, priced **at or slightly under the two existing competitors** once their pricing tabs are verified.
- **Working assumption:** blended **ARPU of about $30 per paying site per month (est.)**.
- **Revenue share:** 0% on eligible Forge earnings until $1M lifetime ([Atlassian, 2026](https://www.atlassian.com/blog/developer/updates-to-marketplace-revenue-share-2026)). Atlassian handles billing and sales tax, so there are no Stripe or merchant-of-record fees.

### Customers needed for $3,000 MRR
| Blended ARPU (est.) | Paying sites needed |
|---|---|
| $20 | 150 |
| **$30 (base)** | **100** |
| $50 | 60 |

**Funnel assumption (est., to be replaced with real data):** about 10-15 installs per paying site. Many installs are free 1-10 user sites or trials that lapse. So **roughly 1,000-1,500 cumulative installs** are needed for 100 paying sites.

## 4. Free stack
| Need | Choice | Cost | Gotcha |
|---|---|---|---|
| Hosting/compute | Forge functions | $0 within the per-app monthly free allowance | Usage-based since Jan 2026. Dev-environment usage counts. Atlassian advises a payment method on file. **No Forge LLM or Containers** (no free allowance) ([Atlassian](https://www.atlassian.com/blog/developer/updates-to-forge-pricing-effective-january-2026), [Forge pricing](https://developer.atlassian.com/platform/forge/forge-platform-pricing/)) |
| Database | Forge storage (KVS / entities) | $0 within allowance | Check quotas ([Forge limits](https://developer.atlassian.com/platform/forge/platform-quotas-and-limits)) |
| Scheduling | Forge scheduled triggers | $0 | Verify minimum interval and quotas |
| Payments/licensing | Paid-via-Atlassian. The app checks the license context | 0% revenue share | Must stay pure Forge (no Connect modules) to keep the 0% rate |
| Email/alerts | Jira issue notifications | $0 | No email provider needed in the MVP |
| Docs, privacy policy, support page | GitHub Pages (`<user>.github.io`) or a free Confluence site | $0 | Required for the Marketplace listing |
| Support inbox | Free email or a free JSM service desk | $0 | Async only. State this on the listing |
| Dev site | Free Atlassian Cloud developer site | $0 | |

**Vercel, Supabase, and Stripe are not needed.** That avoids the Vercel Hobby commercial-use ban and Supabase's inactivity pauses.

## 5. What the owner builds in the first ~20 hours (4 weeks x 5 h)
**Week 1 (5 h): gate + spike**
- (1 h) Owner, after approving account creation: create an Atlassian developer account and a free cloud dev site, install the Forge CLI, and deploy the hello-world app.
- (2 h) **Technical spike**, answering three questions:
  - (a) Can a Forge backend `fetch` arbitrary customer-supplied hosts? Check the egress permission/wildcard rules.
  - (b) Can it read a TLS certificate's `notAfter` (Node `tls` in the Forge runtime)?
  - (c) Does an RDAP lookup work for .com/.net/.org/ccTLDs?

  Write the results to `workspace/build/jira-expiry-guard/spike.md`.
- (2 h) Data model plus admin page skeleton (UI Kit).
- **Gate:** research-assistant's competitor report (task R1) plus the spike results go to the vice-president, who decides go / reshape / switch to the runner-up.

**Week 2 (5 h):** CRUD for items; daily scheduled trigger; RDAP domain-expiry fetch; TLS check if the spike passed.

**Week 3 (5 h):**
- Issue/JSM request creation at thresholds, with deduplication and per-project settings.
- License-context gating so that paid features require an active license.
- Error handling and logging. Keep usage inside the free allowance by batching, with one daily run per site.

**Week 4 (5 h):**
- Listing assets: name, icon, 3 screenshots, docs page, privacy policy, and the data-residency/security questionnaire.
- Pricing tiers (cfo).
- Submit the paid listing for review. Approval time is unknown (est. 1-4 weeks). research-assistant to verify.

## 6. Acquisition (no ads, no daily effort)
1. **Marketplace listing SEO.** A keyword-rich title and description built around the words buyers actually search ("SSL certificate expiry", "domain expiration", "license renewal reminders").
2. **"Free up to 10 users" filter** for discovery. Paid tiers start at 11 users.
3. **Atlassian Community answers.** Write a one-time, genuinely helpful answer on the existing "expiry reminder" threads, disclosing that we're the vendor, plus one App Central article. The owner must approve each post, and there is no spam.
4. **Docs pages on GitHub Pages** that double as long-tail search pages.
5. **Later:** a Data Center version is out of scope. A JSM Assets integration would widen reach.

## 7. Timeline to $3k MRR (all est.)
The app could be live on the Marketplace around early-to-mid January 2027 if build and approval go smoothly.

| Scenario | First $ | $1k MRR | $3k MRR |
|---|---|---|---|
| Optimistic | Feb 2027 | ~Jul 2027 | ~Nov 2027 (about 12 months) |
| Base | Mar-Apr 2027 | ~Q1 2028 | ~Q3 2028 to Q2 2029 (20-30 months) |
| Conservative | Mid 2027 | Maybe never | Not without a second app or a pivot. Plateau of $200-800 MRR |

**Candid odds (est.):**
- About 50% chance of any recurring revenue within 6 months of listing.
- About 10% chance of $3k MRR within 12 months.
- About 25-30% chance within 24 months.

At 5 hrs/week with $0, the realistic path to $3k is **this app plus one or two sister Forge apps** built on the same codebase, each adding $500-1,500 MRR, rather than one app alone.

## 8. Kill / iterate criteria
- **Research gate (Week 1):**
  - If either competitor shows clear dominance (est. 2,000+ installs with strong recent reviews) and we can't name a differentiator, reshape the niche (e.g. lead with Entra secrets).
  - If the Forge spike fails both TLS and arbitrary-host fetch, reshape around manual items + RDAP, or switch to the runner-up (DMARC).
- **90 days after listing:** fewer than 30 installs means rewriting the listing and keywords once. Fewer than 30 installs again 60 days later means kill.
- **9 months after listing:** below $300 MRR means kill, or pivot the codebase to a sister app.
- **Cost:** if Forge usage exceeds the free allowance before $200 MRR, re-architect or kill. **Never let costs exceed revenue.**
- **Time:** if support takes more than 1 hr/week before $1k MRR, cut features or simplify. If it takes more than 2 hrs/week at any point, revisit.

## 9. Task list
| ID | Task | Owner | When | Needs owner approval? |
|---|---|---|---|---|
| R1 | Verify both competitor listings (apps 1227641 and 1235426): installs, price tiers, review themes and complaints, Forge vs Connect. Also confirm the Forge revenue-share and pricing terms on atlassian.com. **Requires allowing marketplace.atlassian.com and www.atlassian.com in session network settings** | research-assistant | Week 1 | No |
| R2 | Collect 20+ Atlassian Community threads asking for expiry/renewal reminders, with URLs, as demand evidence and future answer targets | research-assistant | Week 1 | No |
| R3 | Find the Marketplace paid-app review requirements and typical approval time, plus the partner/payout prerequisites (tax forms, bank) | research-assistant | Week 1 | No |
| V1 | Go/reshape/switch decision after R1 + spike | vice-president | End of Week 1 | No |
| O1 | Create Atlassian developer account + free dev site, install Forge CLI | OWNER | Week 1 | **Yes (account creation)** |
| O2 | Technical spike (egress, TLS, RDAP) and write `spike.md` | OWNER | Week 1 | No |
| O3 | Build the MVP (Weeks 2-3 scope above) | OWNER | Weeks 2-3 | No |
| B1 | Write the functional spec and differentiation vs the 2 competitors, based on R1 complaints, in `workspace/build/jira-expiry-guard/spec.md` | business-development | Week 1-2 | No |
| B2 | Draft listing copy: title, tagline, highlights, keywords | business-development | Week 3 | No |
| C1 | Pricing tiers from R1 benchmarks, with ARPU and customers-needed table | cfo | Week 2 | No |
| C2 | Confirm the Forge free allowance against projected usage per site (est. one daily run); set a cost alarm | cfo | Week 3 | No |
| C3 | Tax flags: Marketplace payouts are income; tax forms; whether a sole proprietorship is fine. Create `workspace/metrics.md` (installs, paid sites, MRR, support min/week) | cfo | Week 4 | No |
| M1 | Name and brand check (no trademark clash with Atlassian marks), icon, 3 screenshots, docs site structure | marketing-social-media-manager | Week 3 | No |
| M2 | Draft one App Central article and 5 helpful Community answers with vendor disclosure. **Not posted** until the owner approves each one | marketing-social-media-manager | Week 4+ | **Yes (publishing)** |
| O4 | Create Marketplace partner profile, privacy/docs page on GitHub Pages, submit listing | OWNER | Week 4 | **Yes (account + publishing)** |
| V2 | First weekly review in `workspace/reviews/<date>.md`, then weekly | vice-president | Weekly | No |

## 10. Unavoidable costs
- **None required.** Forge, the Atlassian dev site, GitHub Pages, and Marketplace billing are all $0 at our scale.
- **Possible costs:**
  - A payment method on file for Forge in case of overages (should be $0 at low usage).
  - A custom domain for credibility, about $10-15/yr. Optional, after first revenue.
  - Income tax on payouts.
