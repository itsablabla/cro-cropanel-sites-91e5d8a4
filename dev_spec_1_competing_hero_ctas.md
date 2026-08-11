# Competing Hero CTAs — dev spec
Site: allbirds.com · Priority 1 · High · Effort: Medium (2-5 days)

## Problem
The homepage hero presents two equally weighted primary calls to action, forcing an an immediate choice between 'SHOP MEN' and 'SHOP WOMEN' rather than guiding users down a single, clear path.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN', 'SHOP WOMEN' directly below the H1.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN, SHOP WOMEN; notes: Two equally prominent CTAs in the hero section, creating decision friction.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Consolidate to a single primary CTA (e.g., 'Shop All') to reduce decision paralysis and streamline the initial user journey. Gender-specific navigation can be offered as secondary options or within the subsequent page.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate to a single primary CTA (e.g., 'Shop All') to reduce decision paralysis and streamline the initial user journey. Gender-specific navigation can be offered as secondary options or within the subsequent page.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_hero_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
