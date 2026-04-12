# STARFALL — Complete Edition

A three-episode vertical-scrolling shoot-em-up built with **Phaser 3** and **HTML5 Canvas**.  
Delivered as a single self-contained `index.html` file — open in any modern browser and play.  
No installation, no server, no dependencies beyond the one-time Phaser CDN load.

---

## How to Play

**Double-click `index.html`** or visit the deployed URL.

Works on **desktop and mobile**. Controls adapt automatically to the device.

### Desktop Controls

| Input | Action |
|-------|--------|
| `WASD` or Arrow Keys | Move ship (8-directional) |
| `SPACE` | Fire weapon (hold to auto-fire) |
| `Q` | Sonar Pulse *(EP III only — reveals cloaked enemies)* |
| `1–4` | Select difficulty |
| `ENTER` | Confirm / advance |
| `ESC` | Pause / Resume |
| `←` `→` | Navigate pilot carousel |

### Mobile Controls

| Zone | Action |
|------|--------|
| **Left half of screen** | Drag anywhere — virtual joystick appears at touch point |
| **Right half of screen** | Tap or hold to fire continuously |
| **◎ button (top right, EP III)** | Sonar Pulse — dims when no charges remain |
| Pause button | Bottom right corner |

> On touch devices the FTUX screen automatically shows the mobile control layout.

---

## Game Flow

```
[ STARFALL — Click / Tap to Begin ]
          ↓
[ THE KETHARAN WAR — full story crawl ]
          ↓
[ Enter Pilot Callsign ]
          ↓
[ Choose Your Pilot — cinematic carousel ]
          ↓
[ EPISODE I BRIEFING — mission context ]
          ↓
[ Select Difficulty ]
          ↓
[ EP I — Desert Sector ]
          ↓  Mission Complete
[ EP II — Ice Reach ]
          ↓  Mission Complete
[ EP III — The Veil ]
          ↓  Mission Complete
[ Final score · FITZ debrief · itch.io CTA ]
```

Pilot name, avatar, difficulty, and episode completion persist across sessions via `localStorage`.

---

## Episodes

### Episode I — Desert Sector
*One pilot. Zero backup. Break through the Ketharan Viper fleet.*

- Desert amber palette
- Finite ammo — fly over supply tents to restock
- 3 waves + miniboss escort + **Desert Viper** boss (3 phases)
- Boss Dossier briefing card before the fight
- FITZ dialogue throughout all waves

### Episode II — Ice Reach
*The pursuit continues to frozen outer colonies.*

- Ice blue palette with aurora shimmer
- **Thermal gauge** — drains passively in cold; replaces shield
- **Freeze Mines** — freezes ship to 30% speed for 3 seconds
- **Ice Shards** — multi-directional hazards; large ones shatter
- **Supply Crates** — restore ammo + thermal
- **Pilot Swap** after Wave 2
- **Boss Transmission** before **The Glacier** (3 destructible hangar bays)

### Episode III — The Veil
*Deep space. No maps. No signals. No backup.*

- Void purple palette, near-total darkness, ship light cone
- **Energy system** — regenerates passively; firing costs 2 energy
- **Sonar Pulse `[Q]`** — 5 charges; reveals all enemies for 3 seconds
- **Phantom Scouts** — invisible until they fire
- **Shade Carriers** — drop 3 cloaked drones on death
- **Void Rifts** — gravitational pull zones
- **The Sovereign** — fully cloaked; bullets blocked until Sonar-revealed

---

## Pilot Roster

Six pilots selectable via cinematic carousel. Each card shows portrait, role, special ability, and bio.

| Pilot | Role | Special Ability |
|-------|------|----------------|
| **NOVA** | Scout Pilot | +20% ship speed |
| **VEGA** | Ace Fighter | 2× ammo / energy capacity |
| **ORION** | Recon Expert | Early Warning / 2× Sonar reveal duration |
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

## HUD Layout

```
┌──────────────────────────────────────────────────────┐
│ [av] PILOT      9,800 ×4          WAVE 1/4           │  Row 1
│ ♥♥♥♥♥         ENEMIES LEFT: 9    [VETERAN]           │  Row 2
└──────────────────────────────────────────────────────┘
  — gameplay —
┌──────────────────────────────────────────────────────┐
│ SHD ████████████     AMMO ████████████  120/120      │
│ HP  ████████████                                     │
└──────────────────────────────────────────────────────┘
```

Combo multiplier shown inline in score (`9,800 ×4`) — colour shifts white → yellow → orange.

---

## Music

Four synthesised tracks via Web Audio API — no external audio files needed.

| Track | When |
|-------|------|
| **Menu theme** | Title → crawl → callsign → EP I briefing (continuous, no gaps) |
| **Game theme** | All wave gameplay |
| **Boss theme** | All boss encounters |
| **Crawl theme** | EP II + III preludes |

The menu theme is a D minor melody with suspense and release — builds from melody alone through bass, pads, and full drums.

---

## Scoring

| Action | Points |
|--------|--------|
| Grunt / Drone | 100–130 |
| Scout / Phantom | 200–280 |
| Elite | 500–550 |
| Shade Carrier | 600 |
| Miniboss | 1,200 |
| Boss | 2,000–3,000 |
| Combo (no-damage streak) | ×2 / ×4 / ×8 |
| Stage clear survival bonus | 500–800 + stats |

---

## Technical Specification

| Item | Detail |
|------|--------|
| Engine | Phaser 3.60.0 via jsDelivr CDN |
| Renderer | WebGL → Canvas 2D fallback |
| Canvas | 480 × 720 px, `Phaser.Scale.FIT` responsive |
| Sprites | Procedurally generated — zero external art files |
| Audio | Web Audio API — all music + SFX synthesised at runtime |
| Touch | Virtual joystick (appears at touch point) + fire zone + EP III sonar button |
| Gamepad | Left stick move, RT / A fire |
| Persistence | `localStorage` — scores, history, pilot name, episode completion |
| Scenes | 30 Phaser scenes across 3 episodes |
| File size | ~465 KB single HTML file |

---

## Repository Structure

```
starfall/
├── index.html    ← Complete Edition (EP I + II + III) — the deliverable
├── README.md     ← This file
└── EVALS.md      ← Evaluation suite (all checks passing)
```

---

## Deployment

Hosted via **Vercel** — every push to `main` auto-deploys.  
For local play: download `index.html` and open in Chrome / Firefox / Safari 14+.  
For local music testing: `python3 -m http.server 8080` then open `http://localhost:8080`.

---

## Credits

Built with [Phaser 3](https://phaser.io) — MIT Licence.  
All game code, procedural sprites, and audio synthesis original.

---

*"Against all statistical probability, yes. I'm as surprised as you are." — FITZ*
