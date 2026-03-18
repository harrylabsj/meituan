# Meituan Skill v2.0.0

Browser automation skill for Meituan food delivery and local services.

## Overview

This skill helps users make better Meituan ordering decisions through browser automation. It can search restaurants, browse menus, check reviews, compare delivery options, and generate order previews.

## Features

- 🔍 **Search restaurants/stores** - Find merchants by name, cuisine, or category
- 📋 **Browse menus** - View items, prices, descriptions, and options
- ⭐ **Check reviews/ratings** - See merchant ratings and customer feedback
- 🚚 **Compare delivery** - Compare delivery time, fees, minimum orders, and promotions
- 🛒 **Add to cart** - Add items with options selected
- 🎫 **Apply coupons/red packets** - Check available promotions and 满减 conditions
- 🧾 **Generate order preview** - Preview total cost with all fees and discounts

## Key Decision Factors

The skill evaluates these factors when comparing options:
- **Delivery time** (配送时间) - Estimated arrival
- **Delivery fee** (配送费) - Shipping cost
- **Minimum order** (起送价) - Minimum basket value
- **Promotions** (满减) - Full-reduction discounts
- **Merchant rating** - Overall score and reviews
- **Menu fit** - Match to user's needs

## Usage

Activate this skill when the user wants to:
- Find restaurants on Meituan
- Compare delivery options
- Check if a promotion is worth it
- Get help deciding "这家值不值得点"
- Preview order costs

## Workflow

1. **Discovery** - Understand user's ordering need
2. **Search & Browse** - Use browser automation to find and explore merchants
3. **Compare & Evaluate** - Analyze delivery fees, promotions, and ratings
4. **Recommend & Preview** - Deliver actionable guidance with order preview

## Safety Notes

- Operates on public merchant pages only
- Does not perform login or payment
- Does not access personal account information
- Respects rate limits and avoids rapid requests

## References

- `references/browser-workflow.md` - Browser automation patterns
- `references/comparison-guide.md` - Merchant comparison logic
- `references/promotion-judgment.md` - Discount interpretation
- `references/risk-signals.md` - Decision risk signals
- `references/output-patterns.md` - Answer structure

## Version

2.0.0 - Browser automation support for food delivery and local services
