# NEON GRID — MVP Game Spec

## Concept
Browser-based roguelike card battler. Pure static HTML/CSS/JS — no framework, no bundler, no SSR. Single index.html + optional split into game.js/style.css.

## Core Loop
1. Player starts with a small starter deck (5 cards)
2. Each run: player fights through 5 rooms (waves of enemies)
3. After each room, player picks 1 of 3 random card rewards to add to deck
4. If player HP reaches 0: game over (permadeath) — restart from room 1
5. Reach room 5 boss and beat it: WIN screen

## Cards (start simple, expand later)
- **STRIKE** — deal 6 damage
- **DEFEND** — gain 5 block (absorbs next hit)
- **SURGE** — deal 3 damage to all enemies
- **HACK** — deal 8 damage, costs 2 energy
- **PATCH** — heal 4 HP
- **OVERCLOCK** — gain +1 energy this turn

## Combat
- Player has 3 energy per turn; cards cost 1 (or 2 for HACK)
- Draw 4 cards per turn from shuffled deck
- End turn → enemy attacks → new turn
- Block refreshes each turn

## Enemies (per room)
- Room 1: Sentinel (15 HP, 4 dmg/turn)
- Room 2: Warden (20 HP, 5 dmg/turn, 3 block)
- Room 3: Hunter (18 HP, 7 dmg/turn)
- Room 4: Phantom (25 HP, alternates 0/10 dmg)
- Room 5: BOSS — ICE-9 (40 HP, 8 dmg/turn, 5 block, buffs self turn 3)

## UI
- Neon dark theme (match coming soon page palette)
- Player HP bar (cyan) + enemy HP bar (red)
- Hand of cards at bottom — click to play
- Energy pip display
- Room progress indicator (1/5)
- Card reward screen between rooms
- Game over + win screens with replay button

## Tech constraints
- ZERO external JS dependencies (no React, no lodash, nothing)
- Web fonts OK (already using Share Tech Mono)
- Single page — game replaces coming soon content on load
- Git commit after each major feature
- Run `git push origin main` after each commit
- Mobile-friendly (touch events + responsive layout)

## Commit order (do these in sequence):
1. feat(game): core game engine — state machine, combat loop, card logic
2. feat(ui): card hand rendering + click to play
3. feat(combat): enemy AI, damage/block resolution, turn flow
4. feat(rooms): room progression, card rewards between rooms
5. feat(enemies): all 5 enemy types + boss
6. feat(ux): win/lose screens, animations, polish
7. feat(mobile): touch support + responsive layout

## When done with each commit, push immediately:
git push origin main

## Notify when done:
When completely finished with all 7 commits AND pushed, run:
openclaw system event --text "Done: Neon Grid MVP game complete — all 7 feature commits pushed to GitHub Pages" --mode now
