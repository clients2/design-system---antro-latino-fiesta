# Latino Fiesta videos, Antro Brixton

Production notes for 536 silent video masters built from the supplied Latino Fiesta sheet, cut into layers. Claude Opus
5.5 started the work on 7 Nov 2026 and rendered the masters locally with After Effects, Blender and DaVinci Resolve, in
a bright Latin American look led by yellow and green.

The videos and the render scripts are not in this repository. The layers and rules they use are: see
[`../README.md`](../README.md). What changed in each version: [`latino-fiesta-videos-iterations.md`](latino-fiesta-videos-iterations.md).

## Masters (8 Nov 2026)
| Engine | 9:16 | 1:1 | 4:5 | 16:9 | Total | What it is |
|---|---|---|---|---|---|---|
| After Effects | 68 | 68 | 50 | 68 | 254 | 14 scenes in their palettes, and 6 promos in rounds `a`, `b`, `c` (no 4:5 promos) |
| Blender | 52 | 52 | 52 | 52 | 208 | 3D recipes `selva` (6 destinations), `carousel`, `stage`, `block` |
| Resolve | 20 | 20 | 14 | 20 | 74 | Every scene in `noche` with a neon glow, and the 6 promos in round `n` (no 4:5 promos) |
| All | | | | | 536 | Silent H.264, 30 fps; scenes 8 s, promos 8 to 24 s |

## File naming
`lf_<engine>_<recipe>_<palette or round>_<format>.mp4`. Engine: `ae`, `bl`, `rs`. Format: `9x16`, `1x1`, `4x5`, `16x9`.
Palettes: `sol`, `selva`, `lima`, `noche`, `mango`, `rosa`. Promos come in rounds `a`, `b`, `c`, with different palettes.

## Render order
1. Layers: matte, paint masks, finishing and generated elements.
2. Clip specs: one JSON file per clip, baked for After Effects and Resolve.
3. After Effects queue, running in the application window.
4. Blender queue.
5. Resolve queue, headless (`-nogui`): scenes in groups of 6, each promo in its own session. A master counts only when
   its frame count matches the spec. Never give SoftGlow a numeric `Filter` input: it crashes Resolve. A crashed session
   keeps port 15000 through its reporter and `fuscript -s`, so both are stopped before Resolve starts.
6. Checks and covers: one cover per master, 1-fps sheets, a four-frame colour check, a blank-frame test and the share of
   yellow and green.

## Timing and copy
- 120 BPM at 30 fps: one beat is 15 frames, one bar is 60. Masters have no audio. Add a licensed library track of about
  120 BPM in the app, and vary it between clips.
- Copy on screen comes only from the sheet, plus `30 ACRE LANE · BRIXTON SW2 5SG` and `@ANTROBRIXTON`.
