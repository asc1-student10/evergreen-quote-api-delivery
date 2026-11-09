# Go / No-Go: Merge Decision

**Date / time:** Nov 10, 2026
**Decision:** ☐ GO   ☒ NO-GO   ☐ GO WITH CONDITIONS

## CI evidence

- Latest run on `main` (run #31, push, "Hotfix: widen the age range for the senior campaign"): **red**.
- Latest run on `delivery/lead`: **green**. Link: https://github.com/asc1-student10/evergreen-quote-api-delivery/actions/runs/42627112799/job/129193600670
- Workflow file: `.github/workflows/ci.yml`
- What the workflow checked: install dependencies from the lock file; start the MongoDB 7 service container; run the API test suite (7 tests). Run #31 failed at the test step: 5 of 7 passed. The two failures were both POST `/api/quote` tests, each returning 400 because the minimum age is now 110.

## What "GO" would mean

- Merge `delivery/lead` → `main`, squash, delete the branch.
- Tag the merge commit `phase-3`.

## What "NO-GO" would mean

- Hold the merge until `main` is green on a commit that either reverts the hotfix or corrects the age rule. The current line sets the minimum (110) above the maximum (100), so it cannot be a valid fix as written.
- Owner of that condition: Engineering Team.
- Also hold until `delivery/lead` is green when run against that updated `main`. Owner: Ricky Cotton.
- Re-evaluate at: Thursday 4PM.

## My call

We are holding the merge today. The one thing driving this call is that `main` is red because the hotfix sets the minimum age to 110, which rejects every quote and is the likely cause of the customer outage. Merging our branch onto a broken `main` would put our delivery goal, a merge with green CI, at risk and would make the outage harder to trace. The call flips to GO when `main` is green on a corrected commit and our branch is green against it, with the instructor's agreement that customers can be told the fix is in.
