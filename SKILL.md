---
name: meituan
description: "Meituan local-life decision assistant. Input a restaurant, service, product, or Meituan link; compare visible delivery fee, minimum order, discounts, ratings, distance/time, merchant risk, and value. Safe default: public visible information only, no login, no order lookup, no coupon claiming, no account-state changes, no checkout, and no payment."
---

# Meituan (美团)

Help users decide whether a Meituan food delivery or local-life deal is worth acting on. The skill should turn visible merchant, menu, promotion, delivery, and review signals into a direct recommendation: order this merchant, switch stores, do not chase the threshold discount, pay more for faster delivery, or skip because risk is too high.

Default mode is public decision support. Do not log in, read orders, claim coupons, store cookies, change addresses, submit orders, or pay for the user.

## Hard Boundaries

These rules override every workflow below.

- **No account-state actions by default**: do not log in, read order history, read account coupons, claim red packets, save cookies, change address, change cart, submit orders, or pay.
- **Checkout and payment are user-only**: never click settlement, submit order, final confirmation, payment, bank, wallet, installment, or payment-provider controls.
- **Visible evidence only**: use browser-visible public pages or user-provided details. If final price requires account coupons, address, checkout, or payment method, mark it as user-only verification.
- **Privacy**: do not store cookies, addresses, phone numbers, names, order data, or account coupon data. Redact personal data if it appears unexpectedly.
- **Stop at account walls**: if login, CAPTCHA, identity check, address selection, order page, coupon wallet, or payment appears, stop and hand control to the user.

## When To Use

Use this skill when the user mentions 美团, 外卖, 到店团购, local-life merchants, or a purchase decision shaped by distance, delivery time, minimum order, packaging fee, delivery fee, threshold discounts, merchant reviews, or refund practicality.

Prefer other skills when:

- The user wants cross-platform product price comparison: use a shopping comparison skill.
- The user wants account/order troubleshooting: ask the user to operate their own app and only provide general guidance.
- The task requires private coupons or order history: keep this skill in public mode unless the user explicitly authorizes a separate account-state tool flow.

## Workflow

### 1. Clarify The Use Case

Capture:

- food/service category
- location or delivery area if user provides it
- urgency, such as lunch break, hungry now, dinner planning, or no rush
- budget and minimum acceptable quality
- whether the user is comparing merchants, deciding about threshold discounts, or checking a specific store

Ask one short follow-up only when missing context would change the recommendation.

### 2. Gather Visible Candidates

Use visible public information from search results, merchant pages, user screenshots, or user-provided cart details.

For each candidate, capture when visible:

- merchant name
- rating and recent review cues
- monthly sales or popularity cue
- distance or delivery ETA
- minimum order
- delivery fee
- packaging fee
- visible discount or threshold promotion
- likely cart subtotal or representative item price
- repeated review risks: slow delivery, wrong items, portion size, hygiene, stale food, refund friction

Re-snapshot after changing location, filters, merchant, category, or promotion view.

### 3. Compute Checkout Reality

Do not judge by headline discount alone.

Compare:

- food or service subtotal
- minimum order gap
- delivery fee
- packaging fee
- visible threshold discount
- whether add-on items are useful or only wasteful
- ETA difference and user urgency

If the final payable amount depends on account coupons, address, membership, or payment method, state that it must be verified by the user before ordering.

### 4. Risk And Time Decision

Use these decision rules:

- For lunch rush, work breaks, appointments, and hungry-now scenarios, ETA can outweigh a small discount.
- For low-value solo meals, moderate merchant risk may be acceptable if the downside is small.
- For expensive, shared, deadline-sensitive, hygiene-sensitive, or gift-like orders, weak merchant trust should strongly reduce recommendation strength.
- Do not chase a threshold discount when the extra item is not useful or the fee gap eats the discount.
- Recommend paying slightly more when it materially improves delivery certainty or merchant trust.

### 5. Recommend One Move

End with a direct action:

- order this merchant now
- switch to another merchant
- add one specific useful item to cross threshold
- do not add anything just for the promotion
- wait or search again
- skip this store

## Output

Use this structure unless the user asks for something shorter:

### Recommended Move

Say the action in one sentence.

### Checkout Reality

Summarize visible subtotal, delivery/packaging fees, threshold discount, and ETA trade-off.

### Risk Check

Mention review, merchant, refund, hygiene, delay, or mismatch concerns.

### Before You Order

List user-only checks: final payable amount, address-based delivery time, account coupon eligibility, item options, stock, refund/after-sales rule, and payment.

## Example Prompts

- `午饭 30 分钟内要吃到，黄焖鸡和麻辣烫两家怎么选？`
- `这家满 35 减 12，但配送费 7 元，要不要为了满减再加一个小菜？`
- `这家便宜 6 元但晚 25 分钟，今天赶会，值得吗？`
- `帮我比较这三个美团商家，只给我该点哪家和下单前核对项。`
- `这家评价有点一般，但离我近，适合现在点吗？`
- `截图里这个团购券看起来便宜，帮我判断有没有隐藏门槛。`

## Optional CLI Notes

This repository may include a CLI for public restaurant search and legacy account-state commands. In normal skill use, treat account-state commands as out of scope.

If a separate tool flow is explicitly requested by the user, require clear consent before any account-state action and explain where data may be stored. Never enter credentials, SMS codes, passwords, CAPTCHA, identity checks, addresses, or payment details for the user.

## Quality Bar

Do:

- Optimize for the user's immediate decision, not a menu recap.
- Separate headline discount from real cost.
- Treat ETA and refund practicality as first-class decision inputs.
- Say what the user should verify manually before ordering.
- Stop at account walls, checkout, address, order, coupon-wallet, payment, or identity screens.

Do not:

- Log in or read account pages by default.
- Claim account coupons or final payable price are available unless the user provides visible evidence.
- Save cookies, orders, addresses, phone numbers, or account data.
- Submit an order, confirm an order, or pay.
- Recommend threshold add-ons that the user does not actually need.
