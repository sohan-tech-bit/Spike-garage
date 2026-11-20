# Design language: haunting, decaying, alive

## Palette (CSS variables)
- `--void: #07080a` near-black background
- `--bone: #e8e2d0` text and icons
- `--blood: #8f1d1d` primary accent and danger
- `--ember: #d9822b` warm flicker and highlights
- `--ghost: #7fe8c8` spectral glow for active tools
- `--rot: #3a4a2f` sickly green for secondary surfaces

## Type
- Display headings: a gothic or horror display face (e.g. "Creepster" or "Metal Mania" from Google Fonts, used sparingly)
- UI text: a clean readable face (e.g. "Inter" or "Special Elite" for labels). Readability always wins over spookiness.

## Scene
- Dark garage: concrete floor, corroded walls, a single swinging hanging bulb with flicker
- Low volumetric fog, drifting dust, rare lightning flash through a dirty window
- Car lit by the bulb plus a faint ghost-colored rim light
- Spray tool shows a glowing brush cursor on the car surface

## UI
- Panels look like rusted metal and old paper tags: scratched edges, subtle grain, drip details
- Tool buttons glow `--ghost` when active; destructive actions use `--blood`
- Sticker tray is a dusty shelf of "cursed decals"
- Micro-interactions: spray hiss sound, sticker slap sound, occasional whisper, heartbeat when saving a photo
- Respect `prefers-reduced-motion` and provide a mute button and an effects slider (flicker, fog, jump-effects off)
- Contrast: all body text meets WCAG AA against its background

## Content rules
- Generic car names only. No brand logos in any asset.
- Atmospheric horror, not graphic gore.
