# STARFALL — Evaluation Suite

Full check list across gameplay, UX, audio, mobile, persistence, and technical correctness.  
Last updated: April 2026.

---

## 1. Core Architecture (8 checks)

- [x] Single `index.html` — no external assets required
- [x] Phaser 3.60.0 loads via CDN; browser-cached after first load
- [x] All 30 scenes registered in `Phaser.Game` — no duplicates
- [x] `localStorage` read/write symmetry — every `getItem` key has a `setItem`
- [x] All state via `Phaser.Data.DataManager` registry — no global variable leaks
- [x] Drip spawner timers cleaned up on wave clear / game over / stage clear
- [x] Physics groups use `maxSize` — no unbounded object creation
- [x] Dead objects deactivated and pooled — not destroyed and recreated

---

## 2. Game Flow (10 checks)

- [x] FTUX gate: fires on first click or keypress — no double-gate
- [x] Music plays immediately on FTUX screen load — no silence before gesture
- [x] "A long time ago..." intro: 2.6s (fade in 0.6s → hold 1.4s → fade out 0.6s)
- [x] Logo zoom: 3.0s with ~2s of full visibility before fade
- [x] Story crawl covers full Ketharan War arc — all 3 episodes, not EP I only
- [x] EP I Briefing screen shown after callsign entry, before difficulty select
- [x] Music flows uninterrupted: FTUX → crawl → callsign → EP I briefing
- [x] Pilot carousel: 6 pilots, cinematic slide, each shows ability + bio
- [x] Episode completion tracked in `localStorage` (sf_ep1_complete etc.)
- [x] SPACE-to-skip on crawl and boss dossier

---

## 3. Mobile & Touch (8 checks)

- [x] EP I: drag-origin joystick on left half, tap-to-fire on right half
- [x] EP II: identical joystick + fire touch system
- [x] EP III: identical joystick + fire touch + sonar ◎ button (top right)
- [x] Joystick appears at touch origin — not locked to a fixed position
- [x] Joystick knob clamped to 46px radius — correct feel
- [x] Fire zone highlights subtly on press — visual feedback
- [x] Sonar button dims when charges are depleted (EP III)
- [x] FTUX controls card detects touch device and shows mobile layout

---

## 4. HUD (7 checks)

- [x] Top strip: strict 2-row layout — no overlaps at any time
- [x] Row 1: avatar + name (left) — score + combo inline (centre) — wave (right)
- [x] Row 2: lives icons (left) — enemies left (centre) — difficulty (right)
- [x] Combo baked into score text (`9,800 ×4`) — fixed 20px font, never overflows
- [x] Score colour shifts: white (×1) → yellow (×2) → orange (×4/×8)
- [x] Enemies left clears correctly when wave ends
- [x] Bottom strip: SHD/HP bars (left) — AMMO bar (right) — no overlaps

---

## 5. Episode I — Desert Sector (8 checks)

- [x] 3 combat waves + boss (W4)
- [x] Kill targets: W1=25, W2=28, W3=30
- [x] Drip spawner: top / side / centre-drop entry patterns
- [x] Finite ammo — NO AMMO warning on empty
- [x] Supply tents spawn every 16s, collected on ship overlap
- [x] Wave 3 Miniboss spawns at 3s into wave
- [x] Boss Dossier card with 5s countdown before Desert Viper
- [x] Stage clear → EP II bridge with mechanic preview card

---

## 6. Episode II — Ice Reach (8 checks)

- [x] 3 combat waves + boss (Wave 3 = boss)
- [x] Thermal gauge drains 4 pts every 3s passively; replaces shield
- [x] Freeze mines slow ship to 30% speed for 3s on contact
- [x] Ice shards spawn from all directions; large ones shatter into 2 on bullet hit
- [x] Supply crates spawn every 22s, restore 35 ammo + 10 thermal
- [x] Pilot swap offered after Wave 2 — PilotSwapScene launches
- [x] Boss Transmission (Vreth taunt) before The Glacier fight
- [x] The Glacier: 3 hangar bays destroyed sequentially, each triggers drone wave

---

## 7. Episode III — The Veil (9 checks)

- [x] 3 combat waves + boss
- [x] Energy system: 100 max, costs 2 per shot, regens 3 per 500ms
- [x] Sonar Pulse [Q]: 5 charges, reveals all + boss for 3s, +1 on wave clear
- [x] Phantom Scouts: alpha=0, flash briefly on fire (220ms)
- [x] Shade Carriers: spawn 3 phantom drones on death, wave target increments
- [x] Void Rifts: pull + damage at <0.7× radius, ASTRA immune
- [x] The Sovereign: alpha=0, bullets blocked without Sonar reveal
- [x] Boss flashes briefly when shooting — player can react
- [x] Stage clear: itch.io CTA + full FITZ debrief

---

## 8. Audio (6 checks)

- [x] Menu track: D minor melody-first theme, suspense and release
- [x] Crawl version of menu track: builds layer by layer (melody → bass → pads → drums)
- [x] Game track: driving upbeat theme across all 3 episodes
- [x] Boss track: intense chromatic tension across all 3 boss fights
- [x] AudioContext unlocked on first user gesture
- [x] No music gaps between scene transitions in prelude sequence

---

## 9. Persistence & Sharing (4 checks)

- [x] High scores per episode (`sf_hi`, `sf_hi_ep2`, `sf_hi_ep3`)
- [x] Run history per episode — last 5 runs with pilot, score, wave, difficulty
- [x] Pilot name persists across sessions (`sf_pilot`)
- [x] Copy Score button on all game over screens

---

## 10. Polish & UX (5 checks)

- [x] STARFALL logo has no episode subtitle — shared cleanly across all screens
- [x] Pilot carousel: cinematic single-pilot display, full info, slide animation
- [x] EP I Briefing screen personalises with pilot name after callsign entry
- [x] FITZ dialogue lines unique per wave and episode
- [x] Boss dossier, transmission, and briefing scenes all skippable

---

*73 checks total — April 2026*
