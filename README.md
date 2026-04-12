# STARFALL — Complete Edition

A three-episode vertical-scrolling shoot-em-up built with **Phaser 3** and **HTML5 Canvas**.  
Delivered as a single self-contained `index.html` — open in any modern browser and play.  
No installation. No server. No dependencies beyond the one-time Phaser CDN load.

---

## Play

**Desktop:** Double-click `index.html`  
**Mobile (iPhone/Android):** Open the deployed URL in Safari or Chrome  
**Local server (for music):** `python3 -m http.server 8080` → `http://localhost:8080`

---

## Controls

### Desktop

| Input | Action |
|-------|--------|
| `WASD` or Arrow Keys | Move ship (8-directional) |
| `SPACE` | Fire weapon |
| `Q` | Sonar Pulse *(EP III — reveals cloaked enemies)* |
| `ESC` | Pause / Resume |
| `ENTER` | Confirm / advance |
| `← →` | Navigate pilot carousel |
| `1–4` | Select difficulty |

### Mobile (iOS / Android)

| Zone | Action |
|------|--------|
| **Left half — drag** | Move ship. Joystick appears at your touch point. |
| **Right half — tap/hold** | Fire continuously |
| **◎ button (top right, EP III)** | Sonar Pulse |
| **ESC / Pause** | Bottom-right corner button |

> The FTUX screen auto-detects touch and shows the mobile control diagram.  
> Tap anywhere on the crawl screen to skip it on mobile.  
> Callsign entry uses a native HTML input — the iOS keyboard opens automatically.

---

## Game Flow

```
[ STARFALL — Tap / Click to Begin ]
           ↓
[ THE KETHARAN WAR — story crawl (tap to skip) ]
           ↓
[ Enter Pilot Callsign — native keyboard on mobile ]
           ↓
[ Choose Your Pilot — carousel, 6 pilots, 1 at a time ]
           ↓
[ EPISODE I BRIEFING — mission context, named for your pilot ]
           ↓
[ Select Difficulty ]
           ↓
[ EP I: Desert Sector → EP II: Ice Reach → EP III: The Veil ]
           ↓
[ Final score · FITZ debrief · itch.io CTA ]
```

---

## Episodes

### Episode I — Desert Sector
*Year 2847. The Ketharan Viper fleet holds the sector. One pilot. Zero backup.*

- Desert amber palette
- 3 waves + boss: **Desert Viper** (3 phases)
- Finite ammo — fly over supply tents to restock
- Wave 3: Miniboss Lieutenant escort
- Boss Dossier briefing card before the fight

### Episode II — Ice Reach
*The Dominion retreats to frozen outer colonies. The pursuit continues.*

- Ice blue palette with aurora shimmer
- 3 waves + boss: **The Glacier** (3 destructible hangar bays)
- **Thermal gauge** — drains passively in the cold
- **Freeze Mines** — contact freezes ship to 30% speed for 3s
- **Ice Shards** — fast hazards from all directions
- **Supply Crates** — restore ammo + thermal
- **Pilot Swap** — specialist reassignment after Wave 2
- **Boss Transmission** — intercepted taunt before the fight

### Episode III — The Veil
*The Dominion flees into deep space. No maps. No signals. No backup.*

- Void purple palette, near-total darkness, ship light cone
- 3 waves + boss: **The Sovereign** (fully cloaked)
- **Energy system** — regens passively; firing costs 2 energy
- **Sonar Pulse `[Q]`** — 5 charges; reveals all enemies for 3s
- **Phantom Scouts** — invisible until they fire
- **Shade Carriers** — drop 3 cloaked drones on death
- **Void Rifts** — gravitational pull zones
- **The Sovereign** — bullets blocked unless Sonar-revealed

---

## Pilot Roster

Six pilots in a cinematic carousel — one shown at a time, slides in from the side. Each card shows portrait, role, special ability, and flavour bio.

| Pilot | Role | Special Ability |
|-------|------|----------------|
| **NOVA** | Scout Pilot | +20–25% ship speed |
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

## HUD Layout

```
┌──────────────────────────────────────────────────────┐
│ [portrait] PILOT   9,800 ×4         WAVE 1/4         │  Row 1
│ ♥ ♥ ♥ ♥ ♥      ENEMIES LEFT: 9    [VETERAN]         │  Row 2
└──────────────────────────────────────────────────────┘
                    gameplay area
┌──────────────────────────────────────────────────────┐
│ SHD ████████████     AMMO ████████████  120/120      │
│ HP  ████████████                                     │
└──────────────────────────────────────────────────────┘
```

Combo multiplier shown inline with score (`9,800 ×4`) — white → yellow → orange as multiplier grows.

---

## Music

Four synthesised Web Audio API tracks — no external files required:

| Track | When it plays |
|-------|--------------|
| **Menu theme** | Title → crawl → callsign → EP I briefing. D minor, builds with the crawl. |
| **Game theme** | All combat waves |
| **Boss theme** | All boss encounters |
| **Crawl theme** | EP II and III preludes |

---

## Technical Specification

| Item | Detail |
|------|--------|
| Engine | Phaser 3.60.0 via jsDelivr CDN |
| Renderer | WebGL (auto-fallback to Canvas 2D) |
| Canvas | 480 × 720 px logical, `Phaser.Scale.FIT` |
| Sprites | Procedurally generated — zero external art files |
| Audio | Web Audio API — 4 synthesised tracks + full SFX |
| Touch | Drag-origin joystick + tap-to-fire + EP3 sonar button |
| Mobile input | Native HTML `<input>` for callsign entry (triggers iOS keyboard) |
| Gamepad | Left stick move, RT/A fire |
| Persistence | `localStorage` — scores, history, pilot name, episode flags |
| iOS fixes | `activePointers:3`, `touch-action:none`, `user-scalable=no`, `viewport-fit:cover`, touchmove preventDefault |
| File | Single `index.html` — ~460 KB |
| Scenes | 30 Phaser scenes across 3 episodes |

---

## Mobile Testing

**Chrome DevTools (quickest):**
1. Open `index.html` in Chrome
2. `F12` → Toggle Device Toolbar (`Ctrl+Shift+M`)
3. Pick iPhone 12 or Pixel 5
4. Touch events are fully simulated

**Real device:**
1. `python3 -m http.server 8080`
2. Find your computer's local IP (e.g. `192.168.1.5`)
3. On your phone: `http://192.168.1.5:8080`
4. Both devices must be on the same WiFi

---

## Local Development

```bash
# Serve locally (needed for music)
python3 -m http.server 8080
# Visit http://localhost:8080
```

Edit `index.html` directly — no build tools required.

---

## Deployment

| Platform | How |
|----------|-----|
| **Vercel** | Connect GitHub repo → auto-deploys on every push to `main` |
| **GitHub Pages** | Settings → Pages → Deploy from branch → root `/` |
| **itch.io** | Upload `index.html` as ZIP, Kind = HTML, viewport 480×720 |

---

## Repository Structure

```
starfall/
├── index.html      ← Complete Edition (EP I + II + III)
├── README.md       ← This file
├── EVALS.md        ← Evaluation suite
└── docs/
    ├── starfall-prd.docx
    ├── starfall-solutions.docx
    ├── starfall-techstack.docx
    ├── starfall-learnings.docx
    └── starfall-evals.docx
```

---

## Credits

Built with [Phaser 3](https://phaser.io) — MIT Licence.  
All game code, procedural sprites, and audio synthesis original.

---

*"Against all statistical probability, yes. I'm as surprised as you are." — FITZ*
