---
name: elm
description: Browser automation skill for Eleme (饿了么) food delivery. Use when the user wants to search restaurants, browse menus, check reviews, compare delivery options, add items to cart, apply coupons, and generate order previews on Eleme. Supports logged-in workflows for personalized results while keeping checkout/payment for user control.
version: 2.0.0
---

# Eleme (饿了么) Food Delivery

Browser automation skill for Eleme food delivery platform. Helps users search restaurants, browse menus, compare delivery options, and prepare orders with coupon optimization.

## Capabilities

| Capability | Description |
|------------|-------------|
| Search restaurants | Find restaurants by cuisine, location, rating, or keywords |
| Browse menus | View dish details, prices, descriptions, and availability |
| Check reviews | Read customer ratings, photos, and delivery feedback |
| Compare delivery | Compare delivery time, delivery fee, and minimum order across restaurants |
| Add to cart | Add dishes to cart with quantity and options selection |
| Apply coupons | Check and apply available coupons, red packets, and promotions |
| Generate order preview | Preview order total, discounts applied, and final price |

## Workflow

### Phase 1: Discovery
1. Clarify user's food preferences (cuisine, budget, delivery time)
2. Identify location/delivery address context
3. Search restaurants matching criteria
4. Present top options with key metrics

### Phase 2: Comparison
1. Compare delivery time, fee, and minimum order
2. Check ratings and recent reviews
3. Evaluate current promotions and coupons
4. Recommend best-fit restaurant

### Phase 3: Selection
1. Browse menu of selected restaurant
2. Add desired items to cart
3. Configure dish options (spiciness, size, etc.)
4. Review cart contents

### Phase 4: Optimization
1. Check available coupons and red packets
2. Apply best combination for maximum savings
3. Generate order preview with breakdown
4. Provide final recommendation

## Agent Execution Guide

### Before Starting
- Confirm user is logged into Eleme in their browser
- Verify delivery address is set
- Ask about dietary restrictions or preferences
- Clarify budget range and urgency

### During Execution
- Use browser automation for live data
- Capture screenshots of key steps
- Show delivery time, fee, and minimum order clearly
- Highlight active promotions

### Key Metrics to Capture
- **Delivery time**: Estimated arrival time
- **Delivery fee**: Shipping cost (may vary by distance/promotions)
- **Minimum order**: Minimum spend required
- **Rating**: Restaurant score and review count
- **Discounts**: Available coupons, red packets, platform promotions

### Output Format

```
### Recommended Restaurant: [Name]
- Cuisine: [Type]
- Rating: [Score] ([Count] reviews)
- Delivery: [Time] min | ¥[Fee] | Min ¥[MinOrder]
- Current promotions: [List]

### Cart Preview
- Items: [List with prices]
- Subtotal: ¥[Amount]
- Discounts: -¥[Amount]
- **Final Total: ¥[Amount]**

### Savings Applied
- Coupon: [Name] -¥[Amount]
- Red packet: -¥[Amount]
- Platform discount: -¥[Amount]

### Next Steps
1. [Specific action]
2. [Verification needed]
```

## Quality Bar

### Do:
- Always capture delivery time, fee, and minimum order
- Compare at least 3 restaurants when possible
- Show actual prices from live page
- Apply coupon optimization when available
- Be transparent about browser automation limits
- Keep checkout/payment for user control

### Do Not:
- Pretend to complete payment
- Store user credentials or session data
- Claim discounts without verification
- Ignore delivery time estimates
- Skip minimum order requirements
- Present stale or cached data as current

## References

- `references/browser-workflow.md` - Browser automation patterns
- `references/comparison-guide.md` - Restaurant comparison guidance
- `references/promotion-judgment.md` - Coupon and discount evaluation
- `references/output-patterns.md` - Output formatting guidelines
