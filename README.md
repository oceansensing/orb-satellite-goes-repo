# orb-satellite-goes-repo

The University of Delaware ORB lab's **GOES-19** products: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Live since 2026-09-27**, on the schedule in its workflow (`3 2,8,14,20 * * *` UTC). `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

ORB's daily GOES-19 **sea surface temperature** composite (`NOAA_GOES19_SST_clean_comp`, composited from its cleaned GOES-19 SST), over 16-52 N, 100-50 W, as `sst-goes.json` (degrees C), regridded to 0.04 degree with `regional: true` and `windowDays: 1`.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: `NOAA_GOES19_SST_clean_comp`, 1989 x 2778 at 0.018 degree, one composite a day (stamped about 10:55 UTC) since 2025-10-26. The newest was 30 hours old that afternoon and one day of the preceding 33 was missing. p1 8.3, median 30.0, p99 31.9 degrees C; 46% of cells hold a value.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: the other University of Delaware ORB repositories, `orb-satellite-viirs-repo`, `orb-satellite-goes-repo` and `orb-satellite-pace-repo`.

**Which document gets what, and what "update docs" means across all
twenty repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all twenty, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
