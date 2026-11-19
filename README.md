# Kitty Game

A browser-based, side-scrolling pixel-art platformer starring Sonia. Guide her through three levels, handle pig enemies, collect useful items, and reach James.

The game is built with HTML Canvas and vanilla JavaScript; it does not require a game engine or third-party runtime libraries.

## Current game design

- **Three tile-map levels.** Level 3 is a 25×200 map. Its original 15-row play area starts at row 10; the camera reveals the ten rows above it as Sonia climbs.
- **Pig encounters.** S attacks defeat Ribbon Pigs. Armored Pigs cannot be defeated by ordinary attacks, but Sleep Powder can put them to sleep.
- **Collectible backpack items.** The backpack pauses the game and shows the selected item's description.
- **Cool Sunglasses.** Wear them to reveal hidden bricks while normal bricks disappear. Both tile types remain solid. Wearing the glasses also adds a dark screen overlay. Select the glasses in the backpack and press Enter to wear them; press Enter during gameplay to toggle them on or off.
- **Level transitions.** Reach James to complete a level, then press Enter to continue.

## Controls

| Input | Action |
| --- | --- |
| A / D | Move left / right |
| W | Jump; hold to hover when the hover ability is available |
| S | Attack |
| B | Open or close the backpack |
| WASD | Select an item while the backpack is open |
| Enter | Confirm the selected item and close the backpack; selected Sunglasses are worn automatically. In gameplay, Enter toggles the Sunglasses when selected or already worn |
| Esc | Close the backpack |
| Ctrl+Shift+L | Enter a level number to start that level directly for testing |

The title menu can also be navigated with W/S and Enter or by clicking.

## Editing levels

Level maps are editable arrays in `levels/level1.js`, `levels/level2.js`, and `levels/level3.js`. Their width and height are read from the arrays.

Tile values:

- `0`: empty
- `1`: normal brick, visible when the Sunglasses are off
- `2`: hidden brick, visible when the Sunglasses are on
- `10`: special tile using the image configured in `LEVEL_TILE_IMAGE_PATHS`

Nonzero tiles are solid. Entity and item markers are:

- `-1`: James
- `-2`: Ribbon Pig
- `-3`: Armored Pig
- `-4`: Sleep Powder
- `-5`: Cool Sunglasses

Item images, names, and backpack descriptions are configured in `LEVEL_ITEM_DEFINITIONS` in `game/level.js`.

## Run locally

Open `index.html` in a browser, or serve the project directory locally:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080`.

## Project layout

- `levels/`: tile-map data and map markers
- `game/`: asset loading, tile collision/rendering, enemies, inventory, title, and level-complete behavior
- `assets/backgrounds/`: title, game-over, level-complete, and per-level backgrounds
- `assets/characters/` and `assets/props/`: character animations and game items
- `main.js`: shared game state, camera, physics, and main loop

The old parallax mountain pack and `assets/Tileset.png` are not used by the current design. Each level uses its own `assets/backgrounds/levelN.png`; brick tiles use `assets/props/brick-tile.png`.

Music: “Cyberpunk Moonlight Sonata” by Joth, via [OpenGameArt](https://opengameart.org/content/cyberpunk-moonlight-sonata).
