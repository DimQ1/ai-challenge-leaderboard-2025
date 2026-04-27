# Leaderboard Replication Report

## Goal
Replicate the leaderboard UI and behavior from the provided static SharePoint artifacts while ensuring no corporate data is copied.

## What Was Implemented
- C# WebAssembly app using Blazor (standalone WASM) in `LeaderboardWasm`.
- Header and messaging consistent with discovered source bundle text:
  - `Leaderboard`
  - `Top performers based on contributions and activity`
  - `Loading leaderboard...`
  - `No activities found matching the current filters.`
- Interactive features included:
  - Search by person name.
  - Filter by year.
  - Filter by quarter.
  - Filter by category.
  - Sorting options.
  - Ranked leaderboard with top-3 podium.
  - Expand/collapse per-person activity detail rows.

## Data Safety / Replacement Strategy
No data from the original corporate page is included.

All records are synthetic:
- Synthetic names.
- Synthetic titles.
- Synthetic categories and point events.
- Synthetic dates and scoring values.

No original people, titles, departments, or corporate identifiers were copied into the implementation.

## Source Files
- App implementation: `LeaderboardWasm/Pages/Home.razor`
- App styling: `LeaderboardWasm/wwwroot/css/app.css`
- Layout simplification: `LeaderboardWasm/Layout/MainLayout.razor`
- GitHub Pages workflow: `.github/workflows/deploy-gh-pages.yml`

## GitHub Pages Deployment
Workflow deploys on push to `main` or `master`:
- Restores and publishes Blazor WASM.
- Rewrites `<base href>` to `/<repository-name>/`.
- Publishes `release/wwwroot` to GitHub Pages.

Expected URL format:
`https://<github-username>.github.io/<repository-name>/`
