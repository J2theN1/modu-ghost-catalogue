# Methods — how the catalogue was collected and scored

## Collection

- **Sensor:** a Google Pixel 9 handset's GNSS chipset, used receive-only.
  The phone logged raw GNSS measurements (including per-satellite Doppler /
  pseudorange-rate) to a local database on-device; a LAN sync (5-minute
  timer) carried each day's capture to the workstation. The handset never
  transmitted anything for this programme.
- **Scoring host:** a local workstation (Lenovo Legion, Ubuntu) running
  the ghost-sat pipeline from the `modu-rf-lab` repository
  (`tools/ghost-sat`), on a 15-minute watch timer
  (`modu-ghost-watch.timer`, `ghost_watch.py`).
- **Campaign:** continuous sweeps, 2026-10-10 → 2026-10-17 UTC, ending
  when the handset went dark (an unrelated software update changed its
  state; collection has not resumed — the snapshot is final).

## Pipeline (per sweep)

1. **Catalogue/TLE:** `tle_catalog.py` maintains the 103-satellite watch
   list and fetches current TLEs from CelesTrak's public groups
   (gps-ops, glo-ops, beidou, galileo). The TLE source group and date for
   every mapping are recorded in each row's `notes`.
2. **Prediction:** `predict.py` propagates each TLE with SGP4 (skyfield)
   and computes the predicted Doppler and elevation for the observing
   site at each measurement epoch.
3. **Comparison:** `gnss_doppler.analyze()` pairs each measured Doppler
   with its prediction, producing `residual_hz`. Because a consumer
   handset's clock bias shifts *every* satellite's Doppler at once, the
   pipeline solves a per-epoch clock bias (`clock_correct.py`; the
   epoch's median residual is the bias estimate) and verdicts are issued
   against the de-biased residuals. A dedicated replay study in the
   estate measures the solver's effect on recorded data; the uncorrected
   failure mode — one drifting clock poisoning every verdict in the
   epoch — is documented there and is why no absolute-threshold verdict
   is issued without the solve.
4. **Persistence:** `log_observation.log_results()` writes one row per
   satellite-epoch to `observations.db` with replay protection on
   (timestamp, norad_id, svid); repeat presentations of the same epoch
   are skipped, and the apparent repeats in the data are genuine
   per-epoch measurement series with distinct residuals, not duplicates.
5. **Backfill:** on 2026-10-12, history from the watch loop's per-run
   verdict logs (2026-10-10 onward) was ingested into the store. Those
   rows' limitation (run-time instead of per-epoch timestamps) is
   recorded in their `notes` and in the datasheet's Known limits.

## Site precision note

The source store contains **no observer coordinates at all** — no
latitude/longitude column exists in either table, and nothing in the
export adds one. This datasheet names the site as West Kelowna, BC,
Canada at 0.1° precision (≈49.8°N, 119.6°W). Finer coordinates exist in
internal estate records and are deliberately not republished: the
residual analysis the catalogue supports is reproducible from public
TLEs plus site geometry at city precision, and a private home's exact
receiver position is not part of the science.

## Sanitization applied to the export (complete list)

- `observations.id` renamed to `obs_id`. All other observation columns
  exported verbatim — including `notes`, after verifying the column
  contains exactly 23 fixed provenance templates and nothing else
  (enumerated in the preparation record).
- `satellites.downlink_json` and `satellites.satnogs_name` **dropped**:
  both are NULL on all 103 rows (planned fields, never populated).
  Nothing was lost; the columns are named here so their absence is a
  recorded decision, not a silent cut.
- `satellites` gained one derived column, `observations_in_export`
  (the row count per NORAD in this snapshot), recomputed at export.
- No rows were filtered, sampled, or altered. Row counts in the exports
  were re-verified against the store after export (797,239 = 797,239).

## Relation to the IDEaS RF work

This catalogue is the frozen final state of the live catalogue cited in
MODU's IDEaS RF Data Fusion pursuit (Component 1b) as evidence for the
receiver clock-bias solver + ghost-object detection claim: a pipeline
that ingests noisy RF-domain data, validates it against expected
models, tags stale data instead of using it silently (STALE_TLE), and
maintains a single queryable fused picture. The proposal pack's figures
(615,394 observations / 103 satellites, live-read 2026-10-14) describe
this same store mid-growth; this release supersedes them with the
final count. Publishing the dataset makes that evidence claim
independently checkable — anyone can recompute the verdict mix, the
residual distributions, and the clock-bias behaviour from the export
and the public TLE archive.
