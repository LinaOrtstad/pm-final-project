# PRD: Decline Reason and Retry Hint

**Author:** @Lina · **Status:** Draft · **Target:** High-Fidelity Prototype · Nov 11, 2026

## 1. The Big Picture

### Vision

When a pay later card tap fails at the supermarket till, the user knows why and what to do within 5 seconds, so one decline never ends a daily habit.

### Press release

**BU Pay & Credit's pay later card now tells you why a payment was declined.** When a tap fails in a shop, the app sends a notification within seconds. It states the reason in plain words and gives one instruction: try again, or pay another way. Until now, a decline at the till left customers in the queue with no explanation and no next move.

For people who tap on autopilot and want to use the card every day, a silent decline meant giving up on the card for the rest of the trip. Now a connection hiccup becomes a second tap, and a real limit or account issue becomes a clear cue to use another payment method. No approval decision changes: the app explains a decline, it never overrides one.

### Success metrics

| Type | Metric | Target |
| --- | --- | --- |
| Primary | In-store share of purchases | +50% against the pre-launch baseline (baseline: open, to be set by analytics) |
| Guardrail | In-store decline rate | Unchanged: no increase against the pre-launch baseline (tolerance: open, to be agreed with Risk) |

B1 does not create taps. B2 (wallet) and B7 (physical card) do that. B1 protects the share they create by stopping a decline from ending the habit. Leading indicator for this feature: the share of declined taps followed by a successful in-store payment within 10 minutes.

## 2. The Details

### User stories

**Story 1: Know why.** As a regular pay later user tapping my card at the supermarket till, I want to see why the payment was declined as soon as it happens, so that I know whether the problem is me, the card or the shop.

Acceptance criteria:

- A notification appears within 5 seconds of the decline and opens the decline screen in 1 tap.
- The screen shows merchant, amount, time and one reason of 12 words or fewer.
- 7 of 7 test scenarios show a reason. None shows a blank or a raw code.

**Story 2: Know what to do.** As the same user with people queuing behind me, I want one clear instruction, try again or pay another way, so that I don't repeat a tap that cannot work.

Acceptance criteria:

- The instruction sits on the same screen as the reason, without scrolling on a 375x667 viewport.
- Technical or merchant issue and contactless limit show "Try again". Limit reached, payment overdue, card blocked or not activated, and unknown show "Pay another way".
- After a second decline on the same transaction, the screen shows only "Pay another way".

**Story 3: Know it worked.** As a user who retried and got approved, I want confirmation that the payment went through on pay later, so that I leave the till without worrying about a double charge.

Acceptance criteria:

- Confirmation shows merchant, amount, time and "Paid with pay later".
- The declined attempt shows "Not charged" only when its status is final-declined.
- "Done" returns to the feed, and the declined row shows "Resolved".

### Screens to build

**Screen 1: Entry point (notification and activity feed)**

- Lock-screen style notification banner. Title: "Payment declined at \[merchant\]". Body: the reason headline. Tap opens Screen 2.
- Activity feed with a declined row: red "Declined" label, merchant, amount, time, and a "New" badge until opened. A few approved rows sit around it for realism.
- Prototype-only control panel, visually separated from the app: a dropdown of 7 scenarios and a "Simulate decline" button.

**Screen 2: Feature core (decline detail)**

- Header: back arrow, merchant, amount, time, "Declined" chip.
- Reason block: icon and reason headline, 12 words or fewer.
- Hint block: either "Try again" or "Pay another way", each with one short instruction line.
- Primary button "Retry payment", shown for "Try again" reasons only. Secondary button "Got it", shown for every reason.
- Deliberately absent: contact links, a detailed view, any risk wording.

**Screen 3: Success and confirmation (resolution)**

- Variant A, retry approved: green check, "Approved on second try", merchant, amount, time, "Paid with pay later", and the declined attempt marked "Not charged".
- Variant B, "Got it" pressed: neutral check, "Got it", and the line "This purchase wasn't paid with pay later."
- "Done" button returns to Screen 1. The declined row reads "Resolved" after Variant A and "Seen" after Variant B.

### Functional requirements

All eight come from the MUST HAVE list.

| ID | Rule | How we measure it |
| --- | --- | --- |
| FR1 | Every simulated decline appears in the feed with merchant, amount and time. | 7 of 7 scenarios. Notification shows within 5 s of "Simulate decline". |
| FR2 | The reason comes from 5 fixed reasons plus 1 fallback: limit reached, payment overdue, card blocked or not activated, contactless limit, technical or merchant issue. | 100% of declines mapped by code lookup. |
| FR3 | Reason text is 12 words or fewer, in plain language, with no risk-rule words (fraud, score, model, rule, suspicious). | 0 strings fail the word count or the word blocklist. |
| FR4 | Each reason maps to exactly one hint. "Try again" only for contactless limit and technical or merchant issue. Every other reason maps to "Pay another way". | 0 retry hints on non-retryable reasons. |
| FR5 | Reason and hint appear on the same screen with no scrolling. | Pass or fail at 375x667. |
| FR6 | The notification opens the decline screen for that transaction. | 1 tap maximum. |
| FR7 | A missing or unmapped code shows "This payment couldn't be approved." with "Pay another way". | 100% of unmapped codes. |
| FR8 | The feature never changes an approval outcome. A retry prompt appears at most once per transaction, and a second decline removes it. | Maximum 1 retry prompt per transaction. 0 code paths that alter approval. |

