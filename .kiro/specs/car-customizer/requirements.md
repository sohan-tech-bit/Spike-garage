# Requirements: Spike Garage car customizer

## R1. Garage scene and car viewing
**User story:** As a visitor, I want to enter a haunted 3D garage and look around my car so that I feel immersed.
- R1.1 The app loads a dark garage scene with fog and a flickering light.
- R1.2 The user can orbit, zoom and pan around the car with mouse and touch.
- R1.3 Camera limits prevent going under the floor or too far away.
- R1.4 A loading screen shows progress while the model loads.

## R2. Car selection
**User story:** As a user, I want to pick from several cars so the project is mine.
- R2.1 At least 3 cars are available, each with a generic invented name.
- R2.2 Switching cars keeps the chosen tool settings and resets (with confirmation) the paint and stickers.
- R2.3 No real brand names or logos appear anywhere.

## R3. Spray painting
**User story:** As a user, I want to spray paint directly on the car surface in detail.
- R3.1 Dragging on the car paints at the pointer position on the surface.
- R3.2 The user can set color, brush size, opacity and edge softness.
- R3.3 Fast strokes are continuous with no gaps.
- R3.4 Special sprays are available: rust, blood drip, cobweb, glow-in-the-dark.
- R3.5 A color picker and a set of preset horror colors are provided.
- R3.6 An eraser removes paint back to the base finish.

## R4. Stickers
**User story:** As a user, I want to add spooky stickers and arrange them precisely.
- R4.1 A sticker tray shows original sticker packs (bats, skulls, ravens, flames, eyes, runes, cobwebs).
- R4.2 Clicking a sticker then clicking the car places it on the surface.
- R4.3 A placed sticker can be selected, moved, scaled, rotated, layered up/down and deleted.
- R4.4 Scale is limited to a minimum and maximum.
- R4.5 No third-party logos or trademarks are included in sticker packs.

## R5. History and saving
- R5.1 Undo and redo for every paint stroke and sticker action.
- R5.2 Clear-all with confirmation.
- R5.3 Export a PNG screenshot of the current view.
- R5.4 Design state is kept in localStorage so a refresh does not lose work.

## R6. Atmosphere and accessibility
- R6.1 Ambient horror audio with a mute control.
- R6.2 Effects intensity slider and `prefers-reduced-motion` support.
- R6.3 All controls are keyboard reachable and labeled.
- R6.4 Runs at a steady frame rate on a mid-range laptop and works on a phone browser.

## Out of scope (until the core is finished)
Wheel/window customization, share links, multiplayer, photo mode.
