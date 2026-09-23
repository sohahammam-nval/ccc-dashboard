# US Protest Events — Crowd Counting Consortium dashboard

An interactive map and summary charts for the [Crowd Counting
Consortium](https://ash.harvard.edu/programs/crowd-counting-consortium/) (CCC)
dataset, covering political protest events in the United States.

**Live site:** https://sohahammam-nval.github.io/ccc-dashboard/

Currently showing CCC Phase 3: 63,145 events from January 2025 onward,
including Puerto Rico, the US Virgin Islands, Guam and American Samoa.

## About the data

CCC is a joint project of Harvard Kennedy School and the University of
Connecticut that collects publicly available data on political protest events
reported in the United States, including rallies, marches, demonstrations, and
acts of civil disobedience. Records are compiled from online print and broadcast
media, social media accounts maintained by organizers and independent
journalists, news searches, organization websites, and confirmed public
submissions.

The full dataset and its codebook, including earlier phases covering 2017–2024,
are published openly on [Harvard
Dataverse](https://dataverse.harvard.edu/dataverse/crowdcountingconsortium).

If you use the data in published work, please cite the Crowd Counting Consortium
as the source. Each dataset version on Dataverse carries its own DOI; see the
Dataverse page for the one matching the version you used.

To report a missing or mis-recorded event, use CCC's [submission
form](https://docs.google.com/forms/d/e/1FAIpQLSc3W_tb71fiEJhi379y0T6gttQ0f9nbb23bj8iicceLP_j8rQ/viewform).

## How it works

The dashboard is a static page: it loads a prepared data file and does all
filtering in the browser, with no server and no backend. Filtering is therefore
immediate, and the site costs nothing to host.

```
docs/
  index.html            the dashboard
  vendor/d3.min.js      D3 v7.9.0, bundled so the page has no external dependency
  data/
    ccc-dashboard.json  the events
    us-states.json      state and territory boundaries
```

The data file is regenerated from the published CCC dataset and committed here;
the site updates on push.

## Running it locally

The page fetches its data, so it must be served over http rather than opened
directly from the filesystem:

```bash
cd docs
python -m http.server 8000
# then open http://localhost:8000
```

## Notes on reading the data

- Crowd size is recorded for roughly 30% of events, and not at random — larger
  and more widely covered gatherings are far more likely to have an estimate.
  The participant total is a sum over those events, not an estimate of total
  turnout. The dashboard shows what share of the current selection it rests on.
- Events are located to their city or town rather than a street address, so many
  events in the same place share coordinates.
- The record depends on what sources surfaced, so thin coverage in a place or
  period may reflect reporting rather than activity.
