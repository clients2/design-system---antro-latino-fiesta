# latino-fiesta design system

The design system for the Latino Fiesta promos at Antro Brixton (30 Acre Lane, Brixton SW2 5SG, London). It is
built from the venue's supplied flattened asset sheet. The look is a bright Latin American print style led by
yellow and green, with pink and orange as accents.

This repository holds the rules for use, the tokens, every image layer and the project notes. The system was created
on 7 Nov 2026 by Claude Opus 5.5.

## Contents
| Path | Contents |
|---|---|
| `artifact/README.md` | Rules for use: content, colour, type, composition, iconography, imagery |
| `artifact/motion.md` | Motion and video: named moves, texture in motion, formats and sound; 120 BPM at 30 fps, one beat is 15 frames and one bar is 60 |
| `artifact/tokens.json` | Colour, palette and type tokens |
| `artifact/Cover/preview.html` | Cover card of the artifact |
| `assets/cutouts/` | 27 layers. `01` to `17`: 11 cut from the supplied sheet, upscaled 4× (Real-ESRGAN), BiRefNet mattes. `20` to `35`: 16 generated subjects added on 9 Nov 2026, see `docs/generated-cutouts.md` |
| `assets/parts/` | 31 pieces split from the cut-outs for animation, including palm, flower and conga recolourings |
| `assets/stickers/` | 26 subjects with a cream die-cut border: 10 from the sheet, 16 generated |
| `assets/elements/` | 70 generated elements: brushes, splats, leaves, aguayo bands, papel picado, rays |
| `assets/masks/` | 8 paint masks keyed from the sheet |
| `assets/textures/` | Grit and halftone textures |
| `assets/cut-metadata.json` | Position of each part inside its cut-out, in pixels |
| `docs/` | Project notes: the Latino Fiesta videos and their iterations, the Friday offer reels, the vector conversion of the sheet, the generated cutouts, the generator models (`docs/generator-models.md`), the sixteen reel variations of 10 Nov 2026 (`docs/reel-variations.md`) |

## Palettes
Six palettes share one set of colours (`artifact/tokens.json`). `sol` (yellow ground), `selva` (green), `lima` (lime)
and `noche` (deep green) carry the yellow and green look; `mango` (orange) and `rosa` (pink) are accents.

## Type
| Role | Face | Source |
|---|---|---|
| Display | Knewave Regular | Google Fonts, https://fonts.google.com/specimen/Knewave |
| Information lines (address, handle) | Barlow Condensed Black Italic | Google Fonts, https://fonts.google.com/specimen/Barlow+Condensed |

The font files are not in this repository; download them from Google Fonts.

## Use in the video scripts
The After Effects, Blender and DaVinci Resolve render scripts read `assets/` by file name. Renaming a file breaks
them. The 536 masters of 7–8 Nov 2026 were rendered from these layers.

## Material not in this repository
Videos, render scripts, the supplied flattened sheet and its SVG trace, and font files.
