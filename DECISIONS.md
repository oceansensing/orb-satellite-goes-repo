# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 — 2026-09-27 — Its own repository, and the server's other products to follow

The University of Delaware ORB lab's products get repositories of their own, one per sensor (`-viirs-`, `-goes-`, `-pace-`), so a sensor's products and its budgets live together and a sensor that goes quiet quiets one origin. **Published but not drawn** (the owner, 2026-09-27): the products go to Pages and R2 on a schedule and the website's map carries no layer for them, while its status line reports their health. One-way in the ordinary data-repository sense: moving a product later costs roots in the contract, an origin in the site's config and the union `check:docs` holds.
