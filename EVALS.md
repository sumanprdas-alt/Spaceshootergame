# STARFALL — Evaluation Suite

Full check list across gameplay, UX, audio, mobile, persistence, and technical correctness.  
Last updated: April 2026.

---

## 1. Core Architecture (8 checks)

- [x] Single `index.html` — no external assets required
- [x] Phaser 3.60.0 via CDN; browser-cached after first load
- [x] All 30 scenes registered in `Phaser.Game` — no duplicates
- [x] `localStorage` read/write symmetry — every `getItem` has a `setItem`
- [x] All state via `Phaser.Data.DataManager` registry — no global leaks
- [x] Drip spawner timers cleaned up on wave clear / game over / stage clear
- [x] Physics groups use `maxSize` — no unbounded object creation
- [x] Dead objects deactivated and pooled — not destroyed and recreated

---

## 2. Game Flow (10 checks)

- [x] FTUX gate: fires on first click or tap — no double-gate
- [x] Music plays immediately on FTUX load — no silence before gesture
- [x] "A long time ago..." intro: 2.6s total
- [x] Logo zoom: 3.0s with ~2s of full visibility before fade
- [x] Story crawl header reads "STARFALL: THE KETHARAN WAR" — not Desert Sector
- [x] Crawl covers full war arc — all 3 episodes, not EP I only
- [x] EP I Briefing screen shown after callsign, before difficulty select
- [x] Music flows uninterrupted: FTUX → crawl → callsign → EP I briefing
- [x] Pilot carousel: 6 pilots, cinematic slide, each shows ability + bio
- [x] Episode completion tracked in `localStorage`

---

## 3. Mobile & Touch (12 checks)

- [x] `Phaser.Game` config: `input:{activePointers:3}` — iPhone multi-touch enabled
- [x] Viewport: `user-scalable=no`, `maximum-scale=1`, `viewport-fit=cover`
- [x] CSS: `touch-action:none` on body, canvas, `#game-container`
- [x] CSS: `user-select:none`, `-webkit-touch-callout:none` on body
- [x] `document.touchmove` preventDefault (passive:false) — stops iOS scroll bounce
- [x] EP I: `_setupTouch()` called in `create()`, `_applyTouchInput()` in `update()`
- [x] EP II: `_setupTouch()` called in `create()`, `_applyTouchInput()` in `update()`
- [x] EP III: `_setupTouch()` called in `create()`, `_applyTouchInput()` in `update()`
- [x] Joystick velocity not overwritten by keyboard block — `!this._tm?.active` guard
- [x] Joystick appears at touch origin — not fixed position
- [x] Joystick release: smooth deceleration to zero (Linear lerp, not instant stop)
- [x] Sonar ◎ button (EP III): dims when charges depleted
- [x] Tap-to-skip on all 3 crawl scenes (EP I, II, III)
- [x] FTUX controls card: detects touch device, shows mobile layout

---

## 4. Callsign / Text Input (5 checks)

- [x] `makeNativeInput()` creates a real HTML `<input>` overlaid on the canvas
- [x] `focus()` called immediately — iOS keyboard opens without extra tap
- [x] `autocapitalize="characters"` — names uppercase automatically on iOS
- [x] CONFIRM button reads HTML input value — works on mobile and desktop
- [x] `removeNativeInput()` called on scene `shutdown()` — no orphaned inputs

---

## 5. HUD (7 checks)

- [x] Top strip: strict 2-row layout — no overlaps at any time
- [x] Row 1: avatar + name (left) — score + combo inline (centre) — wave (right)
- [x] Row 2: lives icons (left) — enemies left (centre) — difficulty (right)
- [x] Combo baked into score text (`9,800 ×4`) — fixed 20px font, never overflows
- [x] Score colour: white (×1) → yellow (×2) → orange (×4/×8)
- [x] Enemies left clears when wave ends
- [x] Bottom strip: SHD/HP bars (left) — AMMO bar (right) — no overlaps

---

## 6. Episode I — Desert Sector (8 checks)

- [x] 3 combat waves + boss (W4)
- [x] Kill targets: W1=25, W2=28, W3=30
- [x] Drip spawner: top / side / centre-drop entry patterns
- [x] Finite ammo — NO AMMO warning on empty
- [x] Supply tents spawn every 16s, collected on overlap
- [x] Wave 3 Miniboss spawns at 3s into wave
- [x] Boss Dossier card with 5s countdown before Desert Viper
- [x] Stage clear → EP II bridge with mechanic preview card

---

## 7. Episode II — Ice Reach (8 checks)

- [x] 3 combat waves + boss (Wave 3 = boss)
- [x] Thermal gauge drains 4pts every 3s passively
- [x] Freeze mines: 30% speed for 3s on contact
- [x] Ice shards: all directions; large ones shatter on bullet hit
- [x] Supply crates: every 22s, restore ammo + thermal
- [x] Pilot swap after Wave 2 — PilotSwapScene launches
- [x] Boss Transmission before The Glacier fight
- [x] The Glacier: 3 hangar bays sequential; each triggers drone wave

---

## 8. Episode III — The Veil (9 checks)

- [x] 3 combat waves + boss
- [x] Energy: 100 max, costs 2/shot, regens 3 per 500ms
- [x] Sonar Pulse [Q]: 5 charges, reveals for 3s, +1 on wave clear
- [x] Phantom Scouts: alpha=0, flash 220ms on fire
- [x] Shade Carriers: spawn 3 phantom drones on death
- [x] Void Rifts: pull + damage at close range, ASTRA immune
- [x] The Sovereign: alpha=0, bullets blocked without Sonar
- [x] Boss flashes briefly when shooting — player can react
- [x] Stage clear: itch.io CTA + full FITZ debrief

---

## 9. Audio (6 checks)

- [x] Menu track: D minor melody-first theme with suspense and release
- [x] Crawl version: builds layer by layer (melody → bass → pads → drums)
- [x] Game track: driving upbeat theme across all 3 episodes
- [x] Boss track: intense chromatic tension across all 3 boss fights
- [x] AudioContext unlocked on first user gesture
- [x] No music gaps between scene transitions in prelude sequence

---

## 10. Persistence & Sharing (4 checks)

- [x] High scores per episode (`sf_hi`, `sf_hi_ep2`, `sf_hi_ep3`)
- [x] Run history per episode — last 5 runs
- [x] Pilot name persists across sessions (`sf_pilot`)
- [x] Copy Score button on all game over screens

---

## 11. Polish & UX (5 checks)

- [x] STARFALL logo: no episode subtitle — shared cleanly across all screens
- [x] Pilot carousel: cinematic single-pilot display, full ability info, slide animation
- [x] EP I Briefing personalises with pilot name after callsign entry
- [x] FITZ dialogue unique per wave and episode
- [x] All skippable screens (crawl, boss dossier, transmission) work on both keyboard and tap

---

*78 checks total — April 2026*
