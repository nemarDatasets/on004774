[![DOI](https://img.shields.io/badge/DOI-10.82901%2Fnemar.on004774-blue)](https://doi.org/10.82901/nemar.on004774)

<!-- nemar:provenance -->
## Provenance

This dataset is mirrored on NEMAR from OpenNeuro.

- Source: [ds004774](https://openneuro.org/datasets/ds004774)
- DOI: [10.18112/openneuro.ds004774.v1.0.0](https://doi.org/10.18112/openneuro.ds004774.v1.0.0)

## Channel types (18 Oct 2026)

channels.tsv `type`: 17 rows in 2 files (sub-MAYO03, sub-MAYO04) had the value 'n/a', which is not a BIDS channel type. They are generic amplifier inputs named `C<n>` (e.g. C26, C27, C28, C29) with no electrodes.tsv entry, status bad and headbox n/a, i.e. inputs not connected to an electrode. Their type is now MISC; status and every other column are unchanged.

## Channel order of the MEF 3 recordings (19 Oct 2026)

The rows of the channels.tsv of the MEF 3 recordings were in acquisition order (`acquisition_channel_number` of each channel's `.tmet`). The MEF 3 readers return the channels sorted by name: pymef's session metadata, and MNE's `read_raw_mef`, which takes its order from pymef. This order does not depend on the order of the channel directories on disk: a copy with the `.timd` directories created in reverse order is read in the same order. `mne_bids.read_raw_bids` (0.20) therefore stopped with "Channel mismatch between channels.tsv and the raw data file" unless called with `on_ch_mismatch='reorder'`. The rows are now in the reader's order (sorted by channel name). Every row is unchanged; only the order changed. The acquisition order is still available from `acquisition_channel_number` in the `.tmet` files.

Files: `sub-MAYO01_ses-ieeg01_task-ccep_run-01_channels.tsv`, `sub-MAYO02_ses-ieeg01_task-ccep_run-01_channels.tsv`, `sub-MAYO03_ses-ieeg01_task-ccep_run-01_channels.tsv`, `sub-MAYO04_ses-ieeg01_task-ccep_run-01_channels.tsv`, `sub-MAYO05_ses-ieeg01_task-ccep_run-01_channels.tsv`.
