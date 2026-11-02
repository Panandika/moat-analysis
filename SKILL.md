---
name: moat-analysis
description: >
  Score how defensible a SaaS product, service, or business is against AI
  disruption, using the 8-moat / 10-attack framework from Rob Walling & Anar's
  MicroConf Europe 2026 talk ("How do you survive as a SaaS in the age of AI").
  Researches the target on the web, scores each moat 0-10 with cited evidence,
  rates exposure to each AI attack, flags dead moats the target still relies on,
  and recommends moves to climb. Use when the user asks to "analyze moats",
  "how defensible is X", "is X safe from AI", "moat score", "moat scorecard",
  "will AI kill X", or wants to evaluate a product/competitor/acquisition target.
  Triggers: "moat analysis", "moat-analysis", "analyze the moats of", "defensibility".
---

# Moat Analysis

Evaluate one product/service (or compare several) against the AI-era moat framework.
Core premise: assume cloning the code costs ~zero. A moat only counts if it still
protects the business after someone vibe-codes a feature-equal copy.

## Inputs

- **Target**: product name, URL, or the user's own business (ask for a short
  description if it's private / not on the web).
- **Mode** (default `quick`):
  - `quick` — inline research, ~6-10 searches, single target.
  - `deep` — one subagent per target or per moat group; use for 2+ targets or
    acquisition-grade diligence.
- **Lens** (optional): `founder` (how to strengthen) or `buyer` (will it exist in
  3-5 yrs → valuation). Default: both.

## Workflow

1. **Identify target.** Confirm exact company/product (name collisions are common).
   Background check: legal entity, founded, HQ, funding/ownership, licenses or
   certifications held, reputation (reviews, complaints, press). Give a one-line
   identity verdict before scoring.
2. **Map the business.** Who is the customer, who is the user (same or different?),
   what job it does, pricing model (per seat / usage / outcome), what it integrates
   with, whether it *advises* or *acts*.
3. **Research evidence per moat** (section below). Prefer primary sources: official
   site, docs, pricing page, partner directory, regulator registries, status page,
   changelog, earnings/filings; then G2/Capterra/Reddit/press. Every factual claim
   gets an inline citation `[n]`. Unknown ≠ zero: mark `?` and say what was searched.
4. **Score 8 moats** 0-10 using the rubric.
5. **Rate 10 attacks** Low / Med / High exposure, one-line reason each.
6. **Dead-moat check.** List any old moats the target leans on that AI erodes.
7. **Verdict + moves.** Overall defensibility, top 2-3 moves to climb, top risks.
8. **Sources list** at end.

Do not score from memory alone. If a moat can't be evidenced, say so.

## The 8 moats (what still works)

Moats are a dial (0-10), not a switch. 1-2 strong moats is already a good position.

| # | Moat | Test question | Strong signal | Examples |
|---|---|---|---|---|
| 1 | **Buyers know & trust you** — brand, known buying process, partners whose business depends on recommending you, internal champions | Who built their business or career around recommending/defending you? | Partner/agency/consultant ecosystem; certifications for implementers; "default choice" in the vertical | QuickBooks (accountants), Shopify (agencies), Salesforce |
| 2 | **System of record** — daily ops built around you; balances, approvals, statuses, roles, rules; other systems read from / write to you | If they leave: what can't they export, what breaks downstream, what must they rebuild? | Users log in daily; history/audit trail; many inbound/outbound integrations; it's the business's OS | Jira, Gymdesk |
| 3 | **Allowed to act** — executes (moves money, sends, cancels, approves), not just reports/recommends | Do you take the action, or only advise? | Write access to money/customers/production; sits in a live flow | Stripe Connect, Reimbi, Churnkey |
| 4 | **They don't check your work** — output trusted blindly after years of being right; high stakes if wrong | Do customers trust the output enough to not double-check? | Compliance-grade calculations; customer doesn't understand the domain; long track record | Gusto (payroll), Avalara (sales tax) |
| 5 | **Someone official already said yes** — vendor itself holds licenses, accreditations, board approvals, carrier registrations | What approvals do you hold that a newcomer must wait for? | Vendor-held license (not just "serves regulated customers"); slow/expensive to obtain | Vanta, BACB-approved CE provider, US SMS (10DLC/consent) |
| 6 | **Everyone's already in it** — network effect / multi-party coordination | Would a competitor have to move everyone at once? | Many roles or orgs in one space; non-technical participants; switching needs group agreement | Slack, Commit Swimming (whole club + parents) |
| 7 | **Every customer makes it smarter** — cross-customer learning loop | Does one customer's experience improve it for everyone else? | Must pass **all 3 gates**: (a) pooled across customers, not siloed; (b) customer can export data but not the learned model; (c) still improving over time | Stripe Radar, Ramp, Mailchimp Omnivore |
| 8 | **Hard to keep running** — the moat is operations, not code | What do you maintain that you resent maintaining? | Ongoing ops burden: IP rotation, deliverability/anti-spam, infra, uptime, regulatory upkeep | ScrapingBee, Cloudflare, Drip (anti-spam staff) |

