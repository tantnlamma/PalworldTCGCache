# PalworldTCGCache

Public, read-only cache refreshed every 12 hours for DeckMetric and other data consumers.

Base URL:

```text
https://raw.githubusercontent.com/tantnlamma/PalworldTCGCache/main/
```

## Supported cache-v3 files

- `manifest.json`
- `latest/cards.json`
- `latest/sets.json`
- `latest/decks.json`
- `history/cards.csv`
- `history/colors.csv`

Consumers should read `schema_version`, `generated_at`, and `refresh_interval` from the manifest, validate a full download before replacing local data, and retain a last-known-good snapshot when a refresh fails.

## Derived data

The files below are deprecated and retained only for backward compatibility:

- `derived/decks.json`
- `derived/recommendations.json`
- `derived/synergies.json`

They do not reliably represent `payload.main` in the current deck corpus. New consumers should derive deck statistics and synergy from `latest/decks.json` on-device or in their own pipeline. Deck quantities come from each entry's `count`; `payload.soul` is a separate section and should not be included in main-deck synergy.

No GitHub authorization header is required for public raw-file requests. Do not embed repository credentials or tokens in client applications.
