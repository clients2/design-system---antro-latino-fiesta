# design-system---antro-latino-fiesta

Short name `latino-fiesta`. Working design system for Latino Fiesta promos at Antro Brixton, London. The Claude.ai
Design System artifact is listed in the register of skill `/style`. Created 7 Nov 2026 by Claude Opus 5.5.

## Layout
| Path | Contents |
|---|---|
| `assets/cutouts/` | 11 layers cut from the supplied sheet, 4× Real-ESRGAN, BiRefNet mattes |
| `assets/parts/` | 31 pieces split from the cut-outs for animation, including palm, flower and conga recolourings |
| `assets/stickers/` | 10 subjects with a cream die-cut border |
| `assets/elements/` | 70 generated elements: brushes, splats, leaves, aguayo bands, papel picado, rays |
| `assets/masks/`, `assets/textures/` | 8 keyed paint masks from the sheet; grit and halftone textures |
| `assets/cut-metadata.json` | Position of each part inside its cut-out, in pixels |
| `artifact/` | The artifact's text files as published: `README.md`, `motion.md`, `tokens.json`, cover |

## Conventions
- Fonts live in `../../assets/fonts/`: `knewave/` (display) and `barlow-condensed/` (information lines). The other
  families moved there on 7 Nov 2026 were candidates and are unused here.
- The video scripts read `assets/` by short name (`fiesta.py`, `blender_fiesta.py`). Renaming a file breaks them, and
  breaks the asset records in the artifact's index.
- Rules for use are in `artifact/README.md`; the artifact is the published copy.
- Source sheet and the generating scripts: `../../projects-uk/client-antro/antro-brixton/video/opus55_2026-11-07-sat_latino-fiesta-videos/`
  (`scripts/cut_*.py`, `scripts/make_elements.py`). Supplied sheet: `../../projects-uk/client-antro/antro-brixton/graphics/gpt6_2026-11-07-sat_vector-conversion/`.
- Public Git repository: https://github.com/clients2/design-system---antro-latino-fiesta, a clean copy of this folder with its own history. It holds no videos, scripts or source sheet. `docs/` holds cleaned copies of the project notes.

## Related
- [`../AGENTS.md`](../AGENTS.md); register of short names: skill `/style`.
