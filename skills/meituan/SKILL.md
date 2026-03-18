---
name: meituan
description: Browser automation skill for Meituan food delivery and local services. Search restaurants, browse menus, check reviews, compare delivery options, and generate order previews. Use when user wants to order food delivery (外卖), find local services, compare restaurants, check delivery fees/times, or optimize Meituan orders.
version: 2.0.0
---

# Meituan

Browser automation skill for Meituan food delivery and local services. Helps users search restaurants, browse menus, check reviews and ratings, compare delivery options, and generate order previews.

This skill uses browser automation to interact with Meituan's public pages. It does not perform login, payment, or order placement - those remain under user control.

## Capabilities

| Capability | Description |
|------------|-------------|
| Search restaurants/stores | Search for restaurants, stores, and local services by name, cuisine, or category |
| Browse menus | View menu items, prices, descriptions, and available options |
| Check reviews/ratings | View merchant ratings, review counts, and customer feedback |
| Compare delivery | Compare delivery time, delivery fee (配送费), minimum order (起送价), and promotions across merchants |
| Add to cart | Add items to cart with options/variants selected |
| Apply coupons/red packets | Check available coupons, red packets (红包), and promotion conditions (满减) |
| Generate order preview | Preview order total with all fees, discounts, and final price |

### Key Decision Factors

When comparing options, the skill evaluates:
- **Delivery time** (配送时间): Estimated arrival time
- **Delivery fee** (配送费): Shipping cost to your location
- **Minimum order** (起送价): Minimum basket value required
- **Promotions** (满减): Full-reduction discounts and conditions
- **Merchant rating**: Overall score and review volume
- **Menu fit**: How well the menu matches the user's needs

## Workflow

### Phase 1: Discovery
Understand the user's ordering need:
- Accept a store name, dish type, cuisine, or general request
- Clarify location/delivery address if needed
- Identify ordering scenario (one-person, group, budget-focused, speed-focused)
- If the request is too broad, ask one short clarifying question

### Phase 2: Search & Browse
Use browser automation to:
- Search for matching restaurants/stores on Meituan
- Browse menu categories and item details
- Collect pricing, options, and availability
- Note delivery parameters (time, fee, minimum)

### Phase 3: Compare & Evaluate
Analyze collected information:
- Compare delivery fees and minimum orders
- Evaluate promotion conditions (满减 thresholds)
- Check ratings and review signals
- Assess menu fit for the user's scenario
- Calculate true cost including all fees

### Phase 4: Recommend & Preview
Deliver actionable guidance:
- Present best option(s) with clear reasoning
- Show comparison of key factors
- Warn about risks or trade-offs
- Generate order preview if items selected
- Provide final ordering advice

## Agent Execution Guide

### When to Use

Use this skill when the user wants to:
- Find restaurants or stores on Meituan
- Browse menus and compare prices
- Check delivery fees, times, and minimum orders
- Evaluate if a promotion (满减) is actually worth it
- Compare multiple merchants for the same dish/cuisine
- Get help deciding "这家值不值得点"
- Preview what an order would cost with all fees

### When NOT to Use

Do not use this skill for:
- Login, account access, or personal order history
- Payment processing or checkout completion
- Claiming coupons or red packets requiring login
- Address management or saved locations
- Real-time order tracking after placement

### Browser Automation Notes

- Operate on public merchant pages and search results
- Respect rate limits and avoid rapid-fire requests
- Handle dynamic content loading (infinite scroll, lazy load)
- Extract visible text and structured data only
- Stop before any payment or confirmation steps

### Data to Extract

For each merchant:
- Name, cuisine type, rating, review count
- Delivery time estimate
- Delivery fee
- Minimum order amount
- Active promotions (满减 rules)
- Menu categories and item prices

## Quality Bar

### Do
- Focus on public merchant and promotion signals
- Explain trade-offs clearly (e.g., low item price but high delivery fee)
- Optimize for the user's actual ordering scenario
- Warn when a discount looks attractive but isn't cost-effective
- Verify delivery parameters are realistic for the user's location
- Present multiple options when the choice isn't clear-cut

### Do Not
- Pretend to log in or inspect account-only pages
- Claim to retrieve orders, coupons, or personal red packets
- Store cookies, tokens, or account data
- Present public-page heuristics as guaranteed outcomes
- Complete checkout or payment on behalf of the user
- Ignore delivery fee impact on total cost

## Output

Use this structure unless the user asks for something shorter:

### Best Option
State the strongest current choice for the user's scenario.

### Why
List the main reasons.

### Comparison Factors
Summarize the most important fields: delivery fee, minimum order, time, discount, and fit.

### Risks or Caveats
List meaningful concerns: weak discount conditions, high delivery fee, long wait time, low-value bundle traps.

### Final Advice
Give a direct ordering suggestion in plain language.

## References

Read these references as needed:
- `references/browser-workflow.md` - Browser automation patterns for Meituan
- `references/comparison-guide.md` - Merchant comparison logic
- `references/promotion-judgment.md` - Discount and fee interpretation
- `references/risk-signals.md` - Common takeout decision risks
- `references/output-patterns.md` - Final answer structure
