# Shipping Delay Friction — dev spec
Site: allbirds.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The prominent 'Due to increased demand, orders may take up to 30 days to ship' statement creates significant friction and distrust regarding delivery speed, especially for first-time buyers.

## Evidence (from the live site)
> Homepage body_sample: 'Due to increased demand, orders may take up to 30 days to ship.'
> Product page (/products/anytime-ankle-sock) body_sample: 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
notes: A shipping delay notice is prominently displayed on the homepage hero and product pages, potentially deterring purchases. The 'Refund policy' is only visible in the footer.

## Required change
notes: Add a concise 'Easy Returns' or 'Satisfaction Guarantee' statement (e.g., 'Not satisfied? Easy 30-day returns.') directly adjacent to the shipping delay notice on the homepage hero and product pages, linking to the full policy.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a concise 'Easy Returns' or 'Satisfaction Guarantee' statement (e.g., 'Not satisfied? Easy 30-day returns.') directly adjacent to the shipping delay notice on the homepage hero and product pages, linking to the full policy.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_friction` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
