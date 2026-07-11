# WealthWise — Avatar-Based Digital Wealth Advisor

**IDBI Innovate 2026 · Track 01 (Digital Wealth Management)**

An avatar-based AI wealth advisor that lives inside the bank's mobile app.
"**Dhan**", the animated avatar, reads the customer's own transaction and
investment behaviour and turns it into timely, personalized, data-driven
guidance — conversational advisory, portfolio insights, and goal planning,
for **every** customer, not just HNIs.

## The problem

Wealth management remains fragmented and inaccessible to most customers.
Without a view of customer investment behaviour and spending habits, the bank
cannot provide timely, personalized guidance at scale.

## What the prototype shows

- **Avatar-led conversation** — animated SVG avatar with lip-sync and free
  browser text-to-speech (Web Speech API). No paid services.
- **Personalized advisory engine** — every answer is computed from the
  customer profile (income, spends, surplus, allocation, risk profile):
  financial snapshot, spend analysis, surplus deployment plan, FD-rebalance
  advice, 80C/ELSS tax optimisation.
- **Portfolio view** — net worth, current vs recommended allocation,
  behaviour-driven insights (idle surplus, FD concentration, spend spikes).
- **Goal planner** — exact SIP mathematics with projection chart and a
  "fits your surplus?" suitability check.

### Design principle: computed, never hallucinated

Deterministic finance math (SIP/goal/allocation/tax) is the source of truth;
an LLM layer handles open conversation with strict guardrails and a
bank-approved product catalogue. Advice is SEBI-IA suitability-checked
against the customer's risk profile.

## Run it

Zero dependencies — it's a single static page:

```bash
python -m http.server 8000   # then open http://localhost:8000
```

## Integration architecture (post-shortlist)

- **Data in**: CBS balances, card/UPI spends, deposit & MF holdings,
  AA-consented external assets.
- **Engine**: advisory microservice (rules + models) + LLM conversation layer
  with guardrails; product suggestions restricted to the bank catalogue.
- **Surface**: SDK module inside the IDBI mobile app; avatar renders
  on-device (SVG + TTS) so it scales to millions at near-zero marginal cost.
- **Compliance**: full audit log of every recommendation with its inputs.

---
*Demo profile is synthetic. No real customer data.*
