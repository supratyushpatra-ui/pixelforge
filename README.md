# PixelForge Studio

A beginner-friendly browser-based pixel-art and sprite animation editor built with plain HTML, CSS, and JavaScript. No build tools, dependencies, or server are required.

## Run it

Open `index.html` in a modern browser. For local development, you can also run `python -m http.server 8000` in this folder and visit `http://localhost:8000`.

## Features

- Pixel drawing with pencil, eraser, flood fill, eyedropper, line, and rectangle tools
- Editable canvas dimensions (8–64 pixels in each direction)
- Color picker, hex input, and custom palette
- Undo and redo history
- Horizontal flip and clear frame
- Multi-frame sprite timeline, duplicate/delete frames, and playback (1–24 FPS)
- Export current frame as a crisp, scaled PNG
- Save and reopen projects as JSON
- Responsive dark-futuristic layout
- Keyboard shortcuts: `B` pencil, `E` eraser, `Ctrl/Cmd+Z` undo, `Ctrl/Cmd+Y` redo, `Ctrl/Cmd+S` save

## How it works

Each frame is a flat array of `width * height` entries. An entry is either a CSS hex color or `null` for transparency. The index for pixel `(x, y)` is `y * width + x`. The visible canvas is redrawn from this data after edits. The editor uses a 16× internal drawing scale and `image-rendering: pixelated` for crisp pixels. The animation timeline stores a separate pixel array for every frame.

Project files are JSON, so they are portable and easy to inspect. PNG export creates a temporary canvas at the selected scale and writes only the active frame.

## Suggested learning path

1. Explore the UI and draw a simple 16×16 icon.
2. Inspect `cellAt`, `put`, and `render` to understand pointer-to-pixel mapping and rendering.
3. Try the flood-fill implementation in `flood`.
4. Create two or more frames and inspect `renderFrames` and the playback timer.
5. Save a project, open the JSON file in a text editor, then load it back into PixelForge.
