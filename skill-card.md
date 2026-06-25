## Description: <br>
Meituan public local-life decision assistant. Compare visible merchant, delivery-fee, packaging-fee, threshold-discount, rating, ETA, distance, review-risk, refund-friction, and value signals before deciding whether to order, switch merchants, add a useful item, wait, or skip. Safe default: public visible information only; no login, no order lookup, no account coupon access, no coupon claiming, no cart mutation, no checkout, and no payment. <br>

This skill is ready for commercial/non-commercial use. <br>

## Publisher: <br>
[harrylabsj](https://clawhub.ai/user/harrylabsj) <br>

### License/Terms of Use: <br>
MIT-0 <br>

## Use Case: <br>
External users use this skill to compare visible Meituan merchant, fee, discount, delivery-time, and review-risk signals before deciding whether to order now, switch merchants, add a useful item for a threshold discount, wait, or skip a deal. <br>

### Deployment Geography for Use: <br>
Mainland China service context; global users can use it when evaluating user-provided or public Meituan-visible evidence. <br>

## Known Risks and Mitigations: <br>
Risk: Meituan prices, delivery times, stock, coupons, refund terms, and final payable amounts can change by city, address, account, time, and checkout state. <br>
Mitigation: Treat conclusions as visible-evidence decisions and require the user to verify final payable amount, address-based ETA, stock, coupon eligibility, refund terms, and payment details before ordering. <br>
Risk: Screenshots or copied cart details may include personal data. <br>
Mitigation: Redact names, phone numbers, addresses, order IDs, and payment information; do not store account-state data. <br>
Risk: Over-optimizing for discounts can lead to wasteful add-ons or weak merchant choices. <br>
Mitigation: Recommend threshold add-ons only when useful and net-positive after fees; prefer speed and merchant trust when the price difference is small. <br>

## Reference(s): <br>
- [ClawHub skill page](https://clawhub.ai/harrylabsj/skills/meituan) <br>
- [Meituan website](https://www.meituan.com) <br>

## Skill Output: <br>
**Output Type(s):** [Text, Markdown, Guidance] <br>
**Output Format:** [Markdown recommendation sections] <br>
**Output Parameters:** [1D] <br>
**Other Properties Related to Output:** [Recommendations separate checkout reality, merchant risk, confidence gaps, and user-only checks before ordering.] <br>

## Skill Version(s): <br>
2.2.0 (source: local maintenance update) <br>

## Ethical Considerations: <br>
Users should evaluate whether this skill is appropriate for their environment, review visible evidence before relying on recommendations, and apply their organization's safety, privacy, and compliance requirements before deployment. <br>
