# Iterations: Latino Fiesta videos

One entry per version of a look or render, for the videos described in [`latino-fiesta-videos.md`](latino-fiesta-videos.md). The check boards, previews, logs and rejected masters named below are not in this repository.

## Style previews (`previews/`), numpy compositor, 7 Nov 2026

| Label | File | What changed and why | Result |
|---|---|---|---|
| v1 | `v1_9x16.jpg` | First layouts from the cut layers | Grain too heavy (0.55), type too small |
| v1b | `v1b_9x16.jpg` | Grain lowered, splat core and rays redrawn | Better; layouts need more fill |
| v2 | `v2_9x16.jpg` | Vertical layouts filled, leaves bleed off the frame | Accepted for 9:16 |
| v3 | `v3_16x9.jpg`, `v3_4x5.jpg` | Landscape and 4:5 layouts. 4:5 now uses square layouts (portrait means height above 1.4 × width) | Accepted for 16:9 |
| v4 | `v4_1x1_1x1.jpg`, `v4_4x5_4x5.jpg` | Check of square and 4:5 after the threshold change, 3 frames per scene | Accepted, no change needed |

## After Effects masters

| Label | Date | Change and why | Method and settings | Result |
|---|---|---|---|---|
| ae-v1 | 7 Nov 2026 | First full queue | `ae_build.jsx.txt`: baked keys at 15 fps, hold key before each change. ffmpeg x264 CRF 18, 30 fps | Single scenes good. Promos and `perks` wrong: a layer's opacity ramped to 0 between its last key and its hide key, so scenes faded to black before each cut (`ae_vs_preview_dim.jpg`, top row AE, bottom row preview). 62 clips of 254 affected |
| ae-v2 | 7 Nov 2026 | Hold key added before a hide (`HOLD_HIDE`) | As ae-v1 | Applies to every batch built after the fix. 27 masters built before it moved to `tmp/rejected_v1/` and rendered again. `ae_v2_cut_check.jpg`, frames 108 to 122 of `promo-baile_a`, ae-v1 at 1:1 on top, ae-v2 at 16:9 below: the title holds full colour up to the wipe at frame 120, where ae-v1 had already dimmed it. Same-format check, `ae_v2_cut_check_1x1.jpg`: mean brightness at frame 108 is 91 in ae-v1 and 106 in ae-v2, and both read 123 from the cut at frame 120 onward. Fix confirmed |
| ae-v3 | 8 Nov 2026 | `building` scene, 9:16 only: tape and the two corner leaves drawn before the logo and address instead of after | `scenes.py` `scene_building`; specs rebuilt for the 13 clips that contain the scene in 9:16. Address crops from the covers: `resolve/address_check_building.jpg` (16:9 clear, 9:16 covered in both engines), `resolve/address_check_9x16.jpg` (`logo` scene clear). Before/after preview at frame 232: `previews/building_9x16_address_fix.jpg` | Before: the leaves covered "30 ACRE LANE" and "SW2 5" in every 9:16 `building`, `promo-lugar` and `promo-noche` clip. After: the full address reads, the leaves still frame the lower corners. Old masters (10 After Effects, 3 Resolve) moved to `tmp/rejected_v1/building_address_covered/` and rendered again |

## Blender masters

