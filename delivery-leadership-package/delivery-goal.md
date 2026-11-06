# Delivery Goal: Evergreen Quote

## Goal

By Thursday, Evergreen Quote is merged to main with green CI and running on a local cluster, serving REST and GraphQL from one database.

## "Done" looks like

- The API answers every documented route: list, fetch by id, create with a computed premium.
- The same data answers through GraphQL, with the explorer at `/explorer`.
- `npm test` passes; the safety net holds.
- The containerized API serves the same answers as the dev server, and the CI run on the merge commit is **green**.
- The cluster demo shows three API pods behind one Service.
- A reviewed PR is merged, branch deleted.
- `delivery-leadership-package/` is complete and committed.
a
## Out of scope (this week)

- New products, rating factors, or premium logic beyond the sponsor's three base rates
- Production AWS deployment; the S3 deploy is reviewed on paper, and the live path is optional
- Changes to the marketing site beyond reviewing its deploy files
- Authentication, rate limiting, and partner onboarding
