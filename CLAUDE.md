# Claude-Agents: Online Revenue Team

This repo holds a five-agent team (in `.claude/agents/`) whose goal is finding and
building automated, recurring online revenue.

| Agent | Role |
|---|---|
| `revenue-strategist` | Lead. Scores ideas, picks winners, writes plans, runs weekly reviews |
| `market-researcher` | Proves demand, tears down competitors, sets pricing |
| `product-builder` | Builds the minimum sellable product + landing page |
| `growth-marketer` | Launch, SEO, email sequences, retention |
| `automation-engineer` | Billing, fulfillment, scheduled pipelines, metrics |

## Workflow

1. Fill in `workspace/profile.md`.
2. `revenue-strategist` → `workspace/opportunities.md` (scored list) and `workspace/plan-<slug>.md`.
3. `market-researcher` → `workspace/research/<slug>.md` (GO / TEST FIRST / NO-GO).
4. `product-builder` → `workspace/build/<slug>/`.
5. `growth-marketer` → `workspace/marketing/<slug>/`.
6. `automation-engineer` → `workspace/automation/<slug>/` and `workspace/metrics.md`.
7. Weekly: `revenue-strategist` reviews metrics and decides double down / iterate / kill.

## Shared rules

- All shared state lives in `workspace/`. Read before writing; don't overwrite a teammate's file without reason.
- No spending money, creating accounts, publishing, or contacting real people without the user's explicit OK.
- No deceptive, spammy, or ToS-violating tactics. Cite sources for market claims.
