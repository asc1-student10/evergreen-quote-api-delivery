# Decision Memo: Prioritize Required API Verification

**Date:** November 06, 2026
**Author:** Ricky Cotton
**Decision area:** Day 2 scope tradeoff

## Context

The Day 2 work includes assembling and checking the quote routes, correcting the premium calculation, configuring the service and rates, and mounting GraphQL. There are also optional hands-on challenges. The available time is limited, and the core service needs to be reliable before the team moves on to packaging and deployment.

## Options considered

1. **Option A: Complete the required API work and verify it before attempting optional challenges.** This protects time for the capabilities and checks needed for the Thursday demonstration. It leaves less time for extra practice.
2. **Option B: Do an optional challenge before finishing the required API checks.** This provides additional hands-on learning, but could leave a required route or test unverified at the end of the day.
3. **Option C: Attempt all work in parallel without reserving time for verification.** This may appear faster, but makes it harder to identify which change caused a failure.

## Recommendation

I chose Option A: prioritize the required API assembly and verification, and defer the optional challenge unless the required work is complete with time to spare. I will use the test suite and documented curl checks to confirm the core behavior before moving to the next delivery stage.

## Why

The customer and sponsor need quote results that are saved, validated, and priced correctly. Completing extra practice is less valuable than confirming those essential outcomes before the API is containerized and demonstrated.

## What would change my mind

If the required API checks are complete and green by the afternoon check-in, with enough time remaining to repeat the checks afterward, I would reconsider and take on an optional challenge.
