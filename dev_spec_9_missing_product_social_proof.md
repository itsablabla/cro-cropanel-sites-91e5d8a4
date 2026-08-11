# No Product Social Proof — dev spec
Site: allbirds.com · Priority 9 · High · Effort: High (5+ days)

## Problem
Product cards on collection pages lack visible social proof (e.g., star ratings, review counts), making it difficult for buyers to quickly assess product quality and popularity, leading to hesitation.

## Evidence (from the live site)
> Inventory for '/collections/shop-all-26' shows product listings with images, titles, and prices in the body_sample, but no explicit mention of star ratings or review counts on individual product cards.

## Current state
notes: The collection page displays product images, titles, and prices. There are no visible average star ratings or review counts directly on individual product cards.

## Required change
notes: Integrate average star ratings and the total number of reviews directly onto each product card on the collection page to provide immediate social proof and aid product selection.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Integrate average star ratings and the total number of reviews directly onto each product card on the collection page to provide immediate social proof and aid product selection.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_product_social_proof` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
