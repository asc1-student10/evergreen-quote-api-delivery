# Decision Memo: Accepting an AI-Written Test for Missing Coverage

**Date:** Nov 9, 2026
**Author:** Ricky Cotton
**Decision area:** AI-assisted code review

## Context

On Day 3, Copilot wrote a test that checks the API rejects a quote request missing a coverage amount. The test passed on its first run. Before the team relies on it in the safety net and in CI, we need to decide whether it is trustworthy.

## Options considered

1. **Accept as written.** Quick, and it covers a real rule. But it only checks the status code, and a passing run doesn't show the test would catch a break.
2. **Reject and remove it.** No risk of a misleading check. But we lose useful coverage and must write the test by hand.
3. **Accept with changes.** Confirm it fails when the coverage rule is removed, and tighten it to check that the error names the missing field. This keeps the check and makes it meaningful, for a few extra minutes of work.

## Recommendation

Option 3: accept the test with changes, and verify it fails when the rule is broken.

## Why

The rule it protects matters to the customer: a quote without a coverage amount must not be priced. A test that would pass even if the rule were removed gives false confidence, the same kind of failure as the premium bug we found on Day 2. Checking that it fails on a broken rule takes minutes and tells us the test works.

## What would change my mind

If removing the coverage rule makes the test fail, and the test checks that the error names the missing field, I would accept it as written. If CI shows it failing, or the sponsor changes the coverage rule, I would revisit the decision.
