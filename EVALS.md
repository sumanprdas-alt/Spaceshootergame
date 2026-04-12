# STARFALL — Evaluation Suite

All checks passing — April 2026.

---

## 1. Core Architecture (8)

- [x] Single `index.html` — no external assets required
- [x] Phaser 3.60.0 via CDN; cached after first load
- [x] All 30 scenes registered — no duplicates
- [x] `localStorage` read/write symmetry — every `getItem` key has a matching `setItem`
- [x] Cross-scene state via `Phaser.Data.DataManager` registry — no global leaks
- [x] Drip spawner timers cleaned up on wave clear / game over / stage clear
- [x] Physics groups use `maxSize` to cap object creation
- [x] Dead objects deactivated and pooled — not destroyed/recreated

---

## 2. Game Flow (11)

- [x] FTUX gate: single click/tap fires — no double-gate
- [x] Music plays immediately on FTUX load (no pre-click silence)
- [x] FTUX controls card: shows keyboard layout on desktop, mobile layout on touch
- [x] "A long time ago..." intro: 2.6s (was 6s)
- [x] Logo zoom: 3.0s, 2s of full visibility before fade
- [x] Crawl covers full Ketharan War arc — all 3 episodes, no EP I-only framing
- [x] STARFALL logo has no episode subtitle — shared cleanly across all screens
- [x] Callsign entry music continues from crawl (no stop/start gap)
- [x] EP I Briefing scene shown after callsign, before difficulty select, greets pilot by name
- [x] Episode completion tracked per episode (`sf_ep1_complete` etc.)
- [x] SPACE-to-skip on crawl and boss dossier

---

## 3. Mobile Touch Controls (6)

- [x] EP I: virtual joystick (appears at touch origin on left half) + fire zone (right half)
- [x] EP II: same joystick + fire zone — full touch parity with EP I
- [x] EP III: joystick + fire zone + ◎ Sonar button (top right, dims when no charges)
- [x] Joystick appears where player touches, not fixed to corner
- [x] Fire zone highlights on contact; joystick knob clamps to radius
- [x] HUD strip (y<60) excluded from joystick trigger area — no accidental activation

---

## 4. HUD (7)

- [x] Top strip: strict 2-row layout — no overlaps at any combo/wave state
- [x] Row 1: avatar + name | score + combo inline | wave label
- [x] Row 2: lives icons | enemies left | difficulty badge
- [x] Combo baked into score text (`9,800 ×4`) — fixed 20px font, colour-coded
- [x] Enemies left clears correctly when wave ends
- [x] Boss HP bar replaces wave label during boss fights
- [x] Bottom strip: SHD/HP bars left, AMMO bar right — no overlaps

---

## 5. Pilot Carousel (5)

- [x] 6 pilots, one at a time, slides in from right
- [x] Each card: large portrait, name, role, ⚡ ability label + description, bio
- [x] Navigate: ◀ PREV / NEXT ▶ buttons + left/right arrow keys
- [x] Dot indicator row shows current pilot (1 of 6)
- [x] Confirm: button + ENTER + SPACE — flash animation then transition

---

## 6. Episode I — Desert Sector (8)

- [x] 3 combat waves + boss wave
- [x] Kill targets: W1=25, W2=28, W3=30
- [x] Drip spawner: top, side, centre-drop entries
- [x] Finite ammo — NO AMMO warning when empty
- [x] Supply tents every 16s, collected on overlap
- [x] Wave 3 Miniboss (Viper Lieutenant)
- [x] Boss Dossier card + 5s countdown
- [x] Stage clear → EP II bridge + mechanic preview

---

## 7. Episode II — Ice Reach (8)

- [x] 3 combat waves + boss
- [x] Thermal gauge: drains 4pts every 3s passively
- [x] Freeze mines: 30% speed for 3s on contact
- [x] Ice shards: multi-directional; large ones shatter into 2 on bullet hit
- [x] Supply crates: every 22s, restore 35 ammo + 10 thermal
- [x] Pilot swap offered after Wave 2
- [x] Boss Transmission scene before The Glacier
- [x] The Glacier: 3 sequential hangar bays, each triggers drone wave

---

## 8. Episode III — The Veil (9)

- [x] 3 combat waves + boss
- [x] Energy: 100 max, costs 2/shot, regens 3 per 500ms
- [x] Sonar Pulse [Q]: 5 charges, reveals all for 3s, +1 on wave clear
- [x] Phantom Scouts: alpha=0, flash 220ms on fire
- [x] Shade Carriers: spawn 3 phantoms on death, wave target increments
- [x] Void Rifts: gravitational pull, damage at <0.7r, ASTRA immune
- [x] The Sovereign: alpha=0, bullets blocked until Sonar-revealed
- [x] Boss reveals briefly when firing — reactive counter-attack possible
- [x] Stage clear: itch.io CTA + full FITZ debrief

---

## 9. Audio (6)

- [x] Menu theme: D minor melody-first, plays FTUX → crawl → callsign → EP I briefing
- [x] Game theme: driving F minor, all wave gameplay
- [x] Boss theme: chromatic tension, all boss encounters
- [x] Crawl theme: same D minor theme, layer-by-layer build
- [x] AudioContext unlocked on first gesture — no silent first session
- [x] Music continuous across scene transitions — no stop/start gaps

---

## 10. Persistence & Sharing (4)

- [x] High scores per episode (`sf_hi`, `sf_hi_ep2`, `sf_hi_ep3`)
- [x] Run history per episode — last 5 runs
- [x] Pilot name persists (`sf_pilot`)
- [x] Copy Score button on all game over screens

---

*Total: 72 checks — all passing, April 2026*
