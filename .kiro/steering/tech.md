# Tech stack and conventions

## Stack
- Vite + React + TypeScript (strict)
- three.js via @react-three/fiber and @react-three/drei
- Zustand for app state (tool, color, brush, sticker list, history)
- Plain CSS modules or a single `theme.css` with CSS variables (no heavy UI kit)
- Vitest for unit tests, fast-check for property-based tests
- Deploy: Vercel or Netlify (static build)

## Painting approach
- Each car has a UV-unwrapped mesh. Paint into an offscreen `CanvasTexture` that is applied as the car's paint layer.
- Raycast pointer to the mesh, read the hit `uv`, draw brush dabs on the canvas at that UV, set `texture.needsUpdate = true`.
- Interpolate between pointer samples so fast strokes leave no gaps.
- Keep the paint canvas at 2048x2048 (fallback 1024 on weak devices).
- Stickers are decals: store as data (id, assetId, uv position, rotation, scale, z-order), render them into the same canvas or as `DecalGeometry`. Pick one and stay consistent.

## Code style
- Small pure functions for anything testable: brush math, UV interpolation, sticker transforms, history stack.
- UI components stay thin; logic lives in `src/lib/`.
- No `any`. No unused code. Name things plainly.
- Performance budget: car under 80k triangles, steady 60fps on a mid laptop, lazy-load models.

## Testing
- Unit tests for the history stack (undo/redo), sticker transforms, brush interpolation.
- Property-based tests (fast-check): undo then redo returns the same state; any sequence of operations followed by full undo returns the empty state; sticker scale stays inside min/max bounds.

## Repo hygiene (hackathon rules)
- Public GitHub repo with an open-source license file (MIT) visible in the About section.
- `/.kiro` folder at the repo root and **never** in `.gitignore`.
- README includes run instructions, live URL, and a "How Kiro was used" section.
