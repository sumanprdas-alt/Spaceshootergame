# STARFALL — Complete Edition

A three-episode vertical-scrolling shoot-em-up built with **Phaser 3** and **HTML5 Canvas**.  
Delivered as a single self-contained `index.html` file — open it in any modern browser and play.  
No installation, no server, no dependencies beyond the one-time Phaser CDN load.

---

## How to Play

**Double-click `index.html` to launch** (or visit the deployed URL).

Chrome, Firefox, Safari 14+, and Edge (desktop) are all supported.

### Controls

| Input | Action |
|-------|--------|
| `WASD` or Arrow Keys | Move ship (8-directional) |
| `SPACE` | Fire weapon |
| `Q` | **Sonar Pulse** *(Episode III — reveals cloaked enemies)* |
| `1–4` | Select difficulty on keyboard |
| `ENTER` | Confirm / advance |
| `ESC` | Pause / Resume |
| `←` `→` Arrow Keys | Navigate pilot carousel |
| Touch left half | Virtual joystick (mobile) |
| Touch right half | Fire (mobile) |
| Gamepad left stick | Move |
| Gamepad RT / A | Fire |

---

## Game Flow

```
[ STARFALL Title Screen — Click to Begin ]
         ↓
[ THE KETHARAN WAR — full story crawl ]
         ↓
[ Enter Your Pilot Callsign ]
         ↓
[ Choose Your Pilot — cinematic carousel (6 pilots) ]
         ↓
[ EPISODE I BRIEFING — mission context ]
         ↓
[ Select Difficulty ]
         ↓
[ EP I — Desert Sector  →  EP II — Ice Reach  →  EP III — The Veil ]
```

Each episode has a mission complete screen with a bridge to the next episode.  
Episode completion, pilot name, and high scores persist across sessions via `localStorage`.

---

## Episodes

### Episode I — Desert Sector
*Year 2847. One pilot. Zero backup. The Ketharan Viper fleet holds the sector.*

**3 waves + boss: Desert Viper (3 phases)**

- Desert amber palette
- Finite ammo — fly over supply tents to restock
- Wave kill counter on HUD
- Multi-directional enemy drip spawner (top, sides, centre-drop)
- Wave 3: Miniboss Lieutenant escort
- Boss Dossier briefing card before the fight
- FITZ dialogue throughout

### Episode II — Ice Reach
*The Dominion retreats to frozen outer colonies. The pursuit continues.*

**3 waves + boss: The Glacier (3 destructible hangar bays)**

- Ice blue palette with aurora shimmer
- **Thermal gauge** — drains passively in the cold; replaces shield
- **Freeze Mines** — contact freezes ship to 30% speed for 3 seconds
- **Ice Shards** — fast hazards from all directions; large ones shatter
- **Supply Crates** — restore ammo and thermal
- **Pilot Swap** — after Wave 2, reassign to a specialist
- **Boss Transmission** — intercepted taunt from Commander Vreth

### Episode III — The Veil
*The Dominion flees into deep space. No maps. No signals. No backup.*

**3 waves + boss: The Sovereign (fully cloaked)**

- Void purple palette, near-total darkness, ship light cone
- **Energy system** — regenerates passively; firing costs 2 energy
- **Sonar Pulse `[Q]`** — 5 charges; reveals all enemies for 3 seconds
- **Phantom Scouts** — invisible until they fire
- **Shade Carriers** — drop 3 cloaked drones on death
- **Void Rifts** — gravitational pull zones; damage at close range
- **The Sovereign** — fully cloaked; bullets blocked unless Sonar-revealed

---

## Pilot Roster

Six pilots selectable via cinematic carousel — each with full name, role, special ability, and bio shown on screen.

| Pilot | Role | Special Ability |
|-------|------|----------------|
| **NOVA** | Scout Pilot | +20% ship speed |
| **VEGA** | Ace Fighter | 2× ammo / energy capacity |
| **ORION** | Recon Expert | Early Warning / 2× Sonar reveal |
| **LYRA** | Combat Engineer | +25–30% bullet damage |
| **SIRIUS** | Heavy Gunner | Full thermal start / 2× energy regen |
| **ASTRA** | Stealth Raider | Freeze immune (EP II) / Void immune (EP III) |

---

## Difficulty Tiers

| Tier | Enemy HP | Speed | Aggression | Boss HP |
|------|----------|-------|------------|---------|
| RECRUIT | ×0.65 | ×0.75 | ×0.65 | ×0.55 |
| VETERAN | ×1.0 | ×1.0 | ×1.0 | ×1.0 |
| ELITE | ×1.5 | ×1.4 | ×1.6 | ×1.7 |
| NIGHTMARE | ×2.2 | ×1.8 | ×2.4 | ×2.6 |

---

## HUD Reference

```
┌─────────────────────────────────────────────────────┐
│ [avatar] PILOT     9,800 ×4         WAVE 1/4        │  ← Row 1
│ ♥♥♥♥♥           ENEMIES LEFT: 9    [VETERAN]        │  ← Row 2
└─────────────────────────────────────────────────────┘
  gameplay area
┌─────────────────────────────────────────────────────┐
│ SHD ████████████    AMMO ████████████  120/120      │
│ HP  ████████████                                    │
└─────────────────────────────────────────────────────┘
```

Combo multiplier baked into the score line (e.g. `9,800 ×4`) — colour shifts white → yellow → orange as multiplier increases.

---

## Scoring

| Action | Points |
|--------|--------|
| Grunt / Drone kill | 100–130 |
| Scout / Phantom kill | 200–280 |
| Elite kill | 500–550 |
| Shade Carrier kill | 600 |
| Miniboss kill | 1,200 |
| Boss kill | 2,000–3,000 |
| Combo (no damage streak) | ×2 / ×4 / ×8 |
| Stage clear survival bonus | 500–800 + stats remaining |

---

## Music

Four synthesised Web Audio API tracks — no external audio files required:

| Track | Used in |
|-------|---------|
| **Menu theme** | Title screen → crawl → callsign → EP I briefing |
| **Game theme** | All gameplay waves |
| **Boss theme** | All boss encounters |
| **Crawl theme** | EP II and III preludes |

The menu track is a D minor theme with suspense and release — rises, dips, climbs, resolves. Continuous from first click through the full prelude sequence.

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
| Persistence | `localStorage` — scores, run history, pilot name, episode completion |
| File size | ~450 KB single HTML file |
| Scenes | 30 Phaser scenes across 3 episodes |

---

## Repository Structure

```
starfall/
├── index.html     ← Complete Edition (EP I + II + III) — the deliverable
├── README.md      ← This file
└── EVALS.md       ← Evaluation suite
```

---

## Credits

Built with [Phaser 3](https://phaser.io) — MIT Licence.  
All game code, procedural sprite generation, and audio synthesis original.

---

*"Against all statistical probability, yes. I'm as surprised as you are." — FITZ*
