# Transparent Shipping Fee — dev spec
Site: allbirds.com · Priority 4 · High · Effort: Medium (2-5 days)

## Problem
While the condition for free shipping is prominent, the specific cost for orders not meeting this threshold is only explicitly revealed after adding an item to the cart.

## Evidence (from the live site)
> The claim 'Free ground shipping on orders over $100' is visible on the homepage, shop all page, and product pages. However, the explicit cost of '$5.00' for shipping when the order is under $100 is primarily disclosed within the 'Added to Cart Spend more to earn free shipping! Shipping $5.00 Subtotal' snippet, which appears after a user interacts with an 'Add to Cart' action.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: The condition for free shipping ('Free ground shipping on orders over $100') is clearly stated across multiple pages. However, the specific $5.00 shipping fee for orders below this threshold is not explicitly shown on product or collection pages before an item is added to the cart, only appearing in the 'Added to Cart' confirmation.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: To enhance transparency, explicitly state the $5.00 shipping fee for orders under $100 alongside the free shipping claim on product and collection pages. For example, 'Free ground shipping on orders over $100. Otherwise, a flat $5.00 shipping fee applies.'

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN To enhance transparency, explicitly state the $5.00 shipping fee for orders under $100 alongside the free shipping claim on product and collection pages. For example, 'Free ground shipping on orders over $100. Otherwise, a flat $5.00 shipping fee applies.'
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_delayed_shipping_cost_disclosure` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
