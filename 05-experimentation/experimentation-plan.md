# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** Based on  A regular pay later user who pays in shops by tapping a bank card on autopilot and would use a pay later card daily if it worked at places like the supermarket, In-store share of purchases today never exceeded 17.7%. I believe that the ability to use one card everywhere, including splitting the big weekly shop, without thinking about it for  A regular pay later user who pays in shops by tapping a bank card on autopilot and would use a pay later card daily if it worked at places like the supermarket, will result in User to use Riverty card for all there purchases, as measured by a 50% increase in In-store share of purchases. I will protect In-store decline rates remains the same and will make a go/no-go decision after 6 months
- **From M3, your primary success metric & guardrail metric:** In-store share of purchases increase to 50%
In-store decline rates remains the same
- **From M4, the feature you scoped in your PRD this is what you're testing:** Decline Reason and Retry Hint -When a pay later card tap fails at the supermarket till, the user knows why and what to do within 5 seconds, so one decline never ends a daily habit

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** Every simulated decline appears in the feed with merchant, amount and time.
- **Persona pull your M2 persona:** A regular pay later user who pays in shops by tapping a bank card on autopilot and would use a pay later card daily if it worked at places like the supermarket
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** User can use one card everywhere, including splitting the big weekly shop, without thinking about it.
- **Primary success metric the one number that defines success, from M3:** In-store share of purchases increase with 50%
- **Baseline rate today's rate of your primary metric, from your M3 data:** In-store share of purchases at 17.7%
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** <15%
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** +2pts
- **Sample size per arm use the calculator in the builder, baseline + MDE:** 5000
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** 50/50 over 1 month
- **Significance threshold p < 0.05 is standard, explain any deviation:** <0,05

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** The card is declined at a bakery, and the app gives no reason (N-06, T-101). The participant went back to their debit card the same week. The card never gets a second chance, and the participant files no ticket, so the loss is invisible. For many users the moment comes even earlier: 143 activated cards never reached the phone wallet (T-102), so tap-to-pay was never available to them.
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** Screen 1: Entry point (notification and activity feed)
Lock-screen style notification banner. Title: "Payment declined at [merchant]". Body: the reason headline. Tap opens Screen 2.
Activity feed with a declined row: red "Declined" label, merchant, amount, time, and a "New" badge until opened. A few approved rows sit around it for realism.
Prototype-only control panel, visually separated from the app: a dropdown of 7 scenarios and a "Simulate decline" button.
Screen 2: Feature core (decline detail)
Header: back arrow, merchant, amount, time, "Declined" chip.
Reason block: icon and reason headline, 12 words or fewer.
Hint block: either "Try again" or "Pay another way", each with one short instruction line.
Primary button "Retry payment", shown for "Try again" reasons only. Secondary button "Got it", shown for every reason.
Deliberately absent: contact links, a detailed view, any risk wording.
Screen 3: Success and confirmation (resolution)
Variant A, retry approved: green check, "Approved on second try", merchant, amount, time, "Paid with pay later", and the declined attempt marked "Not charged".
Variant B, "Got it" pressed: neutral check, "Got it", and the line "This purchase wasn't paid with pay later."
"Done" button returns to Screen 1. The declined row reads "Resolved" after Variant A and "Seen" after Variant B.
Functional requirements
All eight come from the MUST HAVE list.
ID	Rule	How we measure it
FR1	Every simulated decline appears in the feed with merchant, amount and time.	7 of 7 scenarios. Notification shows within 5 s of "Simulate decline".
FR2	The reason comes from 5 fixed reasons plus 1 fallback: limit reached, payment overdue, card blocked or not activated, contactless limit, technical or merchant issue.	100% of declines mapped by code lookup.
FR3	Reason text is 12 words or fewer, in plain language, with no risk-rule words (fraud, score, model, rule, suspicious).	0 strings fail the word count or the word blocklist.
FR4	Each reason maps to exactly one hint. "Try again" only for contactless limit and technical or merchant issue. Every other reason maps to "Pay another way".	0 retry hints on non-retryable reasons.
FR5	Reason and hint appear on the same screen with no scrolling.	Pass or fail at 375x667.
FR6	The notification opens the decline screen for that transaction.	1 tap maximum.
FR7	A missing or unmapped code shows "This payment couldn't be approved." with "Pay another way".	100% of unmapped codes.
FR8	The feature never changes an approval outcome. A retry prompt appears at most once per transaction, and a second decline removes it.	Maximum 1 retry prompt per transaction. 0 code paths that alter approval.
- **Isolation check, what has NOT changed? list everything identical between arms (app version, eligibility rules, notifications, onboarding). If something changed inadvertently, your test is compromised.:** App version, Eligibility rules, onboarding to app

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** I believe that [Decline reason and retry hint] for A regular pay later user who pays in shops by tapping a bank card on autopilot and would use a pay later card daily if it worked at places like the supermarket will result in User can use one card everywhere, including splitting the big weekly shop, without thinking about it., as measured by a +2 pts change in In-store share of purchases increase with 50% within 1 month. We will protect <17,7% throughout the test.
- **Your shipping criteria (filled in):** We will SHIP if In-store share of purchases increase with 50% improves by ≥ +2 pts at P < 0,05 and <17,7% does not reach Drop to 10% usage after 1 month. We will ITERATE if direction is positive but lift is below MDE. We will KILL if the primary metric shows no improvement or moves negatively. The read date is fixed at the end of 1 month, no results reviewed before then.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** _(not filled in)_
