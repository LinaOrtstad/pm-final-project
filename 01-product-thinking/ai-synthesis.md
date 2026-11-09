# AI Synthesis, Product Health & Insights Summary (Module 2)

## Responses
- **Assumption to validate #1:** User already uses cards from other providers
- **Assumption to validate #2:** Riverty card will bring value to users
- **Assumption to validate #3:** Users spend lots of time on finding payment information
- **Moment of misery / red flag #1 (e.g., “user gave up after 3 tries”):** User already have several apps and don't want one more
- **Moment of misery / red flag #2:** User are scared of getting interest
- **Moment of misery / red flag #3:** Merchants don't see the value for them with a card that user can use at any shop
- **Product Health & Insights Summary (Claude's output):** Product Health & Insights Summary: First Consumer Card Test Launch
Executive Summary

The card is technically functional for online use and shows healthy early engagement among heavy pay later users, but reliability gaps in the in-store and wallet experience are undermining the core promise of a card that works everywhere. Users are most affected by problems of clarity (silent declines, split balances, mismatched due dates) rather than outright system failure, and these erode trust faster than they generate support tickets. Because the pilot population skews heavily toward employees, the headline approval and activation figures likely overstate how the product would perform with the general market.

Thematic Synthesis
1. Technical Stability

In-store payment is the weakest part of the technical experience. Decline rates in physical shops ran well above online decline rates throughout the pilot, and after improving mid-pilot they rose again in the final month. Wallet provisioning fails or is abandoned for roughly a third of activated cards, which leaves participants without the tap-to-pay behavior that would put the card in their habitual routine. Notification timing compounds the problem by making successful payments look like failures.

In-store declines with no reason shown (Critical): Several dozen declines were logged, and at least one participant reverted to their debit card within a week of a single unexplained decline.
Wallet provisioning failure or abandonment (Critical): About a third of activated cards (143 of 431) never reached the phone wallet, which blocks the primary in-store use case.
Delayed purchase notifications (High): Late push messages in some shops lead participants to believe a payment failed, and some pay a second time with another card.
Decline rate drift in the latest month (Medium): Overall declines rose from 2.2% to 3.5% across the pilot, and in-store declines rebounded to 8.7% after reaching 6.4%.
2. Onboarding and Activation

The funnel loses people at two points. The first is before application: only about 60% of invitees applied. The second is after approval: roughly a quarter of approved people (155 of 586) never activated the card. Identity verification is a smaller leak, with strong completion overall, but its retry behavior pushes some applicants out. Activation is notably weaker among light pay later users, who also signal wariness about credit-style products.

Approval-to-activation drop-off (High): Only 73.5% of approved people activated, and the rate falls to 62% among light pay later users.
Identity check retry friction (Medium): A failed document upload triggers a repeat photo request, and some applicants abandon at this step.
Wallet setup disconnected from approval (Medium): Wallet addition happens after activation as a separate step, and a significant share of users never complete it.
3. Trust and Clarity

This is the most consistent qualitative theme. Participants cannot form a single mental model of what they owe: card balances and standard pay later orders sit on separate screens, statement dates differ from pay later due dates, and reminders for different amounts arrive in the same week. Combined with silent declines, the product repeatedly leaves users unsure whether a payment worked, what they owe, and when. Some prospective users also distrust the card because instalment language reads as interest-bearing credit, which they actively try to avoid.

Fragmented view of total obligations (High): Participants ask which total is the real one and cannot see card and pay later liabilities in one place.
Conflicting due dates and duplicate reminders (High): Misaligned statement and pay later schedules produce overlapping reminders for different amounts.
Unexplained declines (High): The absence of a reason or next step turns a recoverable event into lost confidence.
Instalment and credit perception (Medium): Light and cautious users associate instalment messaging with interest-bearing credit, which creates hesitation before activation.
4. Engagement and Value Proposition

Early engagement is encouraging but not yet proven durable. Heavy pay later users transact far more often and spend considerably more per month than light users, and online and partner merchant spend dominates card volume. However, only around two-thirds of cards are active one month after activation, and about half to 57% are active after two months. Active card counts also dipped in the final month. Qualitative feedback suggests the card has to compete with an ingrained habit of tapping a bank card, with app fatigue, and with incentives such as cashback that may drive trial more than retention. Merchants raise a parallel question about what the card offers them beyond the checkout option they already have.

Retention decay after activation (High): Month-one retention sits at roughly 64% to 69% across cohorts and falls further by month two.
Weak in-store habit formation (High): In-store share of purchases stays under 20%, consistent with users defaulting to their bank card in shops.
Merchant value gap (Medium): Enterprise merchants ask what they gain, and SME merchants welcome traffic-driving offers but not flows that favor large marketplaces.
Incentive-driven trial risk (Medium): Cashback is cited as a reason to try the card, with explicit doubt about continued use.
Multi-app fatigue (Medium): Heavy users already manage several pay later apps and are reluctant to add another thing to check before payday.
5. Support Load

The ticket pattern points to confusion rather than failure. Much of the likely support demand stems from the clarity gaps above: balance questions, duplicate reminders, and uncertainty about whether a payment went through. Double payments caused by delayed notifications could also create refund and reconciliation work.

Balance and due date queries (High): Predictable contact volume follows from the split views and misaligned schedules.
Possible duplicate payments (Medium): Participants who pay again after a delayed notification create reconciliation workload.
Credit score questions (Medium): Participants ask whether using the card affects their credit score, and no help content exists to answer them.
6. Evidence Quality and Delivery Context

Several findings should be read with caution. Employees make up 639 of 1,200 invitees, and the internal risk view is that approval and repayment results will look better than they would for real customers. Annual spend extrapolated from four months is indicative only, and take rate and churn cannot be measured in an invite-only test. Operations also notes that proposition changes pass through approval of pricing, credit policy and terms, a process that takes months.

Pilot population bias (High): Approval and repayment figures are likely optimistic relative to the target market.
Unmeasurable adoption and churn (Medium): Share of existing users who would take a card and annual churn require assumptions rather than observation.
Slow proposition change cycle (Medium): Pricing, credit policy and terms changes carry long approval lead times.
Minor Technical Debt

Inconsistent display of the post-purchase instalment option across categories (perceived by participants as random), and the lack of a help article on credit score impact.
- **Did the AI catch the specific moment of misery / pain point you found in Step 1?:** Not really, I lac the merchant point of view
- **Did it smooth over a critical frustration into a generic bullet point?:** Yes
- **Did the AI try to suggest features or a roadmap despite the constraints?:** No, didn't get any suggested features
- **Logic leak / hallucination #1 (e.g., “AI suggested a new search bar feature, roadmap leak”):** Can't really find any hallucination, I don't get any suggested features as output and Claude is really pointing out tha lack of data and don't make any assumptions on that
- **Logic leak / hallucination #2:** _(not filled in)_
