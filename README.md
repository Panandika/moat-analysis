# moat-analysis

An agent skill that scores how well a software product can defend itself once AI makes code cheap to copy.

You give it a product name. It researches the company on the web, scores eight moats from 0 to 10 with a cited source behind each score, rates exposure to ten AI attacks, and recommends moves for the weakest spots.

The framework comes from [Rob Walling and Anar's MicroConf Europe 2026 talk](https://www.youtube.com/watch?v=KpILHX2D-AA) on surviving as a SaaS company in the age of AI. They estimate 10 to 20 percent of SaaS companies will decline or go to zero, and they argue that feature lists, clever code and integration counts stopped protecting anyone. MicroConf publishes a free field guide and scorecard at [microconf.com/moats](https://microconf.com/moats). This repo turns their framework into a research procedure an agent can run. MicroConf has no involvement with it.

## Install

`SKILL.md` follows the [Agent Skills](https://agentskills.io) format: YAML frontmatter with a name and description, then plain Markdown instructions. Clone the repo into the folder your agent reads skills from:

```bash
git clone https://github.com/Panandika/moat-analysis <your-agent-skills-dir>/moat-analysis
```

Your agent needs a web search tool. If it doesn't load skills, paste `SKILL.md` into its system prompt or project instructions.

## Use

Agents that support slash commands take:

```
/moat-analysis Churnkey
/moat-analysis Gusto deep
/moat-analysis Otter.ai vs Granola vs Fathom
```

Any agent also picks it up from plain requests: "how defensible is Linear", "will AI kill Calendly", "moat scorecard for my product".

| Option | What it does |
|---|---|
| `quick` (default) | 6 to 10 searches, one product, runs in the main conversation |
| `deep` | One research subagent per product, if your agent can spawn them. Use it to compare competitors or vet an acquisition |
| `founder` lens | Weights the report toward moves you can make |
| `buyer` lens | Weights it toward whether the company survives 3 to 5 years |

For a private product, describe it in a few sentences and the skill scores what you tell it.

## The eight moats

The test assumes anyone can clone your code for free. A moat counts only if it still holds after that.

| # | Moat | Question the skill answers |
|---|---|---|
| 1 | Buyers know and trust you | Who built a business or career around recommending you? |
| 2 | System of record | If a customer leaves, what can't they export and what breaks downstream? |
| 3 | Allowed to act | Do you move the money or send the message, or only suggest it? |
| 4 | Nobody checks your work | Do customers trust the output enough to skip checking it? |
| 5 | Someone official said yes | Which licences or approvals do you hold that a newcomer has to wait for? |
| 6 | Everyone's already in it | Would a competitor have to move a whole team or community at once? |
| 7 | Every customer makes it smarter | Does one customer's data improve the product for all the others? |
| 8 | Hard to keep running | What operational burden do you carry that a clone would have to carry too? |

Most products hold one or two of these. Two scores of 7 or higher puts you in good shape.

## The ten attacks

Supply side, where AI floods your market with substitutes:

1. Your customer builds the three features they use.
2. Competitors reach feature parity in months.
3. Open source catches up, and non-technical buyers can now deploy it.
4. The platform you plug into ships your feature for free.
5. Agencies sell custom builds at SaaS prices.
6. The model does the job natively.

Demand side, where AI shrinks or impoverishes your buyers:

7. Your customers go out of business.
8. Your seat count shrinks as AI agents replace staff.
9. The thing you manage stops mattering.
10. AI replaces your human user, and a rival sells software plus an agent.

The skill rates each attack Low, Med or High with a one-line reason.

## What the report contains

1. Identity check: legal entity, founders, funding, licences, reviews, and a verdict on whether the company is who it claims to be.
2. Business map: buyer versus user, pricing model, integrations, and whether the product acts or advises.
3. Scorecard: eight scores with confidence (H, M or L) and citations.
4. Attack table with the top two or three risks.
5. Old moats the product still leans on, such as feature count or UX familiarity.
6. Verdict: Fortress, Defended, Exposed or At risk.
7. Moves that would raise specific scores, with before and after estimates.
8. Gaps: what the research couldn't find and where it looked.

### Verdict bands

| Verdict | Condition |
|---|---|
| Fortress | Two or more moats at 7+, and no High on attacks 7 to 10 |
| Defended | One moat at 7+, or two or more at 5 to 6 |
| Exposed | Best moat at 5 or below |
| At risk | High on attack 7 or 10 with no agent strategy, or a total of 15/80 or less |

A High on attack 4 caps the verdict at Exposed. When your biggest integration partner ships your core feature, your moat scores stop mattering much.

## Rules the skill follows

- Each score cites a source. Without one, the score carries an L and a stated reason.
- Vendor statistics ("cuts churn 58%") get labelled self-reported.
- Selling to regulated customers earns nothing on moat 5. The vendor has to hold the approval itself.
- Per-customer models earn nothing on moat 7. The loop has to pool data across customers, keep what it learned after a customer exports their data, and keep improving.

## Example

[examples/churnkey.md](examples/churnkey.md) holds a full run on Churnkey, a cancel-flow tool. Rob Walling named Churnkey in the talk as a moat example because it acts inside the cancellation flow. The research found that Stripe now ships Retention Rules, which target cancel offers by reason, tenure and lifetime value. Churnkey scored 20/80 and landed in Exposed. The research dates from 2 November 2026.

## Limits

- Scores reflect public evidence. A company with thin press coverage gets many `?` marks.
- Two runs on the same product can differ by a point or two per moat, since a model applies the rubric.
- The framework ignores pricing power, team quality and cash position. Read it next to a financial review.

## License

MIT. See [LICENSE](LICENSE).
