# Browser Workflow for Eleme

## Authentication
- User must be logged in before automation begins
- Do not handle login flows or credential input
- If not logged in, prompt user to log in first

## Navigation Patterns

### Restaurant Search
1. Navigate to ele.me or open Eleme app
2. Confirm delivery address
3. Use search bar for cuisine/keyword
4. Apply filters (rating, delivery time, price)
5. Capture results page

### Menu Browsing
1. Click restaurant from search results
2. Wait for menu to load
3. Scroll through categories
4. Click dish for details/options
5. Capture dish information

### Cart Operations
1. Click "Add" button on dish
2. Select options if prompted (size, spiciness)
3. Confirm added to cart
4. View cart to verify contents
5. Capture cart summary

### Coupon Application
1. Navigate to cart/checkout page
2. Look for coupon/red packet section
3. Check available coupons
4. Apply best combination
5. Verify discount applied

## Data Capture Points

### Restaurant Card
- Name
- Rating (score + review count)
- Delivery time estimate
- Delivery fee
- Minimum order amount
- Distance
- Current promotions

### Menu Item
- Name
- Price
- Description
- Options/variants
- Popularity/sales count
- Customer photos (if available)

### Cart Summary
- Item list (name, quantity, price)
- Subtotal
- Delivery fee
- Discounts breakdown
- Final total

## Error Handling

### Page Load Failures
- Retry once after 3 seconds
- If still failing, report to user

### Element Not Found
- Scroll to ensure element is in view
- Check if page structure changed
- Report specific element missing

### Login Required
- Stop automation
- Prompt user to log in
- Resume after confirmation

## Best Practices

1. Wait for page elements before interacting
2. Take screenshots at key decision points
3. Verify prices match before and after cart
4. Double-check coupon application
5. Keep session active but don't store credentials