| Label | Date | Change and why | Method and settings | Result |
|---|---|---|---|---|
| bl-v1 | 7 Nov 2026 | First full clip, `carousel` `sol` 9:16 | EEVEE, 24 samples, 240 frames, 147 s while AE rendered | Rejected, kept as `tmp/rejected_v1/lf_bl_carousel_sol_9x16_clipped-colour.mp4`. Diffuse weight was ignored, so lit surfaces summed above 1 and clipped: green palm turned mint. Ray floor turned about the wrong axis and tilted up through the title |
| bl-v3 | 7 Nov 2026 | Diffuse colour scaled by its weight, floor turns about the vertical | Stills at 0.4 scale, 16 samples (`blender/v3_sheet.jpg`) | Colours match the palette. `block` showed cream sticker backs that read as blank blobs |
| bl-v4 | 7 Nov 2026 | `block` stickers swing ±28° and no longer show their backs. Square and landscape stills | `blender/v4_1x1_sheet.jpg`, `v4_16x9_sheet.jpg` | `stage`: title cropped at the bottom and over the face in square and landscape |
| bl-v5 | 7 Nov 2026 | `stage` lettering and hero placed per frame shape, turntable turns about the vertical | `blender/v5_sheet.jpg` | Lettering inside the frame and clear of the face. Accepted for production |
| bl-v6 | 7 Nov 2026 | 4:5 stills; full-resolution check of the `selva` destinations | `blender/v6_4x5_sheet.jpg`, `v6_selva_9x16_check.jpg` | 4:5 `block`, `carousel`, `stage` accepted; `stage` lettering overlaps the couple's bodies, faces clear. `selva` with the `stack` destination wrong in every shape: black slabs over the lower half of each genre word. `building` and `logo` fine |
| bl-v7 | 7 Nov 2026 | Genre bands placed 0.12 apart in depth, each in front of the one above it | `blender/diag_stack_sheet.jpg`: left as built, middle without the thick sides (slabs remain, so the sides are not the cause), right with depth steps | Cause: the cut-outs carry dark ink at their lower edge, which the next band covers in After Effects. In one plane the bands fought for depth. Fixed. The four 9:16 `selva-stack` masters moved to `tmp/rejected_v1/blender_stack_slabs/` and rendered again |
| bl-v8 | 8 Nov 2026 | Stack scale capped at 0.82 of the frame height | Check of the eight 1:1 and 16:9 `selva-stack` masters, all rendered after bl-v7 (`blender/v7_stack_1x1_16x9.jpg`, frames 60, 150, 210): no slabs. In 16:9 the stack was sized from the frame width only and ran 1.38 frame heights, so SALSA and LATIN BEATS were cut off; the same rule gave 1.14 in 4:5. Stills at half size after the cap: `blender/v8_stack_cap_sheet.jpg` (16:9 and 4:5, frames 150 and 210) | Whole stack inside the frame in both. 9:16 (0.80) and 1:1 (0.77) unchanged by the cap. The four 16:9 `selva-stack` masters moved to `tmp/rejected_v1/blender_stack_16x9_cropped/` and queued again; the cap was in place before any 4:5 `selva-stack` render started. Masters checked after rendering, `blender/v8_stack_16x9_4x5_masters.jpg` (frames 150 and 210 of two 16:9 and two 4:5 clips): every band inside the frame. Blender complete: 52 masters in each of 9:16, 1:1, 4:5, 16:9 |

## Resolve masters

Resolve Studio 21.1.1.10, headless (`-nogui`), one Fusion composition per clip, read from the same baked specs as After Effects. The series is every scene and promo in `noche` with a glow, so it adds clips instead of repeating the After Effects set.

