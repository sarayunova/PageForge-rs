# PageForge app icon

<img src="hicolor/128x128/apps/ai.storyteller.pdfcraft.png" alt="PageForge app icon: a white document and pencil on blue" width="128">

> **Current icon (PageForge):** a white document-and-pencil glyph on a blue tile, by LiVi Software Company (`pageforge-icon-source.png`), masked to the rounded tile. It is used for `pdfcraft.ico`, `pdfcraft-1024.png` and `hicolor/<size>/apps/ai.storyteller.pdfcraft.png`. The source art has a small sparkle mark in its bottom-right corner. The file names are unchanged so packaging needs no edits.
>
> **Not yet replaced:** `pdfcraft.svg`, `pdfcraft-small.svg`, `pdfcraft.icns` and `hicolor/scalable` are still the PdfCraft lion described below.

## PdfCraft lion (previous icon)

**Creature:** a lion, in a frontal head-and-shoulders portrait, mane running off the bottom of the tile.

**Style:** an engraving (woodcut-weight line work) portrait in the Crafting Apps "owl template" framing:
a full-bleed colour field, no frame or roundel, the animal looking at the viewer and filling the tile.

**Palette:** exactly three colours.

| Colour | Hex | Used for |
|---|---|---|
| Ink | `#0b0b0c` | line work and the figure's contour |
| Paper | `#efe9dc` | the figure (the lion's silhouette) |
| PdfCraft green (app colour) | `#12a58a` | the full-bleed field |

**Tile:** `viewBox="0 0 512 512"`, a rounded square with `rx=112` that clips everything. Windows and Linux
icons use the full-bleed tile. macOS icons put it on Apple's grid (an 824 px body centred on a transparent
1024 px canvas).

**Provenance:** the project owner's original drawing, made in ArtCraft (2880 px, keyed to the palette), then
vectorised with craftrules `assets/logo-options/_tools/vectorize_tile.py` (potrace; no filtering or
warping). The source drawing is kept in craftrules at `assets/app-icons/pdfcraft/source.png`, not here.
Licence: [LICENSE.txt](LICENSE.txt) (`MIT OR Apache-2.0`, like the repo).

## Files

| File | What it is |
|---|---|
| `pdfcraft.svg` | the master vector (traced at 2048 px); every PNG, `.ico` and `.icns` is rendered from it |
| `pdfcraft-small.svg` | a lighter vector (traced at 1024 px) for places where size matters, such as this README |
| `pdfcraft-1024.png` | 1024 px on Apple's grid; also the runtime Dock icon on macOS |
| `pdfcraft.icns` | macOS icon (16–1024 px) |
| `pdfcraft.ico` | Windows icon (16–256 px), embedded in `pageforge.exe` by `apps/pdfcraft/build.rs` |
| `pdfcraft-document.svg` | Windows PDF file icon master: a Lucide document outline, green badge and outlined PDF lettering; no font dependency |
| `pdfcraft-document.ico` | Windows PDF file icon (16–256 px), embedded as resource 2 in `pageforge.exe` |
| `hicolor/<n>x<n>/apps/ai.storyteller.pdfcraft.png` | Linux hicolor theme, 16–512 px; the 256 px one is the runtime icon on Windows and Linux |
| `hicolor/scalable/apps/ai.storyteller.pdfcraft.svg` | Linux scalable icon (copy of the master) |

Where it shows: `apps/pdfcraft/src/main.rs` sets the window icon (Dock, taskbar, Alt-Tab, launcher) and the
Wayland app id `ai.storyteller.pdfcraft`; `packaging/linux/ai.storyteller.pdfcraft.desktop` names the
hicolor icon.

The Windows installer shows PDF files that PageForge opens with the PageForge app icon (resource 1,
`"pageforge.exe",0`); resource 2, the PDF document icon, is embedded but no longer referenced. Its document outline is adapted from Lucide `file-text`
1.49.0 (ISC); its badge and outlined lettering are original (`MIT OR Apache-2.0`), covered by
[LICENSE-document.txt](LICENSE-document.txt). Both icons are embedded, requiring no runtime
sidecar. This provides a file type icon; first-page thumbnails still need a thumbnail provider.

## Regenerate

```sh
packaging/icons.sh        # needs resvg and python3; iconutil (macOS) for the .icns
cargo xtask assets        # then update the sha256 values in ATTRIBUTION.toml and run with --write
```
