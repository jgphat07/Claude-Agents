# Restock-Alert Subscription (Walmart + other retailers): Research Brief

*Research Assistant, 2026-11-06. Network note: walmart.com, reddit.com, whop.com and developer.bestbuy.com could not be fetched in this session. **Almost every fact below comes from WebSearch result snippets, not full pages I read myself.** Many of the sources are affiliate/SEO review sites. Each one is labelled. Verify anything load-bearing before building.*

---

## 1. Verdict: TEST FIRST (leaning NO-GO as a $3k/mo vehicle)

| Factor | Finding | Effect |
|---|---|---|
| Demand | Real and loud, especially for Pokémon TCG (sources in §3) | + |
| Price ceiling | Paid groups charge $2.99 to $9.99/mo, and big free options exist (§4) | – |
| Affiliate upside | Walmart pays roughly 1 to 4% on toys/games. Video game hardware may pay 0% (§6) | – |
| Clean data access | Walmart scraping is prohibited. Whether the Walmart Affiliate API returns stock status is **unconfirmed**. Best Buy has an official API with availability data (§5) | – (Walmart), ± (Best Buy) |
| Product reality | Bots win online drops within seconds. Walmart moved hot Pokémon items to a random **Collectibles Drawing** in 2026, which makes speed alerts worth less there (§3) | – |
| Owner fit | Needs about 430 to 500 paying subs at $6 to $7 to reach $3k/mo (estimate: $3,000 ÷ ~$6.50 net). Members complain when they miss a drop, which creates support load. No audience, no ads budget | – |

**Bottom line:** As a Walmart-focused paid alert group, the idea is weak. The niche is crowded and cheap, Walmart's data can't be legally sourced in an automated way (as far as this research could confirm), and Walmart has partly replaced first-come drops with lotteries. The only version worth testing is narrow and uses compliant data only.

**Cheapest validation test (costs $0, but publishing/posting needs owner OK):**
1. Build a free Discord bot/webhook that polls only the **official Best Buy Products API** (needs a free key, limits 5 req/s and 50k/day) for one watchlist. Add a **Walmart Collectibles Drawing / drop-calendar** channel built from public announcements. No Walmart scraping.
2. Run it free for 3 to 4 weeks with a waitlist-style "Pro tier" button that shows $4.99/mo.
3. **Success threshold:** at least 300 free members and at least 5% clicking or committing to Pro (15 or more) within 30 days, plus at least $25 in affiliate commissions reported in Impact or Best Buy. If you miss all three, kill it. *(These thresholds are my estimates, not benchmarks from a source.)*

**Niches to start in, if tested:** (1) **Pokémon TCG** (the biggest and loudest community, though also the most saturated) and (2) **Best Buy-sourced tech drops** (GPUs, Switch 2 bundles), because that's where a compliant official API exists.

---

## 2. Buyer and where they gather

