# Regression Testing

RFP Engine was developed through staged historical regression exercises based on real-world RFx patterns. The public portfolio describes the behaviors without publishing solicitation files, employer knowledge, proposal content, customer information, or pricing.

## What the suite is designed to prove

| Scenario | Expected behavior |
|---|---|
| Required evidence is unavailable | Hold the affected component and identify the missing evidence |
| One component is blocked | Continue unrelated eligible work |
| A commitment needs human authority | Stop before incorporating the commitment |
| A process restarts | Recover the latest verified authoritative revision |
| Saved and visible state disagree | Reject stale or non-authoritative state |
| A required package field is missing | Detect it before final assembly |
| A reviewed package changes | Invalidate downstream review as required |
| Final approval identifies one package | Reject submission closeout for any different package |
| Pricing context is incomplete | Keep the pricing branch non-authoritative and independently held |

## Representative failure modes discovered

The testing program has exposed and driven fixes for:

- whole-workflow drafting stops caused by a single blocked component;
- persisted Opportunity Records lagging visible workflow state;
- required form fields discovered too late in package assembly;
- ambiguous requirement timing being mistaken for submission obligations;
- excessive human gates that did not represent genuine decision authority; and
- runtime artifact loss that could otherwise invite reconstruction from incomplete state.

## Testing philosophy

A fluent answer is not a passing result. A passing result must preserve authority, evidence, exact state, and artifact identity—even when doing so means stopping the workflow.
