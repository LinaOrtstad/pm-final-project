# PRD & Prototype Sprint (Module 4)

## Pick & scope with MoSCoW
- **The “Now” feature I’m scoping (name + one-line core description):** B1 Decline reason and retry hint
- **My finalized Must-Haves (after overriding the AI):** MUST HAVE

Every in-store decline shows up in the app within seconds, with merchant, amount and time. The moment of misery is a decline at the till with nothing in the app. Without a record, nothing else matters. The latency target is for backend to set, and the test is whether the persona sees it while still at the checkout.
A plain-language reason from a short fixed set, plus a fallback for unmapped codes. For example: limit reached, overdue payment, card blocked or not activated, contactless limit, technical or merchant issue. There are no silent declines, so an unknown code still says “couldn’t be approved”. This is your seed item, tightened so the message never goes blank.
A retry-or-switch signal in the same message. It is one line telling the user either “try again” or “pay another way now”. I’m moving this up from your Should. A reason alone doesn’t tell someone on autopilot, with a queue behind them, whether retrying is pointless. Without this, half of the feature’s own name is missing.
A push notification that opens straight to that declined transaction. The autopilot persona won’t go looking in the app, so the message has to reach them.
Constraint: no change to approval logic, and no exposure of risk or fraud rules in the copy. This protects the decline-rate guardrail, and the feature explains declines without changing them.
- **What I demoted from Must → Should/Won’t, and why:** Customer service contact info, as in your seed item. The goal is to make the call unnecessary, and a contact link in the decline message sends users to support instead of solving it.
Pre-decline warnings, such as low-limit alerts. They overlap with B3, which is cut.
Switching to pay now at the till. It overlaps with B4, which is cut.
Limit-increase requests and anything that loosens approvals. They put the guardrail at risk.
SMS or email channels. Push and in-app cover the persona.
Credit-score or risk-factor explanations. They carry compliance risk, and the persona doesn’t need them.

## Generate your Simplified PRD
- **One thing my PRD makes explicit that a vague brief would have missed:** Details in the funtinal requirements I think easily could have been missed

## Prompt-to-prototype sprint
- **Where did the prototype reveal a gap in my PRD logic? (what I had to update):** Didn't find any
- **My prototype: save Claude's HTML as prototype.html in 04-roadmap/, open it in your browser, and add a screenshot:** 04-roadmap/Prototype Decline Reason and Retry Hint.html
