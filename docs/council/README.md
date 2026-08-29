# The Macro-Receipts Council

A standing five-seat advisory council used to pressure-test product, marketing and
positioning decisions before they are built.

## Why a council and not a single reviewer

Every seat is deliberately biased. The value is in the collisions: the Positioning seat
and the Distribution seat want opposite things about tone; the Reduction seat wants to
delete what the Funnel seat wants to monetise. A decision that survives all five
disagreements is usually right. A decision every seat likes is usually bland.

## The seats

| Seat | Discipline | Methodology applied | Charter |
|---|---|---|---|
| 1 | Positioning, trust, remarkability | Seth Godin | [`council-godin.md`](../../.claude/agents/council-godin.md) |
| 2 | Distribution, X-native attention | Gary Vaynerchuk | [`council-vaynerchuk.md`](../../.claude/agents/council-vaynerchuk.md) |
| 3 | Behavioural science, signalling | Rory Sutherland | [`council-sutherland.md`](../../.claude/agents/council-sutherland.md) |
| 4 | First-principles reduction, scope | Elon Musk | [`council-musk.md`](../../.claude/agents/council-musk.md) |
| 5 | Funnels, offers, revenue | Russell Brunson | [`council-brunson.md`](../../.claude/agents/council-brunson.md) |

## Standing rule on the personas

These are **advisory personas applying publicly documented frameworks**. They are not the
real people, they do not speak for them, and they never produce invented quotations
attributed to them. This matters more here than on a normal project: Macro-Receipts is a
product whose entire credibility rests on accurate attribution of what real people
actually said. The council must not model behaviour the product forbids.

## How to convene

Each seat is a subagent definition in `.claude/agents/`. Run them in parallel, giving each
one the same Chair's question set plus any seat-specific asks. Never let one seat see
another's answer before writing its own — the independence is the point. Synthesise
afterwards, and record the disagreements as well as the conclusions.

## Sessions

| # | Date | Question | Output |
|---|---|---|---|
| 001 | 2026-08-28 | Engagement, revenue, the share, and look/feel/style/format for the X-first launch | [`session-001-brainstorm.md`](./session-001-brainstorm.md) · [`session-001-decisions.md`](./session-001-decisions.md) |
| 002 | 2026-08-28 | Cold start: zero followers, no budget — how do we get attention? | [`session-002-brainstorm.md`](./session-002-brainstorm.md) · [`session-002-decisions.md`](./session-002-decisions.md) |
