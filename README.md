# MODU Ghost-Satellite Catalogue — GNSS Doppler Residual Observations

**Frozen snapshot v1.0.0 · 2026-10-10 → 2026-10-17 (UTC) · Published 2026-10-20**

> Licence: **CC-BY-4.0** — free use, including commercial use, with attribution to
> MODU Industries Ltd. (full text in `LICENSE`).
> Citation: MODU Industries Ltd., *MODU Ghost-Satellite Catalogue — GNSS Doppler Residual
> Observations, frozen snapshot v1.0.0 (2026-10-10 → 2026-10-17)*, GitHub release v1.0.0, 2026.
> DOI: pending — a Zenodo deposit is a separate, later step; this GitHub release is the
> canonical v1.0.0 source until then.

## What this is

797,239 per-epoch Doppler-residual observations of 103 GNSS satellites —
GPS (32), GLONASS (24), BeiDou (31), Galileo (16) — collected by a single
consumer handset (Google Pixel 9) operating as a receive-only GNSS observer
in West Kelowna, British Columbia, Canada, and scored on a local workstation
against SGP4 predictions from public CelesTrak TLEs.

Each row is one satellite at one epoch: the Doppler the receiver measured,
the Doppler the public orbit model predicted, the residual between them,
the satellite's elevation, and the pipeline's verdict on that residual.
The catalogue exists to catch the epochs where reality disagrees with the
public model — stale TLEs, anomalous residuals, and "ghost" behaviour —
which is why the pipeline that built it is called the ghost-sat pipeline.

## Files

| File | Contents | Size |
|---|---|---|
| `observations.csv.gz` | All 797,239 observation rows (CSV, gzip) | 16.0 MB |
| `observations.parquet` | Same rows, Apache Parquet (zstd) | 14.8 MB |
| `satellites.csv` | The 103-satellite catalogue table | 17.5 KB |
| `observations-sample.csv` | First 50 observation rows, for inspection | 9 KB |
| `MANIFEST.sha256` | SHA-256 of the three data files | — |

## Schema — `observations`

| Column | Type | Meaning |
|---|---|---|
| `obs_id` | int | Row number in the source store (stable within this snapshot) |
| `timestamp` | ISO 8601 UTC | Epoch of the observation (see backfill caveat below) |
| `norad_id` | int | NORAD catalogue number of the satellite |
| `name` | text | Satellite name as mapped from CelesTrak (1,018 rows unmapped = empty) |
| `constellation` | text | GPS / GLONASS / BEIDOU / GALILEO |
| `svid` | int | Space-vehicle id within the constellation (PRN/slot) |
| `observed_doppler_hz` | float | Doppler measured by the receiver, Hz |
| `predicted_doppler_hz` | float | Doppler predicted from the TLE via SGP4, Hz |
| `residual_hz` | float | Magnitude of the Doppler residual, \|observed_doppler_hz − predicted_doppler_hz\|, Hz; the signed residual is recoverable as observed_doppler_hz − predicted_doppler_hz from the two columns above |
| `elevation_deg` | float | Satellite elevation at the observing site, degrees |
| `verdict` | text | Pipeline verdict (glossary below) |
| `notes` | text | Provenance: which CelesTrak group/date the mapping came from; flags backfilled rows and ghost candidates |

## Verdict glossary

| Verdict | Rows | Meaning (as implemented in the pipeline) |
|---|---|---|
| CONSISTENT | 667,821 | Residual within tolerance after the per-epoch clock-bias solve |
| LOW_ELEVATION | 111,561 | Epoch scored at low elevation, where geometry dominates the residual |
| STALE_TLE | 11,867 | Prediction rested on a stale TLE for that object |
| NEEDS_INVESTIGATION | 4,651 | Residual anomalous; class is chronic on a few objects |
| GHOST_CANDIDATE | 1,323 | Residual exceeds the ghost threshold — a flag for review, **not** a claim of an uncatalogued object |
| NEEDS_OBSERVATION | 16 | Predicted observable but not observed |

## Coverage

- **Span:** 2026-10-10T03:03:49Z → 2026-10-17T03:59:16Z (7.04 days)
- **Per day (UTC):** Oct 10: 1,475 · Oct 11: 95,300 · Oct 12: 148,249 ·
  Oct 13: 163,472 · Oct 14: 164,665 · Oct 15: 48,372 · Oct 16: 148,165 ·
  Oct 17: 27,541
- **Per satellite:** max 10,718 (GPS BIII-9, NORAD 67588); min 1,793
  (BeiDou-2 IGSO-5, NORAD 37948); full table in `satellites.csv`
- **Observing site:** West Kelowna, BC, Canada, approx. 49.8°N, 119.6°W
  (0.1° precision — see the precision note in `METHODS.md`)

## Known limits — read before citing

1. **Frozen snapshot.** Collection stopped 2026-10-17T03:59:16Z when the
   observing handset went dark. This is a complete snapshot of a 7-day
   campaign, not a live feed; the catalogue is not growing.
2. **Backfilled rows carry run-time timestamps.** 226,154 rows (28.4%) were
   backfilled on 2026-10-12 from the watch loop's verdict logs; their
   per-epoch times were not recorded at capture, so their `timestamp` is
   the ingest run's time. Every such row says so in `notes`
   ("backfill 2026-10-12: timestamp is run_utc…"). Live rows carry true
   per-epoch timestamps. Do not do sub-hour timing analysis on backfilled
   rows.
3. **One receiver, one site.** Residuals include the handset's clock
   behaviour. The pipeline solves a per-epoch clock bias (the epoch's
   median residual) before verdicts; absolute residuals on single epochs
   should still be read with that in mind.
4. **Below-horizon epochs are included.** Elevations span −80.6° to
   +89.6°: the sweep scored predicted epochs regardless of visibility,
   which is what makes the LOW_ELEVATION class (14.0% of rows) meaningful
   as a control population rather than an error.
5. **GHOST_CANDIDATE is a pipeline flag, not a discovery claim.** 1,323
   rows across 36 NORAD ids where the residual exceeded the pipeline's
   threshold. Treat them as candidates for investigation — the file's own
   verdict name says exactly that, no more.
6. **Names are mapping products.** Satellite names/PRNs come from
   CelesTrak group files on the dates recorded in `notes`, cross-checked
   against public slot tables (GLONASS) and a validated SVID table
   (Galileo). 1,018 rows have an empty `name` (unmapped at ingest);
   `norad_id` is the reliable key.

## Provenance

Source store: `observations.db` (SQLite), the ghost-sat pipeline's
canonical store in the `modu-rf-lab` repository (tools/ghost-sat).
Figures in this datasheet were recomputed from the store and from the
exported files on 2026-10-19/20 (row counts, distinct NORAD count,
verdict mix, per-day and per-satellite counts, SHA-256 manifest) —
not copied from earlier records. Earlier documents quote smaller
live-read figures (e.g. 615,394 observations on 2026-10-14); those
were the same catalogue mid-growth and are superseded by this snapshot.
