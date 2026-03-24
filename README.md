# MLB Line Scout v1

Single-file browser-based MLB betting model. No server, no build step, no npm. Deploys to GitHub Pages.

## Features

- **Auto-fetch** from ESPN public API: game slate, run lines, team stats, starting pitcher ERA/WHIP/K9
- **9-component weighted formula**: Pythagorean W%, starting pitcher, bullpen, lineup OPS, recency, rest, park factor, context, platoon
- **Player Props tab**: pitcher strikeout projections, team HR projections, team total bases projections
- **Park factors** for all 30 MLB stadiums (Coors +35%, Oracle Park -8%)
- **Baseball Reference scrapers** (copy+paste): team stats, pitching (FIP, BABIP), batting (ISO, SLG, HR/PA)
- **Post-mortem training loop** with Pearson correlation analysis per component
- **Totals model** with park factor and K-rate adjustments
- **Customizable date picker** for past/future slates
- **Weight editor** with changelog tracking

## Deploy

1. Create repo `MLB_Agent` on GitHub
2. Upload `index.html` to root
3. Enable GitHub Pages (main branch, root)
4. Add `.nojekyll` file
5. Visit `kglennon19.github.io/MLB_Agent/`

## Data Tiers

| Tier | Source | Data | Action Required |
|------|--------|------|-----------------|
| Auto | ESPN API | Slate, odds, team stats, pitcher ERA/K9 | None — loads on page open |
| Sync | Baseball Reference | Pythagorean W%, BABIP, FIP, ISO, SLG | Copy+paste scraper in F12 |

## Formula Weights (default)

| Component | Weight | Key Metric |
|-----------|--------|------------|
| Starter | 28% | ERA/FIP edge × innings |
| Base | 22% | Pythagorean W% differential |
| Bullpen | 12% | Team bullpen ERA |
| Lineup | 10% | Team OPS/wRC+ |
| Recency | 8% | Last-10 scoring rate |
| Rest | 6% | Pitcher days rest |
| Site | 6% | Home field + park factor |
| Context | 4% | Travel, interleague |
| Platoon | 4% | Starter hand vs lineup (dormant) |

*MLB Line Scout v1 — March 2026*
