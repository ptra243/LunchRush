# Lunch Rush

A match-3 cooking roguelite. Match ingredients to fill customer orders during a frantic lunch shift, survive a five-day week, and build your menu and kitchen between shifts. The goal is Overcooked-style chaos on a match-3 board, with Balatro-style builds.

## What's here

| Path | What it is |
| --- | --- |
| `prototypes/lunch-rush-roguelite.html` | Current prototype: five-day roguelite run with stars, objectives, shop, grill, sink and bosses |
| `prototypes/lunch-rush-v1.html` | First prototype: a single 2½ minute shift |
| `docs/design-doc.md` | Design doc (exported from the live doc on 28 Oct 2026) |
| `docs/pending-decisions.md` | Proposals from the latest playtest that haven't been approved yet |
| `docs/lunch-rush-builds.xlsx` | Build archetypes, build-supporting items and Balatro parallels |
| `godot/` | Empty for now; the production build will live here |

## Playing the prototypes

Open either HTML file in a browser. They're single files with no build step. On a phone, the hosted versions are easier:

- Roguelite (current): https://claude.ai/artifact/UW2TTHAeGqTAuaQuhS9Br7
- v1: https://claude.ai/artifact/SY9t8HerabTin8Nq4LUXcU
- Live design doc: https://claude.ai/artifact/VRS7nAEapUCgig7oARFjF7

The hosted links are the latest versions; the files here are a snapshot from 28 Oct 2026.

## Plan

1. Keep tuning game feel and balance in the HTML prototype.
2. Build the real game in Godot (2D, exports to Android, iOS, PC and web).
3. Keep recipes, ingredients, upgrades, customers, abilities and relics in data files rather than code.
