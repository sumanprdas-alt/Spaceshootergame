# STARFALL — Complete Edition

A three-episode vertical-scrolling shoot-em-up built with **Phaser 3** and **HTML5 Canvas**.  
Delivered as a single self-contained `index.html` — open in any modern browser and play.  
No installation. No server. No dependencies beyond the one-time Phaser CDN load.

---

## Play

**Desktop:** Double-click `index.html`  
**Mobile:** Open the deployed URL in any mobile browser  
**Local server (for music):** `python3 -m http.server 8080` then visit `http://localhost:8080`

---

## Controls

### Desktop (Keyboard)

| Input | Action |
|-------|--------|
| `WASD` or Arrow Keys | Move ship |
| `SPACE` | Fire weapon |
| `Q` | Sonar Pulse *(EP III only — reveals cloaked enemies)* |
| `ESC` | Pause / Resume |
| `ENTER` | Confirm / advance screens |
| `← →` | Navigate pilot carousel |
| `1–4` | Select difficulty |

### Mobile (Touch)

| Zone | Action |
|------|--------|
| Left half of screen | Drag anywhere — joystick appears at touch point |
| Right half of screen | Tap or hold to fire continuously |
| ◎ button (top right, EP III) | Sonar Pulse |
| Bottom-right corner | Pause |

> The FTUX screen automatically detects touch devices and shows the correct control diagram.

---

## Game Flow

```
[ STARFALL — Click / Tap to Begin ]
           ↓
[ THE KETHARAN WAR — story crawl ]
           ↓
[ Enter Pilot Callsign ]
           ↓
[ Choose Your Pilot — carousel (6 pilots, 1 at a time) ]
           ↓
[ EPISODE I BRIEFING — mission context ]
           ↓
[ Select Difficulty ]
           ↓
[ EP I: Desert Sector ]
           ↓  Mission Complete
[ EP II: Ice Reach ]
           ↓  Mission Complete
[ EP III: The Veil ]
           ↓  Mission Complete
[ Final score · FITZ debrief · itch.io CTA ]
```

Each episode has its own mission complete screen with a bridge to the next.  
Pilot name, avatar, difficulty, and episode completion badges persist via `localStorage`.

---

## Episodes

### Episode I — Desert Sector
*Year 2847. The Ketharan Viper fleet holds the sector. One pilot. Zero backup.*

- Desert amber palette
- 3 waves + boss: **Desert Viper** (3 phases)
- Finite ammo — fly over supply tents to restock
- Wave 3: Miniboss Lieutenant escort
- Boss Dossier briefing card before the fight
- FITZ dialogue throughout

### Episode II — Ice Reach
*The Dominion retreats to frozen outer colonies. The pursuit continues.*

- Ice blue palette, aurora shimmer
- 3 waves + boss: **The Glacier** (3 destructible hangar bays)
- **Thermal gauge** — drains passively in the cold; replaces shield
- **Freeze Mines** — contact freezes ship to 30% speed for 3s
- **Ice Shards** — fast hazards from all directions
- **Supply Crates** — restore ammo + thermal
- **Pilot Swap** — specialist reassignment offered after Wave 2
- **Boss Transmission** — intercepted taunt before the fight

### Episode III — The Veil
*The Dominion flees into deep space. No maps. No signals. No backup.*

- Void purple palette, near-total darkness, ship light cone
- 3 waves + boss: **The Sovereign** (fully cloaked)
- **Energy system** — regens passively; firing costs 2 energy
- **Sonar Pulse `[Q]`** — 5 charges; reveals all enemies for 3s
- **Phantom Scouts** — invisible until they fire
- **Shade Carriers** — drop 3 cloaked drones on death
- **Void Rifts** — gravitational pull zones; damage at close range
- **The Sovereign** — bullets blocked unless Sonar-revealed

---

## Pilot Roster

Six pilots selectable via cinematic carousel — one pilot shown at a time, slides in from the side. Each card shows portrait, role, special ability, and flavour bio.

| Pilot | Role | Special Ability |
|-------|------|----------------|
| **NOVA** | Scout Pilot | +20–25% ship speed |
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
│ [portrait] PILOT   9,800 ×4         WAVE 1/4         │
│ ♥ ♥ ♥ ♥ ♥      ENEMIES LEFT: 9    [VETERAN]         │
└──────────────────────────────────────────────────────┘
                    gameplay area
┌──────────────────────────────────────────────────────┐
│ SHD ████████████     AMMO ████████████  120/120      │
│ HP  ████████████                                     │
└──────────────────────────────────────────────────────┘
```

Combo multiplier is shown inline with the score (`9,800 ×4`) — colour shifts white → yellow → orange as the multiplier increases (×2 / ×4 / ×8).

---

## Music

Four synthesised Web Audio API tracks — no external files required:

| Track | When it plays |
|-------|--------------|
| **Menu theme** | Title screen → story crawl → callsign → EP I briefing. D minor, melody-first, builds with the crawl. |
| **Game theme** | All combat waves across all 3 episodes |
| **Boss theme** | All boss encounters |
| **Crawl theme** | EP II and III preludes |

Music flows uninterrupted from the first click through the entire prelude sequence.

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
| Stage clear survival bonus | 500–800 + remaining stats |

---

## Technical Specification

| Item | Detail |
|------|--------|
| Engine | Phaser 3.60.0 via jsDelivr CDN |
| Renderer | WebGL (auto-fallback to Canvas 2D) |
| Canvas | 480 × 720 px logical, `Phaser.Scale.FIT` |
| Sprites | Procedurally generated — zero external art files |
| Music | Web Audio API — 4 synthesised tracks |
| SFX | Web Audio API — all effects synthesised at runtime |
| Touch | Drag-origin joystick + tap-to-fire + EP3 sonar button |
| Gamepad | Left stick move, RT/A fire |
| Persistence | `localStorage` — scores, history, pilot name, episode flags |
| File | Single `index.html` — ~460 KB |
| Scenes | 30 Phaser scenes across 3 episodes |

---

## Repository Structure

```
starfall/
├── index.html   ← Complete Edition (EP I + II + III) — the deliverable
├── README.md    ← This file
└── EVALS.md     ← Full evaluation suite
```

---

## Local Development

No build tools required. Edit `index.html` directly in any text editor.

```bash
# Serve locally (needed for music file loading)
python3 -m http.server 8080

# Then open:
http://localhost:8080
```

**Recommended dev setup:**
- VS Code + Live Server extension (auto-reload on save)
- Chrome DevTools — Performance tab for frame profiling
- Chrome DevTools — Toggle Device Toolbar (`Ctrl+Shift+M`) for mobile simulation

---

## Deployment

The game is a single static HTML file — deploy anywhere:

- **Vercel:** Connect GitHub repo → auto-deploys on every push to `main`
- **GitHub Pages:** Enable in repo Settings → Pages → root `/`
- **itch.io:** Upload `index.html` as a ZIP, set Kind = HTML, viewport 480×720

---

## Credits

Built with [Phaser 3](https://phaser.io) — MIT Licence.  
All game code, procedural sprites, and audio synthesis original.

---

*"Against all statistical probability, yes. I'm as surprised as you are." — FITZ*
