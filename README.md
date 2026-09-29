# Blockcraft

A Minecraft-style block game that runs in your web browser. It is one file, `index.html`, with nothing to install and no downloads. It even works offline, where it just uses a fallback font.

## Play it on your Mac

1. Download this repository. On GitHub, click **Code → Download ZIP**, then double-click the ZIP to unzip it.
2. Double-click `index.html`. It opens in Safari, Chrome or whatever your default browser is.
3. Click **Play**, then click inside the world so the game captures your mouse.

Chrome usually runs it the smoothest. If you'd rather launch it from Terminal:

```sh
open index.html
```

## Controls

| Input | Action |
| --- | --- |
| Mouse / trackpad | Look around |
| `W` `A` `S` `D` | Walk |
| `Space` | Jump. Double-tap to fly, hold to rise |
| `Shift` | Sprint. Sink while flying |
| Click | Break a block |
| Right-click (two-finger click or `Ctrl`-click on a trackpad) | Place a block |
| `1`–`9` / scroll | Choose a block |
| `E` | Open all blocks |
| `Q` / middle-click | Grab the block you are looking at |
| `F` | Turn flying on or off |
| `F3` | Show or hide coordinates |
| Arrow keys | Turn the camera |
| `Esc` | Pause |

## What's in it

- An endless world that is generated as you walk, with hills, forests, beaches, oceans, snowy mountains, caves, and coal and iron ore
- 26 block types with pixel-art textures drawn by code
- Soft shadows in corners, shade under trees, and a 20-minute day and night cycle with a sun and moon
- Swimming, flying, block-breaking particles and simple sound effects
- Automatic saving in your browser, so your builds are still there when you come back. **New world** in the pause menu starts over with a fresh random seed.
- Adjustable render distance and mouse sensitivity in the pause menu

## How it works

Everything is plain JavaScript and WebGL inside `index.html`:

- **Terrain**: seeded Perlin noise sets the height, rock and snow levels, tree placement and cave tunnels. The world is split into 16 × 16 × 128 chunks, and chunks load and unload around the player.
- **Rendering**: each chunk is turned into one triangle mesh. Hidden faces are skipped and ambient occlusion is worked out per vertex. Water is drawn in a separate see-through pass.
- **Physics**: the player is a 0.6 × 1.8 block box with gravity. Collisions are checked against the block grid one axis at a time.
- **Saving**: only the blocks you change are stored in `localStorage`, together with the world seed and your position.
