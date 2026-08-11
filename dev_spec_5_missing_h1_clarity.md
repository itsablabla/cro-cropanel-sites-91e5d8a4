# Missing Collection H1 — dev spec
Site: allbirds.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
The 'Shop All' collection page lacks a clear H1, which can hinder SEO and make it less immediately obvious to visitors that they are on the main product browsing page.

## Evidence (from the live site)
> H1s: `[]` (empty array) in the inventory for `/collections/shop-all-26`. The page title is 'SHOP ALL '26'.

## Current state
h1: (Missing); cta: Apply filters, Shop Men's, Shop Women's, Shop Apparel; notes: The page title is 'SHOP ALL '26', but a visible and semantically correct H1 is absent from the page content.

## Required change
h1: Shop All Allbirds: Shoes & Apparel; cta: Apply filters, Shop Men's, Shop Women's, Shop Apparel; notes: Implement a clear, descriptive H1 that confirms the user's location and purpose on the page, improving both user experience and search engine understanding.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Implement a clear, descriptive H1 that confirms the user's location and purpose on the page, improving both user experience and search engine understanding.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_h1_clarity` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
