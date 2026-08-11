# Vague Hero H1 — dev spec
Site: allbirds.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
The hero H1 presents a brand promise that, while positive, doesn't immediately guide visitors with specific product intent, potentially delaying their journey.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN', 'SHOP WOMEN'. The H1 is a general statement about the brand's values rather than a direct solution to a common visitor need.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN, SHOP WOMEN; notes: The H1 is a strong brand statement but lacks direct product-finding guidance. The CTAs are good for segmentation.

## Required change
h1: Find Your Next Favorite Pair. Naturally Comfortable.; cta: Shop Men's Shoes, Shop Women's Shoes; notes: Rephrase the H1 to be more action-oriented for new visitors, while still highlighting core brand benefits. This helps visitors quickly understand what they can do here.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Rephrase the H1 to be more action-oriented for new visitors, while still highlighting core brand benefits. This helps visitors quickly understand what they can do here.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_vague_brand_promise` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