### Scoring rubric (per moat)

- **0** — absent.
- **1-3** — weak/early; signal exists but a funded clone could match in months.
- **4-6** — real; meaningful switching pain or barrier, but not dominant.
- **7-8** — strong; competitors must earn it over years.
- **9-10** — category-defining (Salesforce/Shopify/Stripe level).

Report confidence per score: `H` (primary evidence), `M` (indirect), `L` (inferred).

## The 10 AI attacks (exposure check)

Supply shock (more supply → commoditization):
1. **Customer vibe-codes it** — they only need the 3 features they use, not your 50.
2. **Competitors reach parity** — feature lead buys far less time.
3. **Open source catches up** — non-technical buyers can now self-host with AI help.
4. **Platform ships your feature free** — the system of record you plug into (CRM etc.) builds it; your UI is their spec.
5. **Custom software at SaaS prices** — agencies build bespoke for $300-1,000/mo recurring.
6. **Model absorbs the product** — the LLM does it natively (ad copy, headline tools).

Demand shock (fewer/poorer buyers):
7. **Customers go out of business** — e.g. translation/transcription agencies; involuntary churn.
8. **Seats disappear** — e.g. support teams 8 humans → 1-2 supervising AI agents.
9. **The managed thing stops mattering** — e.g. take-home coding tests.
10. **Human user replaced** — a rival bundles software + agent at 5-10x price and replaces the worker. If this is High: **agentify or likely go to zero in a few years.**

## Dead / dying moats (flag reliance on these)

Unique features · clever code/algorithms · integrations count (API = spec) ·
UX familiarity (irrelevant once agents operate it) · data-export friction (AI
scrapes it out) · SEO/owned traffic (50/50, AI is muddying it).
Still-alive classics: system of record, multi-person coordination, brand + something.

## Climb moves (from current position → moat)

| If target is… | Move toward |
|---|---|
| Vertical tool | Become the vendor the industry recommends (partner program, implementer certs) |
| Point solution | System of record (own the workflow + data others read) |
| Reporting/analytics | Act — execute the payment/flow, not just suggest it |
| Calculator | Output nobody double-checks (accuracy guarantees, liability, track record) |
| In regulated industry | Become the approved/licensed provider |
| Single-seat tool | Multi-party coordination / network effect |
| Collects data | Cross-customer learning loop passing all 3 gates |
| Has painful infra | Lean in — the burden nobody else will carry |
| Users replaceable by AI | Ship an agent on top; price on outcome |

## Output format

```markdown
# Moat Analysis: <Target>
**Identity:** <entity, founded, HQ, owner/funding, licenses> — verdict ✅/⚠️/❌ [n]
**Business map:** customer vs user · job · pricing model · advises or acts

## Scorecard
| # | Moat | Score | Conf | Evidence |
|---|---|---|---|---|
| 1 | Buyers know & trust | 6/10 | M | 400+ certified partners [3] |
...
**Total: NN/80** · Strong moats (≥7): <list>

## AI attack exposure
| # | Attack | Exposure | Why |
...
Highest risks: <top 2-3>

## Dead moats relied on
- <moat> — <why it's eroding for this target>

## Verdict
<Defensibility: Fortress (≥2 moats ≥7, no High demand attack) / Defended / Exposed / At risk>
<Buyer lens: likely to exist in 3-5 yrs? multiple pressure up/down>

## Moves to climb
1. <specific move> → raises moat #N from X to ~Y
...

## Gaps
- <unknowns + what was searched>

## Sources
[1] <title>(url)
```

Verdict bands (guide, not formula):
- **Fortress** — 2+ moats ≥7 and no High on attacks 7-10.
- **Defended** — 1 moat ≥7, or 2+ at 5-6.
- **Exposed** — best moat ≤5; relies mostly on dead moats.
- **At risk** — any High on attack 7/10 with no agent strategy, or total ≤15.
- A High on attack 4 (platform ships your feature) caps the verdict at **Exposed**, whatever the moat scores.

## Comparing multiple targets

Add a side-by-side table (moats as rows, targets as columns) and a "who wins on
which moat" line. In `deep` mode, spawn one research subagent per target with the
moat table + rubric in the prompt and require cited evidence per score; you merge
and score consistently.

## Rules

- Cite every factual claim; no score without evidence or an explicit `L` + reason.
- Vendor marketing claims (e.g. "reduces churn 58%") are labelled self-reported.
- "Serves regulated customers" ≠ holding an approval (moat 5).
- Siloed per-customer ML ≠ learning loop (moat 7 gate a).
- Keep verdict honest: most products score 1-2 real moats. Say so.
- Framework source: Rob Walling & Anar (Discretion Capital), MicroConf Europe 2026;
  free field guide/scorecard at microconf.com/moats.
