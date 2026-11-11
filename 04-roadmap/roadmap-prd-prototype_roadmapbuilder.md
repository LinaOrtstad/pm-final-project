# Feature Roadmap, Module 4 · BU Pay & Credit

**Scenario:** Riverty BU Pay & Credit, First Consumer Card

**Team:** [your assumed team size]

## Strategic anchors
- **Persona:** A regular pay later user who pays in shops by tapping a bank card on autopilot and would use a pay later card daily if it worked at places like the supermarket
- **Primary metric:** In-store share of purchases increase of 50%
- **Moment of misery:** The card is declined at and the app gives no reason
- **Guardrail:** In-store decline rates remains the same

## Scoring
| Feature | Value | Effort | Quadrant | Decision | Rationale |
|---|---|---|---|---|---|
| B1 Decline reason and retry hint | 5 | 2 | Quick Win | Now | It fixes the moment of misery directly, since a decline with a reason can be retried instead of abandoned. It doesn’t touch approval logic, so the decline-rate guardrail stays safe. |
| B2 Add to wallet from approval screen | 5 | 3 | Major Project | Next | It lets the persona tap at the supermarket with a phone, with no shipping delay, which drives in-store share. Effort stays at 3 only if Apple and Google provisioning approvals start in month 1. |
| B3 One balance view | 3 | 3 | Time Sinker | Cut | Seeing available limit helps avoid limit-driven declines, but it doesn’t help the persona pay in a shop. Do it when capacity frees up. |
| B4 Choose pay now or later after paying | 2 | 5 | Time Sinker | Cut | It adds a decision to a habit built on not deciding. Retroactive switching is hard to build and could reduce pay later share. |
| B5 Partner merchant offers | 2 | 4 | Time Sinker | Cut | This is a Sales preference. Partner deals don’t help supermarket autopilot spending and they cost business-development time. |
| B6 Cashback on every purchase	 | 3 | 4 | Time Sinker | Cut | It could raise share, but it does nothing for a card that gets declined. It also needs a rewards engine and finance sign-off. Revisit once B1 and B2 show activation. |
| B7 Physical card | 4 | 5 | Major Project | Next | It matches the persona’s tap habit exactly and reaches people who don’t use a wallet. Issuing, production and logistics make it heavy and long-lead, and B2 covers most of the same need sooner. |
| B8 One due date | 2 | 4 | Time Sinker | Cut | It is a repayment convenience, not a checkout problem, and it touches billing, collections and credit terms. It has no link to the in-store share target. |

## Roadmap
### NOW, this sprint
- **B1 Decline reason and retry hint**, It fixes the moment of misery directly, since a decline with a reason can be retried instead of abandoned. It doesn’t touch approval logic, so the decline-rate guardrail stays safe.

### NEXT, the following sprints
- **B2 Add to wallet from approval screen**, It lets the persona tap at the supermarket with a phone, with no shipping delay, which drives in-store share. Effort stays at 3 only if Apple and Google provisioning approvals start in month 1.
- **B7 Physical card**, It matches the persona’s tap habit exactly and reaches people who don’t use a wallet. Issuing, production and logistics make it heavy and long-lead, and B2 covers most of the same need sooner.

### LATER, backlog
- _(none)_

### ✂ Cut List
- **B3 One balance view**, Seeing available limit helps avoid limit-driven declines, but it doesn’t help the persona pay in a shop. Do it when capacity frees up.
- **B4 Choose pay now or later after paying**, It adds a decision to a habit built on not deciding. Retroactive switching is hard to build and could reduce pay later share.
- **B5 Partner merchant offers**, This is a Sales preference. Partner deals don’t help supermarket autopilot spending and they cost business-development time.
- **B6 Cashback on every purchase	**, It could raise share, but it does nothing for a card that gets declined. It also needs a rewards engine and finance sign-off. Revisit once B1 and B2 show activation.
- **B8 One due date**, It is a repayment convenience, not a checkout problem, and it touches billing, collections and credit terms. It has no link to the in-store share target.
