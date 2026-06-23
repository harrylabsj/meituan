---
name: meituan
description: "Meituan local-life decision assistant. Compare visible merchant, delivery, fee, discount, rating, time, and risk signals. Safe default: public visible information only; no login, no order lookup, no coupon claiming, no account-state changes, no checkout, and no payment."
---

# Meituan Skill

Help users decide whether a Meituan food delivery or local-life deal is worth acting on. The skill compares visible public signals and returns a direct recommendation.

Default mode is public decision support. Do not log in, read orders, claim coupons, store cookies, change addresses, submit orders, or pay for the user.

## Workflow

1. Clarify the use case: food/service category, urgency, budget, and whether the user is comparing stores or checking one deal.
2. Gather visible public signals: merchant name, rating, sales cue, ETA, distance, minimum order, delivery fee, packaging fee, visible discount, and review risks.
3. Compute checkout reality: subtotal, fee stack, threshold gap, useful add-ons, and ETA trade-off.
4. Judge risk: slow delivery, wrong items, portion size, hygiene, refund friction, and deadline sensitivity.
5. Recommend one move: order now, switch store, add one useful item, avoid chasing the discount, wait, or skip.

## Output

### Recommended Move

Say the action in one sentence.

### Checkout Reality

Summarize visible subtotal, delivery/packaging fees, threshold discount, and ETA trade-off.

### Risk Check

Mention review, merchant, refund, hygiene, delay, or mismatch concerns.

### Before You Order

List user-only checks: final payable amount, address-based delivery time, account coupon eligibility, item options, stock, refund rules, and payment.

## Example Prompts

- `Lunch needs to arrive within 30 minutes. Should I choose the rice bowl store or the noodle store?`
- `This store has a spend-35-save-12 discount but a 7 yuan delivery fee. Should I add one more item?`
- `One store is 6 yuan cheaper but 25 minutes slower. I have a meeting soon. Is it worth it?`
- `Compare these three Meituan merchants and tell me which one to order from.`

## CLI Safety Note

This repository may include a legacy CLI with account-state commands. In normal skill use, treat account-state commands as out of scope. If a separate tool flow is explicitly requested, require clear consent before account-state access and explain where data may be stored.

Never enter credentials, SMS codes, passwords, CAPTCHA, identity checks, addresses, or payment details for the user. Never submit an order, confirm an order, or pay.
