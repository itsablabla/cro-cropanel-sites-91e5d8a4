# Unlabeled Form Inputs — dev spec
Site: allbirds.com · Priority 6 · High · Effort: Low (0.5-2 days)

## Problem
Forms across the site (email signup, 'Get Notified') rely on implicit labeling (e.g., placeholder text or aria-label) rather than explicit `<label>` elements, reducing clarity and accessibility for some users.

## Evidence (from the live site)
> On the homepage, the email signup form is `{"n_inputs": 1, "labels": [], "submit": "Sign Up"}`. Similar forms appear on collection and product pages. While `tech.inputs_unlabelled: 0` suggests an accessible name exists (e.g., via `aria-label` or `placeholder`), the `labels: []` array confirms the absence of a visible `<label>` element.
> On `/products/anytime-ankle-sock`, a form is present as `{"n_inputs": 1, "labels": [], "submit": "Get Notified"}`. Similar to the email signup, `labels: []` indicates no explicit `<label>` element, despite `tech.inputs_unlabelled: 0` suggesting an accessible name is present.

## Current state
notes: Email input fields (for signup and notifications) are present with submit buttons, but lack explicit <label> elements. Contextual text or placeholders provide some guidance, but the fields themselves aren't explicitly labelled for all users.

## Required change
notes: Add explicit `<label>` elements associated with all single-input fields (e.g., email address) to improve clarity and accessibility for all users, including those using assistive technologies.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add explicit `<label>` elements associated with all single-input fields (e.g., email address) to improve clarity and accessibility for all users, including those using assistive technologies.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_implicit_input_labeling` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
