# Evergreen Quote: Vision Brief

## Product
**Name:** Evergreen Quote API (Phase 3 service delivery)
**Delivery week:** 3
**Delivery Lead:** Ricky Cotton
**Engineering team (represented by):** 
**GitHub Project board:** 

## Who is the customer?
Two groups. The first is Evergreen website visitors who want a quick estimate for auto, home, or life coverage and expect the number to be right and to stay the same when they come back. The second is partners who want to request quotes programmatically instead of through the website. Today, both get a page that computes a number and forgets it.

## What pain does Evergreen Quote remove?
Each quote has to be saved, retrieved, and priced the same way every time. Right now a visitor who returns for a quote gets a new, unrelated number, and a partner has no reliable way to request one. The service gives both groups one stored, validated record for each quote, available through REST for the website and GraphQL for partners. A bad input gets a clear error instead of a wrong price.

## What does "good" look like at end of the week?
- The API returns the six seeded quotes from MongoDB through both REST and GraphQL.
- The test suite passes in full, and the GitHub Actions CI run is green on the merged PR.
- The service runs from a container image and on a local Kubernetes cluster with three API pods and one MongoDB pod in Running.
- Premiums match the sponsor's announced rates, and a request with a bad input returns a 400 with a clear message.

## What are we explicitly NOT doing this week?
- New products, new rating factors, or changes to how premiums are calculated beyond the sponsor's three rates.
- Production AWS deployment. The S3 deploy is reviewed on paper only, and the live path is optional.
- Changes to the marketing site beyond reviewing its deploy files.
- Authentication, rate limiting, or any partner-facing onboarding.

## How will we know if it worked?
- All tests passing locally, and a green CI run on the Thursday PR.
- Zero premiums that differ from the sponsor's rate table in a spot-check of the six seeded quotes plus one new quote.
