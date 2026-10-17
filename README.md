# Barnaby's Dandelion Odyssey

A pixel-handheld style isometric voxel gliding game. Launch Barnaby the gnome off a
seesaw with a watering can, hold to glide on his maple leaf, catch updrafts and
boosters, dodge grumpy bees, and chase your best distance.

## Run it

Any static file server works. From the repo root:

```sh
npx live-server        # auto-reloads on edit
# or
python -m http.server 8000
```

Then open http://localhost:8000 (or the port `live-server` picks).

## Controls

| Input | Action |
|---|---|
| `P` / `Space` (press) | Drop the watering can at the power meter's green peak |
| `P` / `Space` (hold) | Glide on the maple leaf |
| `R` | Quick reset |
| Mouse | Slight isometric camera drift |

On-screen: the big magenta **P** button mirrors the keyboard, and the LCD deck has
Shop / Scenes pills plus a pixel-shader toggle.

## File map

```
index.html        Markup: handheld shell, HUD, LCD deck, modals
css/styles.css    All game styling (pixel buttons, LCD bezel, switches)
js/config.js      Constants, shared state, DOM refs, localStorage progression
js/sound.js       Procedural SFX engine (Tone.js, no audio assets)
js/world.js       ThreeWorld: voxel isometric scene, launcher, Barnaby, entities
js/game.js        World gen, physics, HUD, shop, input, 2D overlay, main loop
```

Scripts load in order at the end of `index.html` and share globals — no build step,
no modules, works over `file://` too (CDN scripts need internet).

## Progression

Best distance, acorn balance, upgrades, and gnome name persist in `localStorage`
under the `barnaby_*` keys.

## Upgrades (acorn shop)

1. **Heavy Can** — stronger launches
2. **Leaf Wax** — more stamina, better glide conversion
3. **Boots** — bouncier mushroom and ground bounces

Each goes to Lv.5; cost is `level × 5` acorns.
