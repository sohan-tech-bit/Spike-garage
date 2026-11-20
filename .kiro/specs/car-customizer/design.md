# Design: Spike Garage car customizer

## Architecture
```
src/
  main.tsx, App.tsx
  scene/        Garage.tsx, Car.tsx, Lights.tsx, Fog.tsx
  paint/        paintCanvas.ts, brush.ts, sprays.ts, interpolate.ts
  stickers/     stickerStore.ts, StickerTray.tsx, transforms.ts
  state/        useAppStore.ts (Zustand), history.ts
  ui/           Toolbar.tsx, ColorPanel.tsx, CarPicker.tsx, theme.css
  audio/        ambient.ts, sfx.ts
  lib/          export.ts, storage.ts
public/
  models/       CC0 car models (see ASSETS.md)
  stickers/     original SVG/PNG stickers
  audio/        CC0 sounds
```

## Key data types
```ts
type Tool = 'spray' | 'eraser' | 'sticker' | 'select';

interface Stroke { id: string; tool: 'spray' | 'eraser'; kind: SprayKind; color: string; size: number; opacity: number; softness: number; points: { u: number; v: number }[]; }

interface Sticker { id: string; assetId: string; u: number; v: number; rotation: number; scale: number; z: number; }

interface DesignState { carId: string; strokes: Stroke[]; stickers: Sticker[]; }
```
The design is stored as data (strokes + stickers), and the paint canvas is re-rendered from it. This makes undo/redo, save/load and testing simple and deterministic.

## Paint pipeline
1. Pointer move on the car mesh produces a raycast hit with a `uv`.
2. `interpolate(prev, next, spacing)` yields evenly spaced dabs.
3. `brush.drawDab(ctx, dab)` draws a soft radial gradient on the paint canvas.
4. The `CanvasTexture` is flagged for update once per frame.
5. On pointer up, the stroke is committed to the history stack.

## History
Command-style stack: `push(action)`, `undo()`, `redo()`. State is derived by replaying actions, which makes properties easy to test.

## Error handling
- Model load failure: show an in-theme error panel with a retry button.
- WebGL unavailable: show a friendly fallback message.
- localStorage unavailable or full: continue without saving and show a small warning.

## Testing strategy
- Unit: `interpolate`, brush math, transforms, history.
- Property-based (fast-check): undo/redo round trips, scale bounds, replay determinism.
- Manual: performance check on a mid laptop and a phone.
