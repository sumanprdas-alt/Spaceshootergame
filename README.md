# STARFALL — Complete Edition

A three-episode vertical-scrolling shoot-em-up built with **Phaser 3** and **HTML5 Canvas**.  
Delivered as a single self-contained `.html` file — open it in any modern browser and play.  
No installation, no server, no dependencies beyond the one-time Phaser CDN load.


---

## How to Play

**Double-click `starfall.html` to launch.**

Chrome, Firefox, Safari 14+, and Edge (desktop) are all supported. Works on mobile browsers with touch controls.

### Controls

| Input | Action |
|-------|--------|
| `WASD` or Arrow Keys | Move ship (8-directional) |
| `SPACE` | Fire weapon |
| `Q` | **Sonar Pulse** *(Episode III — reveals cloaked enemies)* |
| `1–4` | Select difficulty on keyboard |
| `ENTER` | Confirm / advance |
| `ESC` | Pause / Resume |
| Touch left half | Virtual joystick (mobile) |
| Touch right half | Fire (mobile) |
| Touch ◎ button | Sonar Pulse (EP III mobile) |
| Gamepad left stick | Move |
| Gamepad RT / A | Fire |

---

## Episodes

### Episode I — Desert Sector
*Year 2847. The Ketharan Dominion launches a surprise assault. One pilot remains.*

**3 waves → boss: Desert Viper (3 phases)**

- Desert amber palette
- Finite ammo with HUD gauge — fly over supply tents to restock
- Wave kill counter — HUD shows enemies remaining
- Multi-directional enemy entry — top, sides, and centre-drop
- Wave 3: Miniboss Lieutenant escort before the boss
- Boss Dossier briefing card before the fight
- FITZ dialogue throughout all waves

### Episode II — Ice Reach
*The Dominion retreats to frozen outer colonies. The pursuit continues.*

**3 waves → boss: The Glacier (3 destructible hangar bays)**

- Ice teal-blue palette, aurora shimmer
- **Thermal gauge** — replaces shield; drains passively in the cold
- **Freeze Mines** — contact freezes ship to 30% speed for 3 seconds
- **Ice Shards** — fast hazards from all directions; large ones shatter on impact
- **Supply Crates** — drift across screen, restore ammo and thermal
- **Pilot Swap** — after Wave 2, FITZ offers a specialist reassignment
- **Boss Transmission** — intercepted taunt from Commander Vreth before the fight
- **The Glacier** — destroy 3 sequential hangar bays; each triggers a drone wave

### Episode III — The Veil
*The Dominion flees into deep space. No maps. No signals. No backup.*

**3 waves → boss: The Sovereign (fully cloaked)**

- Void purple palette, near-total darkness, ship light cone
- **Energy system** — replaces ammo; regenerates passively; firing costs 2 energy
- **Sonar Pulse `[Q]`** — 5 charges; reveals all enemies and the boss for 3 seconds
- **Phantom Scouts** — invisible until they fire; betrayed by muzzle flash
- **Shade Carriers** — slow, high-HP; drop 3 cloaked drones on death
- **Wraith Streakers** — fast diagonal side-entry enemies, briefly visible then fade
- **Void Rifts** — gravitational pull zones; deal damage at close range (ASTRA immune)
- **The Sovereign** — fully cloaked; bullets blocked unless revealed by Sonar

---

## Pilot Roster

Eight pilots with **unique passive abilities** per episode:

| Pilot | Role | EP II Passive | EP III Passive |
|-------|------|---------------|----------------|
| **NOVA** | Scout | +20% speed | +25% speed |
| **VEGA** | Ace Fighter | 2× ammo capacity | 2× energy capacity |
| **ORION** | Recon Expert | Early enemy reveal | 2× Sonar reveal duration |
| **LYRA** | Combat Engineer | +25% bullet damage | +30% bullet damage |
| **SIRIUS** | Heavy Gunner | Start with full thermal | 2× energy regen rate |
| **ASTRA** | Stealth Raider | **Freeze immunity** | **Void damage immunity** |
| **ZEPHYR** | Deep Space Op | 2× score multiplier | 2× score multiplier |
| **CORONA** | Commander | +50% max HP | +50% max HP |