| Label | Date | Change and why | Method and settings | Result |
|---|---|---|---|---|
| rs-v0 | 7 Nov 2026 | First attempts crashed or hung | `scripts/rs_bisect.py` imports one tool type per run; stack trace decoded to `tmp/resolve_crash/Callstack.txt` | Crash: `Filter = Input { Value = 3 }` on SoftGlow segfaults Resolve when the composition loads (`glow_filter3` crashes, `glow_nofilter` loads). Hang: a crashed session's reporter and `fuscript -s` keep port 15000, so the next session never starts its script server. Input removed; `rs_queue.py` clears those processes before starting Resolve |
| rs-v1 | 7 Nov 2026 | Print look, no glow, against After Effects | `resolve/rs_v1_vs_ae.jpg`, 240 frames in 50 s | Layout and motion match After Effects. The two test specs had different palettes, so background and leaf colours differ by design |
| rs-v2 | 7 Nov 2026 | Neon look on all four frame shapes | SoftGlow threshold .42 gain .85, tight threshold .6 gain .5, automatic bitrate. `resolve/rs_v2_neon.jpg`, `rs_v2_crop.jpg` | Rejected, 6 clips kept in `tmp/rejected_v1/resolve_neon_gain85/`. Golden `sun` pushed to lemon, splat (249, 255, 11) against (247, 221, 10) in After Effects. Bitrate stayed near 14.6 Mbps and softened the print grain |
| rs-v3 | 7 Nov 2026 | Lower glow, explicit bitrate | SoftGlow threshold .5 gain .5, tight threshold .65 gain .25, `VideoQuality` 40000. `resolve/rs_v3_gain50.jpg`: rs-v2 top, rs-v3 middle, After Effects bottom | Accepted. Splat (249, 242, 9), glow still visible, 41 Mbps |
| rs-q2 | 8 Nov 2026 | Queue order and grouping, no change to the look | First queue (`tmp/logs/rs_queue.log`): groups of 6, promos first. Promos carry 137 to 244 layers and 480 to 720 frames (scenes 15 and 240). One promo rendered in 4 to 10 min, then the next clip in the same session stalled until the group limit; swap was 18.1 of 19.5 GB with Blender rendering alongside. 3.7 h gave 19 masters; `promo-lugar` and `promo-noche` 9:16 dropped after three tries. `rs_queue.py` now renders all scenes first in groups of 6, then each promo in its own Resolve session with a limit of 1.5 × frames + 300 s, and counts a master only when its frame count matches the spec (`tmp/logs/rs_queue_v2.log`) | Scenes: 36 in about 17 min, 6 per 3 min. The first frame check misread Resolve's doubled ffprobe count (`240`, blank line, `240`) as 0 and moved the 20 finished masters aside; the queue was stopped within a minute and all 20 moved back unchanged, then the parser fixed and checked against every master. `promo-noche` 9:16 then hung twice: SIGTERM leaves headless Resolve alive in its crash reporter, so no fresh session started |
| rs-q3 | 8 Nov 2026 | Forced stop between promos | `stop_resolve()` waits up to 15 s, then kills Resolve, its crash reporter and `fuscript -s` with SIGKILL (`tmp/logs/rs_queue_v3.log`) | `promo-noche` 9:16 rendered in 470 s, `promo-corto` 1:1 in 41 s, each in a new session. 74 of 74 in 77 min, none failed, including the three 9:16 re-renders from ae-v3. Address crops after the re-render: `resolve/rs_address_masters.jpg` |

## Covers and QA (`scripts/qa_masters.py`)

| Label | Date | Change and why | Result |
|---|---|---|---|
| qa-v1 | 7 Nov 2026 | Cover at the end of the clip, or for a promo the end of its first scene; 1-fps sheets, four-frame colour check, blank-frame test, yellow and green share | 45 clips checked before the After Effects fix; that state is kept as `qa_state_2026-11-07_1846.json` |
| qa-v2 | 8 Nov 2026 | Clips set aside since the last run are dropped from the state and the manifest | 526 masters, none with a colour jump, blank frames or audio. Yellow and green share mean 0.57; lowest in `rosa` and `mango` (minority palettes, pink and orange grounds by design). Boards in `boards/` |
| qa-v3 | 8 Nov 2026 | `carousel` cover fixed at frame 120: at the end of the clip the ANTRO logo is half off the left edge (`board_blender_4x5.jpg`) | `blender/carousel_cover_frames.jpg`, frames 105, 120, 135 in all four shapes: at 120 the logo sits centred under the title |

## Design system cover

| Label | Date | Change and why | Result |
|---|---|---|---|
| cover-v1 | 7 Nov 2026 | Band of blocks with one chevron row, top-band skeleton because the name exceeds 440 px at 64 px | `ds/cover_light.png`, `ds/cover_dark.png`: readable in both themes |
