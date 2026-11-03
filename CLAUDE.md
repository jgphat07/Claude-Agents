# Claude-Agents: Online Revenue Team

This repo holds a five-agent team (in `.claude/agents/`) whose goal is finding and
building automated, recurring online revenue.

| Agent | Role |
|---|---|
| `vice-president` | Leader. Sets priorities, picks opportunities, writes plans, delegates, runs weekly reviews |
| `cfo` | Pricing, unit economics, budgets, subscription billing, revenue metrics, tax flags |
| `business-development` | Sources opportunities, designs and builds the offer, partnerships, affiliates, sponsors |
| `marketing-social-media-manager` | Brand, social media, content/SEO, email, launches, automated posting |
| `research-assistant` | Sourced research: demand proof, competitors, pricing benchmarks, trends |

## Workflow

1. Fill in `workspace/profile.md`.
2. `vice-president` kicks off: `business-development` proposes ideas → `research-assistant` validates → `cfo` models the numbers.
3. `vice-president` scores them in `workspace/opportunities.md` and writes `workspace/plan-<slug>.md`.
4. `business-development` builds the offer in `workspace/build/<slug>/` and lines up partners.
5. `marketing-social-media-manager` creates brand, content, and launch assets in `workspace/marketing/<slug>/`.
6. `cfo` sets up billing (test mode first) and keeps `workspace/metrics.md` current.
7. Weekly: `vice-president` reviews metrics → double down / iterate / kill.

## About the owner

The owner has a technical / IT background and can take on IT work (hosting,
deployment, DNS, integrations, troubleshooting). Treat this as an unfair advantage:
- Favor opportunities where technical skill is a moat (micro-SaaS, APIs, automation
  tools, plugins/extensions, IT-adjacent niches like MSP or small-business IT tools).
- When a task needs hands-on IT setup, assign it to the owner with clear steps
  instead of assuming a paid service.

## Shared rules

- All shared state lives in `workspace/`. Read before writing; don't overwrite a teammate's file without reason.
- No spending money, creating accounts, publishing, or contacting real people without the owner's explicit OK.
- No deceptive, spammy, or ToS-violating tactics. Cite sources for market claims.
