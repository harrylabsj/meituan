# Eleme (饿了么) Skill v2.0.0

Browser automation skill for Eleme food delivery platform.

## Overview

This skill enables browser-based automation for Eleme food delivery, helping users:
- Search and compare restaurants
- Browse menus with live pricing
- Check reviews and ratings
- Compare delivery options (time, fee, minimum order)
- Add items to cart
- Apply coupons and promotions
- Generate order previews

## Version

**2.0.0** - Major update with browser automation support

## Requirements

- User must be logged into Eleme in their browser
- Delivery address should be pre-configured
- Browser automation environment available

## Capabilities

| Feature | Status |
|---------|--------|
| Restaurant search | ✅ |
| Menu browsing | ✅ |
| Review checking | ✅ |
| Delivery comparison | ✅ |
| Cart operations | ✅ |
| Coupon application | ✅ |
| Order preview | ✅ |

## Usage

The skill is triggered when users mention:
- "饿了么"
- "点外卖"
- "Eleme"
- "food delivery"
- Related restaurant/ordering queries

## Workflow

1. **Discovery** - Find restaurants matching user preferences
2. **Comparison** - Compare delivery metrics and reviews
3. **Selection** - Browse menu and add items to cart
4. **Optimization** - Apply coupons and generate preview

## Limitations

- Does not handle payment/checkout
- Requires user login
- Does not store user data or credentials
- Real-time data depends on browser session

## References

- `SKILL.md` - Main skill documentation
- `references/browser-workflow.md` - Browser automation patterns
- `references/comparison-guide.md` - Restaurant comparison guidance
- `references/promotion-judgment.md` - Coupon evaluation
- `references/output-patterns.md` - Output formatting

## Changelog

### v2.0.0 (2025-03-18)
- Added browser automation support
- New capabilities: restaurant search, menu browsing, cart operations
- Added coupon optimization workflow
- Added delivery comparison (time, fee, minimum order)
- Restructured with 4-phase workflow
- Added comprehensive agent execution guide
