# Browser Workflow for Meituan

This reference describes browser automation patterns for interacting with Meituan food delivery and local services.

## Entry Points

### Meituan Waimai (Food Delivery)
- URL: `https://waimai.meituan.com/` or `https://www.meituan.com/waimai/`
- Requires location/address selection for accurate results

### Meituan Main (Local Services)
- URL: `https://www.meituan.com/`
- Covers food, entertainment, hotels, and more

## Search Workflow

### 1. Set Location (if needed)
- Look for address/location selector
- Enter or select delivery address
- Wait for page refresh with localized results

### 2. Search for Merchants
- Use search bar to find restaurants by name or cuisine
- Or browse category listings
- Capture search result listings

### 3. Extract Merchant List Data
For each merchant card in search results:
```
- Name
- Rating (评分)
- Monthly sales (月售)
- Delivery time (配送时间)
- Delivery fee (配送费)
- Minimum order (起送价)
- Distance
- Main promotions visible
```

## Merchant Page Workflow

### 1. Navigate to Merchant
- Click merchant name/card from search results
- Wait for menu page to load

### 2. Extract Merchant Info
```
- Full name
- Overall rating
- Rating count
- Delivery time range
- Delivery fee details
- Minimum order amount
- All active promotions (满减 details)
- Business hours
- Announcements/notices
```

### 3. Browse Menu
- Extract menu categories
- For each item:
  ```
  - Name
  - Price
  - Description
  - Monthly sales (if shown)
  - Options/variants
  - Image (optional)
  ```

### 4. Check Reviews (if needed)
- Navigate to reviews section
- Extract:
  ```
  - Rating distribution
  - Recent review highlights
  - Common complaints/praise
  ```

## Cart & Order Preview Workflow

### 1. Add Items to Cart
- Click "Add" or "+" on menu items
- Select options if prompted
- Verify item appears in cart

### 2. View Cart Summary
- Open cart panel/modal
- Extract:
  ```
  - Item list with quantities
  - Subtotal
  - Delivery fee
  - Applied discounts
  - Final total
  ```

### 3. Check Promotions
- Look for available coupons/red packets
- Note any "满减" (full reduction) conditions
- Calculate if adding items would unlock better discounts

## Data Extraction Patterns

### Promotion Parsing (满减)
Format typically: "满{X}减{Y}" (Spend X, save Y)
- Extract threshold amount (X)
- Extract discount amount (Y)
- Calculate effective discount rate

### Delivery Fee Structure
May vary by:
- Distance
- Order amount (some have free delivery over threshold)
- Time of day
- Special promotions

### Rating Interpretation
- 4.8+: Excellent
- 4.5-4.7: Good
- 4.0-4.4: Average
- Below 4.0: Concerning

Consider review count: high rating with low count is less reliable.

## Common Selectors (Examples)

Note: Selectors change frequently. Use semantic/visible text approaches:

```javascript
// Merchant cards
[role="listitem"], .shop-item, [data-tag="shopCard"]

// Menu items
.menu-item, .food-item, [data-tag="dishCard"]

// Cart button
.cart-button, [data-tag="cart"]

// Price elements
.price, .current-price, [data-tag="price"]
```

## Error Handling

### Common Issues
- **Location required**: Prompt user for address
- **No results**: Expand search radius or try different keywords
- **Page load timeout**: Retry with longer wait
- **Dynamic content**: Wait for lazy-loaded elements

### Rate Limiting
- Add delays between actions (1-2 seconds)
- Avoid rapid-fire searches
- Respect any CAPTCHA challenges (stop and notify user)

## Safety Boundaries

### Stop Before
- Login prompts
- Payment pages
- OTP/verification steps
- Personal account pages

### Never Store
- Login credentials
- Payment information
- Personal addresses
- Session cookies

## Example Flow

```
1. Go to waimai.meituan.com
2. Set location to user's address
3. Search for "川菜" (Sichuan cuisine)
4. Extract top 5 merchant summaries
5. Navigate to highest-rated merchant
6. Extract menu and prices
7. Add example items to cart
8. Capture cart preview with totals
9. Report findings to user
```