> **EP III tip:** ORION (2× Sonar duration) and ASTRA (Void immunity) are tier-1 choices.

---

## Difficulty Tiers

| Tier | Enemy HP | Speed | Aggression | Boss HP | Fire Rate |
|------|----------|-------|------------|---------|-----------|
| RECRUIT | ×0.65 | ×0.75 | ×0.65 | ×0.55 | Slow |
| VETERAN | ×1.0 | ×1.0 | ×1.0 | ×1.0 | Normal |
| ELITE | ×1.5 | ×1.4 | ×1.6 | ×1.7 | Fast |
| NIGHTMARE | ×2.2 | ×1.8 | ×2.4 | ×2.6 | Very Fast |

---

## Episode Flow

```
[ Title Screen — Click / Tap to Begin ]
         ↓
[ EP I — Desert Sector ]
         ↓ Mission Complete
[ PLAY AGAIN  |  ▶▶ EP.II  |  MENU ]
    + mechanic preview card for EP II
         ↓
[ EP II — Ice Reach ]
         ↓ Mission Complete
[ PLAY AGAIN  |  ▶▶ EP.III  |  MENU ]
    + mechanic preview card for EP III
         ↓
[ EP III — The Veil ]
         ↓ Mission Complete
  Final score + FITZ debrief + itch.io CTA
```

Each episode has its own **Main Menu** and can be started independently.  
Pilot name, avatar, and episode completion badges persist across sessions.  
**Mid-episode save** — if you quit between episodes, the game resumes from your saved point.

---

## Scoring

| Action | Points |
|--------|--------|
| Grunt / Drone kill | 100–130 |
| Scout / Phantom kill | 200–280 |
| Elite / Wraith kill | 180–500 |
| Shade Carrier kill | 600 |
| Miniboss kill | 1,200 |
| Boss kill | 2,000–3,000 |
| Consecutive kills (no damage) | ×2 / ×4 / ×8 combo |
| Mission clear survival bonus | 500–800 + HP/thermal/sonar remaining |

High scores saved per episode. Share your score with one click on the game over screen.

---

## Technical Specification

| Item | Detail |
|------|--------|
| Engine | Phaser 3.60.0 via jsDelivr CDN |
| Renderer | WebGL (auto-fallback to Canvas 2D) |
| Canvas | 480 × 720 px logical, `Phaser.Scale.FIT` responsive |
| Sprites | Procedurally generated via Canvas 2D API — zero external art files |
| Music | Web Audio API — 4 synthesised chiptune tracks |
| SFX | Web Audio API — all effects synthesised at runtime |
| Touch | Virtual joystick + fire zone + sonar button |
| Gamepad | Left stick move, RT/A fire |
| Persistence | `localStorage` — scores, run history, pilot name, episode completion |
| PWA | Meta tags + fullscreen API |
| File size | ~440 KB single HTML file |
| Scenes | 29 Phaser scenes across 3 episodes |

### Offline Play

All sprites and audio are generated procedurally — no media files needed.  
Phaser loads from CDN once, then the browser caches it.  
For **fully offline play**: download `phaser.min.js` and replace the CDN `<script>` tag.

---

## Repository Structure

```
starfall/
├── starfall.html              ← Complete Edition — EP I + EP II + EP III
├── starfall_ep1_FINAL.html    ← Episode I standalone (locked reference)
├── starfall_ep2.html          ← Episode II standalone (test build)
├── starfall_ep3.html          ← Episode III standalone (test build)
├── README.md                  ← This file
└── EVALS.md                   ← Full evaluation suite (63 checks, 100% passing)
```

---

## Credits

Built with [Phaser 3](https://phaser.io) — MIT Licence.  
All game code, procedural sprite generation, and audio synthesis original.

---

*"Against all statistical probability, yes. I'm as surprised as you are." — FITZ*