### Smart behaviors

| Situation | Outcome |
| --- | --- |
| Technical or merchant issue, first decline | Reason: "The payment didn't go through because of a connection problem." Hint: "Try again", "Tap again in a few seconds." Retry button shown. |
| Technical or merchant issue, retry also declines | Reason unchanged. Hint switches to "Pay another way". Retry button removed. |
| Contactless limit | Reason: "This tap is above the contactless limit." Hint: "Try again", "Tap again and enter your PIN." Retry button shown. |
| Limit reached | Reason: "You've reached your pay later limit." Hint: "Pay another way", "Use another card or cash for this purchase." |
| Payment overdue | Reason: "A payment on your account is overdue." Hint: "Pay another way". No repay shortcut yet. |
| Card blocked or not activated | Reason: "This card is blocked or not yet activated." Hint: "Pay another way". |
| Code missing or unmapped | Reason: "This payment couldn't be approved." Hint: "Pay another way". |
| User opens the app with an unseen decline | Row carries a "New" badge and opens Screen 2 in 1 tap. |
| Decline is older than 10 minutes when opened | "Try again" becomes "Try again next time you pay". Retry button hidden. |
| Retry approved | Screen 3 Variant A. Declined row reads "Resolved". |

### Technical constraints (what not to build)

- No external APIs. Scenarios, merchants and amounts are hardcoded fictional data. No payment processor, no decline-code feed, no push service.
- No login, accounts or authentication.
- One HTML file with plain JavaScript and CSS. No frameworks, no libraries, no build step.
- No storage. State lives in memory and resets on reload.
- The notification is simulated inside the page, not a real push.
- One fixed 375x667 phone frame. No desktop or tablet layouts.
- No analytics, no tracking, no copy generated at run time. Every string comes from one fixed table.
- Production sizing: 3 backend and 2 frontend engineers, delivery inside the 6-month window, with B1 in the NOW lane. Production dependency: the card processor must return decline reason codes (to be confirmed).

## 3. The Logistics

### Features out (Won't have now)

- **Customer service contact information.** The goal is to make the call unnecessary. A contact link in the decline message sends the user to support instead of solving the problem at the till.
- **Pre-decline warnings such as low-limit alerts.** They overlap with B3, which is cut.
- **Switching to pay now at the till.** It overlaps with B4, which is cut.
- **Limit-increase requests and anything that loosens approvals.** They put the in-store decline-rate guardrail at risk.
- **SMS and email channels.** Push and in-app cover the persona.
- **Credit-score or risk-factor explanations.** They carry compliance risk and the persona doesn't need them.

Also outside the prototype: reason-specific one-tap actions, decline analytics, the push-off fallback banner, the detailed decline view, a past-declines list and notification preferences. Decline analytics is still a release gate for production, because without it the guardrail can't be checked.

### Edge cases

| Situation | Handling |
| --- | --- |
| Decline code missing or unmapped | Show "This payment couldn't be approved." with "Pay another way". Never a blank screen, never a raw code. |
| Retry declines again | Keep the reason, replace the hint with "Pay another way", remove the retry button. One retry prompt per transaction. |
| Two declines at different merchants within 2 minutes | Two rows and two notifications. Each opens its own decline screen with its own reason. |
| Notification dismissed unseen | The row keeps its "New" badge until Screen 2 is opened. |
| Decline opened more than 10 minutes later | "Try again next time you pay" replaces the live retry, and the retry button is hidden. |
| Safety and hallucination guard | Reason and hint text come only from the fixed approved table, through a code lookup. Nothing is generated or inferred at run time. If a code could map to more than one reason, use the fallback. Copy never names a cause outside the 5 reasons, such as fraud or credit score. "Not charged" appears only when the status is final-declined. The 6 strings (5 reasons plus fallback) need compliance review before production, because they describe credit decisions. |

### Decision log

| Decision | Why | What we give up |
| --- | --- | --- |
| The hint stays a one-line text instruction. One-tap fixes such as repaying or activating are deferred. | One-tap fixes need integrations that don't fit a prototype or the NOW lane. One line is enough for a user at the till to act. | Overdue and not-activated users get no shortcut yet. |
| "Try again" is allowed for 2 reasons only, once per transaction. | Every extra failed tap is another decline. Prompting retries on limit, overdue or unknown codes would break the in-store decline-rate guardrail. | Some retries that would have worked, such as unknown codes, are never prompted. |

### Evals

| Target | Pass mark | How we test it |
| --- | --- | --- |
| Accuracy | 100% (7 of 7 scenarios) show the correct reason and hint. 0 mismatches. | Scripted run of all 7 scenarios, checked against the mapping table. |
| Time on task | Median 5 seconds or less from opening Screen 2 to stating the reason and the next step, with 80% or more correct. | Moderated test with 5 or more users who match the persona. Small sample, so directional only. |
| Safety triggers | 0 strings over 12 words or containing a blocklisted word. 0 retry hints on non-retryable reasons. Maximum 1 retry prompt per transaction. Fallback fires on 100% of unmapped codes. | Automated string and logic checks on the prototype. For production, the in-store decline rate must stay within the tolerance agreed with Risk (tolerance: open). |
