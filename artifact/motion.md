# Motion and video

Cut everything to 120 BPM at 30 fps: `beat-frames` is 15, `bar-frames` is 60. Land every entrance on a beat and every scene change on a bar line.

Animate on twos: hold each pose for `step-frames` (2 frames). Render 2D compositions at 15 fps and convert to 30 fps, so no in-between frame appears.

## Named moves

Values are read one per step, then held.

| Move | Property | Values | Use |
|---|---|---|---|
| `slam` | scale | 2.6, 1.45, 0.9, 1.05, 0.98, 1 | Titles and logo, with a frame shake |
| `pop` | scale | 0.2, 1.28, 0.9, 1.07, 0.98, 1 | Stickers, flowers, chips |
| `wipe` | x scale from the left edge | 0.04, 0.42, 0.86, 1.05, 1 | Brush strips and genre strips |
| `fly` | offset from rest | 1, 0.55, 0.2, -0.05, 0.02, 0 | Leaves and subjects entering from an edge |
| `fly out` | offset from rest | 0, 0.1, 0.35, 0.75, 1.2 | Leaving at the end of a scene |
| `pulse` | scale | +7% on each beat | Lettering at rest |
| `rock` | rotation | ±3° on each beat | Subjects at rest |
| `hop` | y offset | 26 px on each beat | Small stickers |
| `sway` | rotation | ±3° over one bar | Leaves |
| `spin` | rotation | 16° to 20° a second | Rays |
| `shake` | frame position | 26 px, decaying over 5 steps | With each `slam` |

## Texture in motion

- Boil the edges of lettering and stickers with a displacement whose seed changes at `boil-fps` (5 a second).
- Lay `Textures/grit_knockout.png` over the frame at `grit-opacity`.

## Formats and sound

Deliver the frames listed under Frame formats in the tokens. Masters are silent. Add a licensed library track of about 120 BPM with a driving beat, and vary the track between clips. Choose a cover from the strongest frame of each clip, not the first frame.
