# Delivery Review: Evergreen Quote

## Slide 1: Delivery goal & did we hit it?

- **Goal:** By Thursday, Evergreen Quote is merged to main with green CI and running on a local cluster, serving REST and GraphQL from one database.
- **Hit?** ☒ Yes
- **Why:** The API, REST and GraphQL, and CI are merged to `main` with a green run on the merge commit (PR #13, `f6003808`, 8 of 8 tests passing). The container image and the three-pod cluster demo are done. The merge was held on Wednesday until `main` was green again after the hotfix.

## Slide 2: What shipped

- Merged PR: #13, `delivery/lead` → `main`. [github.com/asc1-student10/evergreen-quote-api-delivery/pull/13]
- Green CI run on the merge commit: conclusion success, 8 of 8 tests passing. [github.com/asc1-student10/evergreen-quote-api-delivery/actions/runs/42647755696]

## Slide 3: Two key decisions

- **Decision 1: Renters coverage deferred to a later round.** It needs a rate, validation rules, seed data, tests, GraphQL changes, and a site update. The API already rejects the new type, so this is a scope decision, not a bug.
- **Decision 2: Hold the merge to `main` on Wednesday (NO-GO), then merge once `main` was green.** `main` was red because a hotfix set the minimum age to 110, which rejected every quote. Merging onto that would have put the delivery goal and customers at risk.

## Slide 4: Risks & injects

- **Top risk:** The hotfix that broke `main`. Closed once `main` was green.
- **Other live risks:** The base-image CVE (shipping on the current image with a patched tag due next window).
- **Inject #1 (Tue):** A renters request and a base-image CVE. We said no to renters, shipped on the current base image, and tracked the CVE.
- **Inject #2 (Wed):** A hotfix broke quoting and CI on `main`. We held the merge (NO-GO), named the owner of the fix, and merged after `main` was green.

## Slide 5: What I'd do differently next round

- Check the environment (port ownership, dependencies, database count) before each working block, not after a failure.
- Require a green run on the target branch before anything reaches `main`, and protect `main` so a broken commit can't be merged.
- Run the full test suite before pushing any change to validation rules, since a one-line schema change can reject every request.

## Q&A prep

- **"Why didn't you ship renters?"** The API rejects the type today, and we don't have a rate or the rules. Adding it touches six areas and needs its own round.
- **"Why ship on an image with a known CVE?"** The flagged issue is moderate, the API isn't internet-facing this week, and the patched tag is due in the next window. We tracked it with an escalation trigger.
- **"Your branch worked. Why hold the merge?"** `main` wasn't green, and merging onto a broken `main` would have hidden the failure instead of fixing it.
- **"The demo returned quotes all week. Why does one red test matter?"** The demo showed responses with normal status codes, but the test caught the wrong premium and the hotfix's minimum age. Status codes alone don't show whether the numbers are correct.
- **"Is the service secure?"** The audit reported 5 dependency vulnerabilities. They didn't block the build, and engineering is reviewing them. The service isn't internet-facing this week.
