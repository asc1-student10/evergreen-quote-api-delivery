# Stakeholder Status Update: Evergreen Quote

**To:** Priya Ramanathan, Project Sponsor
**From:** Ricky Cotton
**Date:** Monday, Nov 9, 2026

## What shipped today
- All Day 2 tasks complete: quote routes assembled and verified against the seeded data, and POST validation returns 400 for invalid input.
- Premium-order fix applied; `npm test` passes all tests.
- GraphQL mounted; explorer queries and `createQuote` verified against the REST data.
- Service name set in `.env`; sponsor rates applied and checked.

## What slipped (and why)
- **Renters coverage: not in this week.** The API rejects `"renters"` today. Adding it needs a new quote type, a rate we don't have, and changes to seed data, tests, GraphQL, and the site dropdown. It needs its own round.
- **Base image: shipping on the current `node:22-alpine` this week.** The scan flagged a moderate-severity CVE. The API is not internet-facing this week, and the patched tag arrives in the next platform window. Tracked as risk R7. Added to our Github Project as well.

## What's next (tomorrow)
- Build and run the container image.
- Enable the CI workflow and review the first run.
- Review the site's S3 deploy artifacts.

## What I need from you
- **By 11:00AM Tuesday, confirm that renters goes into a later round.** If it does, provide the rate, who approves it, and any age or coverage rules.
- **By 11:00AM Tuesday, confirm you agree with shipping on the current base image** so the container build can proceed.
