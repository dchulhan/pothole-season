# Pothole Season

Caribbean coastal road racer. Same bones as a vibe-coded Three.js racer (one HTML module, import map, no physics library), different brief: you are on tarmac, not anti-grav.

Dodge potholes. Stay under the limit through speed traps. Eat the power-ups.

## Run

Any static server, from this folder:

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`. A double-click on `index.html` also works in current Chrome and Firefox (the only remote calls are the Three.js CDN and Google Fonts).

## Controls

- `W` / `S` or `Up` / `Down` — throttle and brake
- `A` / `D` or `Left` / `Right` — lane
- `Space` — eat the queued food (or the one you just grabbed, if the slot is empty it fires on pickup)
- `H` — horn
- `R` — restart after a wreck
- Click the page once so the Web Audio engine can start

Ten other vehicles share the loop (hire cars and maxi-taxis). They drift lanes, pull aside if you sit on their bumper, and horn if you dive past. Clipping one scrapes chassis unless the buss-up-shut is up. Aloo pie still hops potholes, not traffic.

## Stack

- Three.js r164 via jsDelivr import map
- WebGLRenderer, procedural ribbon road on a closed `CatmullRomCurve3`
- Custom kinematic car (speed, lateral offset, chassis). No Cannon, Rapier, or ammo.js
- Web Audio: twin-oscillator engine, plus noise and tone hits for pothole, trap chirp, pickup, eat, shield, horn, scrape, and wreck
- `localStorage` key `potholeSeasonBest` for the best score

## Food

| Pickup | Effect |
|---|---|
| Doubles | Short channa boost |
| Bake and shark | Longer surge |
| Sorrel | Hard nitro, burns chassis a touch |
| Buss-up-shut | Shield, eats the next pothole or fine |
| Aloo pie | Hop, potholes cannot touch you |
| Callaloo | Grip, tighter line |
| Pelau | Chassis repair |
| Corn soup | Regen for a few seconds |
| Coconut water | Jam the next radar |
| Jerk | Trap immunity |
| Pholourie | Magnet, pulls nearby food |
| Patty | Score multiplier |

Potholes chew chassis and scrub speed. Speed traps fine you if you are over the posted limit, unless a food says otherwise. Chassis at zero is a wreck.
