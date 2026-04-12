# STARFALL — Evaluation Suite

63 checks across gameplay, UX, audio, persistence, and technical correctness.  
Last updated: April 2026. All checks passing on current build.

---

## 1. Core Architecture (8 checks)

- [x] Single `index.html` file — no external assets required
- [x] Phaser 3.60.0 loads via CDN; game boots without internet after first load
- [x] All 30 scenes registered in `new Phaser.Game({scene:[...]})` — no duplicates
- [x] `localStorage` read/write symmetry — every `getItem` key has a matching `setItem`
- [x] No global variable leaks — all state via `Phaser.Data.DataManager` registry
- [x] Drip spawner timers cleaned up on wave clear / game over / stage clear
- [x] Physics groups use `maxSize` to prevent unbounded object creation
- [x] Dead objects deactivated and pooled — not destroyed and recreated

---

## 2. Game Flow (10 checks)

- [x] FTUX gate fires on first click or keypress — no double-gate
- [x] Music plays immediately on FTUX screen load (no silence before click)
- [x] "A long time ago..." intro: 2.6s total (was 6s)
- [x] Logo zoom: 3.0s with 2s of full visibility before fade
- [x] Crawl covers full war story — all 3 episodes, no EP I-only framing
- [x] EP I Briefing screen shown after callsign entry, before difficulty select
- [x] Pilot carousel: 6 pilots, slides in/out, each shows name + ability + bio
- [x] Episode completion tracking via `localStorage` (sf_ep1_complete etc.)
- [x] Mid-episode save/resume between episodes
- [x] SPACE-to-skip on crawl and boss dossier — pacing preserved for repeat plays

---

## 3. HUD (7 checks)

- [x] Top strip: strict 2-row layout — no element overlaps at any time
- [x] Row 1: avatar | pilot name (left) — score + combo inline (centre) — wave (right)
- [x] Row 2: lives icons (left) — enemies left (centre) — difficulty badge (right)
- [x] Combo multiplier baked into score text (e.g. `9,800 ×4`) — fixed font size, never overflows
- [x] Enemies left counter shows correct remaining count, clears when wave done
- [x] Boss HP bar replaces wave counter during boss fight
- [x] Bottom strip: SHD/HP bars (left) — AMMO bar (right) — no overlaps

---

## 4. Episode I — Desert Sector (8 checks)

- [x] 3 combat waves + boss wave (W4 = boss)
- [x] Kill targets: W1=25, W2=28, W3=30
- [x] Drip spawner: enemies enter from top, sides, and centre — no batch spawn gaps
- [x] Finite ammo — NO AMMO warning shown when empty
- [x] Supply tents spawn every 16s, drift across screen, collected on overlap
- [x] Wave 3 Miniboss (Viper Lieutenant) spawns at 3s into wave
- [x] Boss Dossier card with 5s countdown before Desert Viper fight
- [x] Stage clear → EP II bridge button with mechanic preview card

---

## 5. Episode II — Ice Reach (8 checks)

- [x] 3 combat waves + boss (Wave 3 = boss transmission → boss)
- [x] Thermal gauge replaces shield — drains 4 pts every 3s passively
- [x] Freeze mines: contact freezes ship to 30% speed for 3s
- [x] Ice shards: multi-directional, large ones shatter into 2 smaller on bullet hit
- [x] Supply crates: spawn every 22s, restore 35 ammo + 10 thermal
- [x] Pilot swap offered after Wave 2 clears — PilotSwapScene launches
- [x] Boss Transmission (Commander Vreth taunt) before The Glacier fight
- [x] The Glacier: 3 hangar bays destroyed sequentially; each triggers drone wave

---

## 6. Episode III — The Veil (9 checks)

- [x] 3 combat waves + boss (Wave 3 → Ep3BossTransmission → boss)
- [x] Energy system: 100 max, costs 2 per shot, regens 3 per 500ms
- [x] Sonar Pulse [Q]: 5 charges, reveals all enemies + boss for 3s, charge restored on wave clear
- [x] Phantom Scouts: alpha=0 until they shoot (brief 220ms flash on fire)
- [x] Shade Carriers: spawn 3 phantom drones on death, wave target increments
- [x] Void Rifts: gravitational pull, damage at <0.7× radius, ASTRA immune
- [x] The Sovereign: fully cloaked (alpha=0), bullets blocked until Sonar-revealed
- [x] Boss reveals briefly when shooting — player can shoot back reactively
- [x] Stage clear: itch.io CTA + full FITZ debrief sequence

---

## 7. Audio (6 checks)

- [x] Menu track: D minor theme, melody-first, plays from FTUX → crawl → callsign → EP I briefing
- [x] Game track: upbeat driving theme, plays during all wave gameplay
- [x] Boss track: intense chromatic tension, plays during all boss fights
- [x] Crawl track: same D minor theme, builds layer by layer (melody → bass → pads → drums)
- [x] AudioContext unlocked on first user gesture — no silent first session
- [x] Music continues uninterrupted across scene transitions (no stop/start gaps)

---

## 8. Persistence & Sharing (4 checks)

- [x] High scores saved per episode (`sf_hi`, `sf_hi_ep2`, `sf_hi_ep3`)
- [x] Run history stored per episode — last 5 runs with pilot, score, wave, difficulty
- [x] Pilot name persists across sessions (`sf_pilot`)
- [x] Copy Score button on all game over screens — clipboard text includes EP, pilot, score, wave, difficulty

---

## 9. Polish & UX (3 checks)

- [x] STARFALL logo has no episode subtitle — shared cleanly across all screens
- [x] Pilot carousel: 6 pilots, cinematic slide animation, full ability info on each card
- [x] FITZ dialogue lines unique per wave and episode — no repeated lines

---

*All 63 checks passing — April 2026*
