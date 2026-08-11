# Mega-menu Overload — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The main navigation's mega-menu presents an overwhelming number of categories and sub-categories simultaneously, potentially leading to user decision paralysis.

## Evidence (from the live site)
> The `nav_items` list on the homepage includes 20 distinct entries, and the `body_sample` explicitly shows a deep hierarchy within categories like 'Men's Shoes' (e.g., 'Shop All Sneakers Slip Ons Sandals Active All-Weather Customer Favorites Runner NZ Cruiser Tree Runner NZ') and 'Women's Shoes' (e.g., 'Trainers Sneakers Flats Sandals Slip Ons Active All-Weather Popular Picks Tree Runner NZ Canvas Cruiser Tree Runner NZ').

## Current state
notes: The primary navigation displays a large, flattened list of categories and sub-categories (e.g., 'Men's Shoes' followed by 9 distinct shoe types, plus 'Socks' and 'Men's Apparel' all at a similar level of prominence), which can be visually dense and cognitively demanding for users.

## Required change
notes: Streamline the top-level navigation to fewer, broader categories. Implement a more structured mega-menu with clear grouping and progressive disclosure for sub-categories. Prioritize popular or high-converting categories for immediate visibility and consider a 'Shop By' filter for less common attributes.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Streamline the top-level navigation to fewer, broader categories. Implement a more structured mega-menu with clear grouping and progressive disclosure for sub-categories. Prioritize popular or high-converting categories for immediate visibility and consider a 'Shop By' filter for less common attributes.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_mega_menu_choice_overload` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
