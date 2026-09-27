# orb-satellite-goes-repo: the founding plan and running record

The University of Delaware ORB lab's **GOES-19** products. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Live since 2026-09-27.**

## What it is for

ORB's daily GOES-19 **sea surface temperature** composite (`NOAA_GOES19_SST_clean_comp`, composited from its cleaned GOES-19 SST), over 16-52 N, 100-50 W, as `sst-goes.json` (degrees C), regridded to 0.04 degree with `regional: true` and `windowDays: 1`.

## Where the data comes from

The University of Delaware's Ocean Remote sensing laboratory (ORB) serves its processed products openly from its own ERDDAP, `https://basin.ceoe.udel.edu/erddap`, with no login. Every dataset there carries the same license text: the data *"may be used and redistributed for free but is not intended for legal use, since it may contain inaccuracies"*. More of that server's products are expected to join (the owner, 2026-09-27), which is why the site's fetcher, `scripts/fetch-erddap.py`, is written for the server and takes a product as a row. **Read 2026-09-27**: `NOAA_GOES19_SST_clean_comp`, 1989 x 2778 at 0.018 degree, one composite a day (stamped about 10:55 UTC) since 2025-10-26. The newest was 30 hours old that afternoon and one day of the preceding 33 was missing. p1 8.3, median 30.0, p99 31.9 degrees C; 46% of cells hold a value.

## The first live run — 2026-09-27

Dispatched once the owner's secrets and Pages were in: green on its first
run, build, Pages and R2. Read live: sst-goes at the 2026-09-26 10:55 UTC composite (30 hours old), 1251 x 901, R2's tree 7 files, every root fresh against its
budget. The land control read 0.0-0.4% of the Kansas-Missouri box filled on
the first local run, and the fetcher's run log prints it every run. The
schedule was turned on in the same commit as this entry.

## Open

1. Re-measure `max_age_hours` after a week of scheduled runs.
2. The server's other GOES products, as the owner names them.

## The workflow's packages come from the site — 2026-09-27

The publish workflow installs `site/scripts/requirements-erddap.txt`, one file
per fetcher family, instead of naming packages in its own `pip install`
line. Dependabot reads requirements files and never a workflow line: an
inline pin elsewhere had carried `requests` 2.32.3, a version with two
advisories, unflagged. The site's `check:docs` now refuses an inline package
here. Confirmed by a dispatched run, green on build, Pages and R2.