- **Buyers:** collectors and parents who want MSRP (not resale) prices, plus small resellers. The reseller groups are pricier: one review lists "Friends and Family" at $60/mo ([review site, snippet](https://friends-and-family-community-review.pages.dev/)).
- **Where they gather (snippet-level evidence):**
  - Discord: a free "Pokemon Restocks & News" server is reported at 67,400 members ([tcgdropradar, snippet](https://tcgdropradar.com/)). PokeNotify has about 30k to 35k Discord members ([TrackaLacker comparison](https://www.trackalacker.com/articles/news/pokenotify-vs-trackalacker-in-2026), [tcgdropradar](https://tcgdropradar.com/)). The Hive Index lists 17 reselling Discords ([thehiveindex](https://thehiveindex.com/topics/reselling/platform/discord/)).
  - Reddit: r/PKMNTCGDeals appeared in results ([mirror link](https://redlib.belloworld.it/user/smichican)). Reddit itself was blocked, so I have no member counts.
  - X/Bluesky: Wario64 is cited as a go-to free restock account ([platform-8hi blog, low reliability](https://platform-8hi.pages.dev/blog/nintendo-switch-2-restock-predictions)). Matt Swider / The Shortcut is cited for Switch 2 alerts ([theshortcut.com](https://theshortcut.com/p/nintendo-switch-2-restock-get-alerts)).
  - Deal sites cover drawings for free: Hip2Save ([hip2save](https://hip2save.com/?p=12001192)), Slickdeals ([slickdeals](https://slickdeals.net/f/18804424-pokemon-tcg-snorlax-ex-and-blissey-ex-special-collection-box-25-free-shipping)).

---

## 3. Pain evidence (news and petition quotes, snippet-level)

1. Switch 2: "A large Walmart restock on June 6 sold out in 20 minutes" ([Tom's Guide live blog](https://www.tomsguide.com/live/news/nintendo-switch-2-restocks-live-updates-and-news)).
2. Pokémon: "even those with alerts set up for Pokemon TCG restocks couldn't get the cards despite running right to Target's website at 2 AM" ([Comicbook.com](https://comicbook.com/gaming/news/pokemon-tcg-cards-prismatic-evolutions-spc-preorders)). **Alerts alone don't beat bots.** That is a core product risk.
3. A change.org petition by a restock-community owner says "real fans are swiftly wiped out by automated bots" ([change.org](https://www.change.org/p/demand-that-walmart-enforce-bot-protection-for-fair-pokemon-card-purchases-events)).
4. Ascended Heroes (2026) drop "cause[d] mob to kick down security gate" ([Geeks and Gamers](https://geeksandgamers.com/pokemon-mega-evolution-ascended-heroes-drop-cause-mob-to-kick-down-security-gate/)). Pokémon Center ETB preorders sold out ([Wargamer](https://www.wargamer.com/pokemon-trading-card-game/ascended-heroes-pre-orders)).
5. Target "is prepared to call the cops on frantic pokemon card hunters" ([Vice](https://www.vice.com/en/article/target-is-prepared-to-call-the-cops-on-frantic-pokemon-card-hunters/)).
6. Walmart's queue: shoppers "wait 10 - 30 minutes… and by the time your spot comes up, everything is sold out" ([blog, low reliability](https://platform-8hi.pages.dev/blog/pokemon-cards-restock-crisis)).
7. Walmart moved to a lottery, the "Collectibles Drawing" (2026): random selection, one entry per person, free with a Walmart.com sign-in ([TrackaLacker guide](https://www.trackalacker.com/articles/news/walmart-draw-system-guide), [Kotaku](https://kotaku.com/pokemon-tcg-scalpers-walmart-lottery-draw-target-30th-anniversary-2000729942), [Dexerto](https://www.dexerto.com/pokemon/pokemon-fans-now-need-lottery-luck-to-buy-cards-at-walmart-3404656/)). One French outlet's headline says Walmart is ending the lottery ([next-stage.fr](https://www.next-stage.fr/2026/09/attention-walmart-arrete-sa-loterie-pokemon-tcg-voici-pourquoi-cest-fou.html)), but an October drawing was also listed ([Wargamer](https://www.wargamer.com/pokemon-trading-card-game/walmart-lottery-october)). **Its status is unresolved.**

---

## 4. Products that sell out most: ranked by alert-service potential

Ranking is **my judgement (an estimate)**. It weighs restock frequency, how big and how recurring the community is, resale premium, and whether compliant data exists.

| # | Category | Example items | Why it sells out | Resale premium (source) | Restock cadence | Community size / trend |
|---|---|---|---|---|---|---|
| 1 | **Pokémon TCG sealed** | Prismatic Evolutions ETB, Ascended Heroes ETB, 30th-anniversary product | Scalpers plus supply shortfall. One report says 10B cards were printed Mar 2025 to Mar 2026 and "demand still outpaced every press run" ([krainsports blog](https://krainsports.blogspot.com/2026/04/the-evolution-of-botting-in-pokemon-tcg.html)) | $60 ETB at ~$400 resale at peak ([Kotaku](https://kotaku.com/pokemon-tcg-prismatic-evolutions-prices-umbreon-1851747243)). Ascended Heroes $60 vs ~$120 ([FinalBoss](https://finalboss.io/walmart-briefly-sold-ascended-heroes-etbs-for-60)) | Weekly. Claimed Walmart Wednesday ~9pm ET drops ([TrackaLacker](https://www.trackalacker.com/articles/news/walmart-wednesday-pokemon-card-drops), unverified), now partly lottery | Largest. Free 67k Discord, 30k+ paid-group Discords. Rising (30th anniversary) |
| 2 | **GPUs** | RTX 5090 FE ($1,999 MSRP) | Supply-limited | $2,800 to $4,000+, with peaks above $10k ([TweakTown](https://www.tweaktown.com/news/113561/rtx-5090-stock-dries-up-as-prices-soar-past-dollars10000/index.html), [TrackaLacker](https://www.trackalacker.com/articles/news/nvidia-geforce-rtx-5090-restock-and-buying-guide)) | Unpredictable. Best Buy "rarely more than one or two in stock" (TrackaLacker, Jul 2026) | Mid-sized, high-value buyers. **Best Buy API data is available** |
| 3 | **Nintendo Switch 2 / bundles** | Console, GameStop bundles | Launch demand | Not quantified in the sources I found | Frequent in 2025. "Sold out across all major online retailers" as of Mar 2026 ([TrackaLacker](https://www.trackalacker.com/articles/news/nintendo-switch-2-is-sold-out-everywhere)) | Large but episodic. Fades as supply normalizes |
| 4 | **Sports cards (Topps Chrome etc.)** | 2025 Topps Chrome Mega/Value boxes | Retail allocation | Not quantified. Target listings out of stock, NFL Chrome Value Box "196k+ bought in last month" ([Target listing](https://www.target.com/p/2025-topps-mlb-chrome-baseball-trading-card-mega-box/-/A-94827548)) | Irregular retail resets | Big hobby. Evidence here is thin |
| 5 | **Holiday 2026 hot toys** | NeeDoh ("routinely sold out"), KPop Demon Hunters items, Pokémon 30th ([Reviewed](https://www.reviewed.com/gift-guides/features/best-toys-gift-guide), [Today/Toy Insider](https://www.today.com/shop/the-toy-insider-hottest-toys-2026-rcna596659)) | Seasonal spikes | Unknown | Oct to Dec only | Huge but **seasonal, not recurring**. NeeDoh appears in Walmart drawings ([Hip2Save](https://hip2save.com/?p=12001192)) |
| 6 | **Labubu / Pop Mart** | The Monsters series, mini Labubu | Blind-box hype, bots | $15 doll reselling for $120+ (Korea, [Korea Times](https://www.koreatimes.co.kr/amp/lifestyle/trends/20250804/chinese-labubu-character-becomes-craze-in-korea-with-15-dolls-reselling-for-over-120)). Resale fell 10 to 30%, then halved after supply increases ([Jing Daily](https://jingdaily.com/intels/2025-09/08/pop-mart-mini-labubu-resale-prices-drop-30), [Yicai](https://www2.yicaiglobal.com/news/pop-mart-slumps-after-chinese-toymaker-boosts-labubu-supply-causing-resale-prices-to-plunge)) | Pop Mart app-only drops | **Declining.** "plentiful and easy to buy" by holiday 2025 ([Westfield, May 2026](https://goodfest.westfield.com/2026/05/labubus-buying-frenzy-is-cooling-off-new-data-shows/)) |
| 7 | **LEGO retiring sets** | 220 sets retiring (Oct 2026 count) | Retirement, not scarcity at launch | Market average ~6.4%/yr appreciation. Ideas ~12.4% ([BrickEconomy May 2026](https://www.brickeconomy.com/article/lego-market-recap-may-2026), [Oct guide](https://www.brickeconomy.com/article/top-lego-sets-retiring-2026-investment-october)) | Slow, predictable. Fits better as a "last chance/price drop" alert than a restock alert | Investor niche. Low urgency |
| 8 | **Limited sneakers** | (not researched in depth) | Draws and app exclusives | n/a | Brand apps run draws | Mature cook-group market. Evidence here is **thin** |
| 9 | **Stanley / Owala cups** | Target Galentine's / Starbucks Stanley | Limited colorways | $45 to $50 retail vs $200 to $250 resale ([WJHG](https://www.wjhg.com/2024/01/05/stanley-cups-sold-out-target-are-selling-more-than-double-price-resale-market/), [Fox11](https://www.fox11online.com/news/offbeat/limited-edition-galentines-day-stanley-cups-gen-z-fly-off-shelves-resales-hit-250-cosmo-pink-red-valentines-target-tiktok)) | One-off drops. Starbucks said no restock ([Axios](https://axios.com/2024/01/10/stanley-cup-target-starbucks-quencher-valentines-restock)) | **All evidence is from 2024. I found nothing for 2025/26 and nothing on Owala.** Treat as faded |
| 10 | **PlayStation limited editions** | (not found) | n/a | n/a | n/a | **No evidence surfaced.** Thin |

---

## 5. Data access and ToS (the most important section)

| Source | What's allowed (per sources) | Availability data? | Risk |
|---|---|---|---|
| **Walmart.com site** | Terms of Use reportedly bar robots, spiders, scraping and data mining without written consent, and restrict price-tracking bots ([ConductAtlas summary](https://conductatlas.com/platform/walmart/walmart-terms-of-use/provision/CA-P-016603/prohibition-on-automated-data-scraping/)). This is a third-party summary; walmart.com itself was blocked | n/a | **HIGH. Do not scrape.** |
| **Walmart Affiliate program (Impact)** | Free to join, runs on Impact ([affiliates.walmart.com FAQ](https://affiliates.walmart.com/faqs)). One summary says affiliates may not "forward, redistribute, or repurpose the Qualifying Links to any third party" or generate communications using Walmart trademarks ([Cuelinks summary](https://www.cuelinks.com/campaigns/walmart-1-affiliate-program), garbled, **verify**) | **Unconfirmed.** A Walmart.io Affiliate API exists (community wrapper [WIOpy](https://pypi.org/project/WIOpy/) has `product_lookup`). I could not confirm a stock field or its use terms. One plugin doc says "Walmart no longer releases new API keys" ([KeywordRush](https://ce-docs.keywordrush.com/modules/affiliate/walmart), secondhand) | **MEDIUM-HIGH.** Get written OK from Walmart affiliate support before using affiliate data for alerts. Branded "Walmart restock" messaging may conflict with trademark clauses |
| **Walmart Data Ventures API** | "may NOT be used by any competitors of Walmart for … analyzing … pricing or product availability" ([developer.walmartdataventures.com](https://developer.walmartdataventures.com/apis/docs/terms-and-conditions)) | Yes, but this is a different, enterprise program | Not the right path |
| **Walmart Marketplace API** | For sellers. Data use is limited to what the agreement expressly permits ([developer.walmart.com](https://developer.walmart.com/us-marketplace/docs/terms-and-conditions)) | Seller-only | Not applicable |
| **Best Buy Products API** | Free key. Limits of 50k/day and 5/s ([API Evangelist profile](https://apis.io/rate-limits/best-buy/best-buy-rate-limits/)). Caching limited (72 hrs vs "temporary", sources disagree). One aggregator says "commercial use requires partner agreement" ([publicapis.dev](https://publicapis.dev/resource/best-buy/r5o8ufzc)) | **Yes.** Products API covers availability and works with the Stores API for in-store ([Best Buy APIs page](https://developer.bestbuy.com/apis), snippet) | **LOW-MEDIUM.** The cleanest source, but read the full ToS (developer.bestbuy.com needs allow-listing) and confirm whether a paid product counts as commercial use |
| **Target** | Terms (updated Mar 22, 2026) grant a license "for noncommercial purposes only" and reportedly cover "spiders, robots… intelligent agents" ([target.com/terms](https://www.target.com/terms), [ConductAtlas](https://conductatlas.com/platform/target/target-terms-and-conditions/provision/CA-P-076762/prohibition-on-unauthorized-search-tools-and-bots/)). I found no public product/availability API | No official source | **HIGH** for automated monitoring |
| **Amazon** | PA-API v5 is being replaced by the **Creators API**. Offers V1 retired; Offers V2 requires the Creators API. Dates conflict (Jan 31 / Apr 30 / May 15, 2026) ([dev.to](https://dev.to/th3nate/amazon-pa-api-v5-is-shutting-down-april-30-2026-here-is-what-changes-at-the-auth-layer-22ek), [affiliate-toolkit](https://www.affiliate-toolkit.com/affiliate-toolkit-3-8-5-amazon-creators-api-support-why-you-need-to-migrate-before-may-15-2026/)) | Offers data via the API. I did not find restrictions on alert use | **MEDIUM.** Needs an active Associates account. Read the Creators API license |
| **GameStop / Pokémon Center** | Not researched in depth. No public API found | n/a | Assume HIGH |

**Plain flags:**
- A paid service whose only data source is scraping Walmart or Target would rest on a ToS violation. That breaks the team rule.
- Third-party Walmart scrapers sold on Apify, Olostep and Zyla ([Apify](https://apify.com/gauravlabs/walmart-product-api.md), [Olostep](https://www.olostep.com/apis/walmart-product-api)) **do not remove the ToS risk.** They only outsource it.
- Selling or promoting checkout bots is out of scope and reputationally toxic (see the petitions above).

---

## 6. Competitors and pricing benchmarks (for `cfo`)

Most of these figures come from review/affiliate sites, and the sources conflict. I could not fetch Whop listings to confirm them.

| Competitor | Type | Price | Members / traction | Coverage | Monetization | Source |
|---|---|---|---|---|---|---|
| PokeNotify | Discord + app | $7.99/mo, 3 to 7 day trial, no annual plan | ~30k to 35k Discord | 100+ retailers, strong CA/UK/AU | Subscription | [TrackaLacker](https://www.trackalacker.com/articles/news/pokenotify-vs-trackalacker-in-2026), [tcgdropradar](https://tcgdropradar.com/) |
| Poke Alerts | Whop/Discord | $5.99/mo | 23k to 35k+ (conflicting) | Pokémon | Subscription | [tcgdropradar](https://tcgdropradar.com/), [review](https://sites.google.com/view/glowlane452/pokealerts) |
| Emerald Alerts | Whop/Discord | $5.99/mo | n/a | Pokémon | Subscription | [whopreviews](https://whopreviews-six.vercel.app/communities/emerald-alerts) |
| PokeFinder | Whop/Discord | $6.99/mo | n/a | Pokémon | Subscription | [review](https://sites.google.com/view/glowlane452/pokefinder) |
| Shiny Town | Whop/Discord | $7.99/mo | 4.9/5 from 134 reviews | Pokémon | Subscription | [whopreviews](https://whopreviews-six.vercel.app/products/shiny-town-shiny-town) |
| PokePings | Whop/Discord | $8.99/mo | 575+ members | Pokémon | Subscription | [review](https://pokepings-whop-review.pages.dev/) |
| Poke Signals | Whop/Discord | $9.99 or $19.99/mo (conflicting) | n/a | Pokémon | Subscription | [review](https://sites.google.com/view/glowlane452/pokesignals) |
| TrackaLacker | App + site + Discord | **Free core**. Premium $2.99/mo ($28.50/yr). Ultra $5.99/mo ($57/yr) | 288 Trustpilot reviews | Multi-category (TCG, GPUs, Switch 2) | Subs (priority delivery) + affiliate links | [App Store](https://apps.apple.com/us/app/id6708238805), [Trustpilot](https://uk.trustpilot.com/review/trackalacker.com?page=5) |
| HotStock | App | Free. Premium $5.49 and AutoBuy $10.99 IAPs (Mar 2026 snapshot) | n/a | Multi-category | Subscription/IAP | [App Pricing Lab](https://apppricinglab.com/iap/apple/1257690900) |
| NowInStock.net | Website | **Free** (asks "why don't you charge…") | Long-running | Multi-category | Ads/affiliate (inferred) | [nowinstock.net](https://nowinstock.net/support/) |
| The Hobby Bin Discord | Discord | **Free** | n/a | Pokémon | Store traffic | [thehobbybin](https://thehobbybin.com/blogs/pokemon-tcg-guides/pokemon-restock-alerts-discord) |
| "Pokemon Restocks & News" | Discord | **Free** | 67,400 | Pokémon | n/a | [tcgdropradar](https://tcgdropradar.com/) |
| Wario64, Matt Swider (X/Bluesky) | Social accounts | **Free** | n/a | Games, consoles, deals | Not confirmed | [The Shortcut](https://theshortcut.com/p/nintendo-switch-2-restock-get-alerts) |
| Reseller cook groups (Flipfluence, Friends and Family) | Discord | $50 to $60/mo | n/a | Reselling (broader than alerts) | Subscription | [Flipfluence review](https://sites.google.com/view/atlasavenue87/flipfluence), [F&F review](https://friends-and-family-community-review.pages.dev/) |

**Weaknesses I could pull:** PokeNotify's US coverage is reportedly weaker than its international coverage (tcgdropradar). TrackaLacker's free-vs-paid feature descriptions contradict each other. The category-wide weakness is that alerts lose to checkout bots (Comicbook.com quote above). I found no substantial review complaints. **Thin.**

**Pricing takeaway:** the consumer ceiling is effectively **$3 to $8/mo**, and strong free tiers are everywhere. Reseller-focused groups get $50 to $60/mo, but they sell profit methods, not just alerts.

**Platform fees:** Whop reportedly takes 3% plus processing (~2.9% + $0.30), roughly 7% all-in per one source ([schoolmaker](https://schoolmaker.com/blog/whop-pricing.md), [Dodo Payments](https://dodopayments.com/zh/blogs/whop-fees-explained)). Discord native subscriptions are reportedly ~10% plus processing ([cartmango](https://cartmango.com/community-platform-for-creators/)). Both are unverified against official pages.

**Affiliate economics (estimates from blogs; confirm in Impact):** Walmart pays about 1 to 4%. Toys may pay ~4%, video game hardware may pay 0 to 2%, and the cookie is ~3 days ([Niche Pursuits](https://www.nichepursuits.com/walmart-affiliate-program/), [bloggingtips](https://bloggingtips.com/walmart-affiliate-program/)). *Illustrative estimate:* a $60 ETB at 4% earns $2.40. Switch 2 hardware may earn $0. Affiliate income alone can't reach $3k/mo without very high volume.

---

## 7. Demand signals

- **Google Trends / search volume:** **not collected.** The tools weren't reachable this session, so this is a gap.
- **Trend direction (qualitative, sourced):** Pokémon is rising, with its 30th anniversary in 2026 and ongoing shortages ([Kotaku](https://kotaku.com/pokemon-tcg-scalpers-walmart-lottery-draw-target-30th-anniversary-2000729942)). Labubu is declining (Westfield, May 2026). Switch 2 urgency is fading (launch was 2025). GPUs are scarce at the high end (TrackaLacker, Jul 2026). Holiday toys spike seasonally.
- **Market-structure signal:** a cluster of SEO "best Pokémon restock Discord" review sites with affiliate disclosures (tcgdropradar, whopreviews, sites.google.com pages) shows the niche is **heavily commercialized and saturated**.

---

## 8. Risks

| Risk | Severity | Note |
|---|---|---|
| Retailer ToS (scraping) | High | Walmart and Target restrict bots and spiders. Use official APIs only |
| Affiliate agreement / trademark | Medium-High | Possible bans on link redistribution and on branded communications. Get written confirmation |
| Retailer format changes | High | Walmart's Collectibles Drawing turns speed-based drops into lotteries. Walmart+ early access also cuts into what alerts are worth ([Notebookcheck](https://www.notebookcheck.net/Switch-2-restock-Walmart-getting-units-tonight-June-25-Plus-members-can-get-early-access.1044400.0.html)) |
| Bots beat alerts | High | Members pay and still miss out, which drives churn and complaints |
| Saturation / free competitors | High | TrackaLacker free, NowInStock free, 67k free Discord |
| Hype decay | Medium | Labubu and Stanley show categories can collapse within months |
| Support load vs "fully automated" | Medium | Alert groups need moderation and fielding "why did I miss it" complaints |
| Reputational (scalper association) | Medium | Petitions and the public mood are against resellers and bots |

---

## Gaps / next steps
- Allow-list **developer.bestbuy.com**, **walmart.io** and **affiliates.walmart.com**, then read the primary ToS and confirm whether the Walmart Affiliate API returns stock status and allows alert use.
- Allow-list **whop.com** and **reddit.com** to verify member counts, prices, and real user complaints.
- Pull Google Trends for "pokemon restock", "walmart drawing", and "rtx 5090 in stock".

---

## Direct check (2026-11-06, after walmart.com was allowed)

- A plain request to Walmart's Terms of Use page (`walmart.com/help/article/walmart-com-terms-of-use/...`)
  returned Walmart's **"Robot or human?" bot-check page** instead of the content. Walmart actively blocks
  automated access to its site, so any restock monitor that polls walmart.com would be fighting bot
  detection, and bypassing it is off the table for this team. Walmart restock data must come from an
  official/affiliate source, or Walmart should be covered only via announced drops (e.g. the Collectibles
  Drawing schedule) rather than live stock checks.
