# Generator models used for the generated cutouts

Notes on every model and tool used on Monday 9 Nov 2026 to make the 16 generated cutouts (`20_maracas` to
`35_bongos`) of the design system `latino-fiesta`. Written by Claude Fable 5.2 (`claude-fable-5-2`), which chose
the subjects, wrote the prompts and scripts, and picked the versions. Total cost: none.

Machine: MacBook, Apple M5, 16 GB memory. The scripts, raw images, logs and review boards named below (`scripts/`,
`results/`) are working material and are not in this repository.

## Summary
| Step | Model or tool | Where it ran | Files | Cost |
|---|---|---|---|---|
| Image generation, v1 | Qwen-Image | Hugging Face Space `mcp-tools/Qwen-Image` (free ZeroGPU) | `20` to `24` | Free quota |
| Image generation, v2 and v3 | Z-Image-Turbo, 4-bit quantised | This Mac, through mflux 0.22.0 | `25` to `35` | None |
| Background removal | BiRefNet (`birefnet-general`) | This Mac, through rembg 2.0.87 | all 16 | None |

## 1. Qwen-Image (Hugging Face Space)
- **Access:** Space `mcp-tools/Qwen-Image`, API endpoint `/generate_image`, called from `scripts/gen_subjects.py`
  with `gradio_client` 2.7.2 and a Hugging Face login.
- **Settings:** 20 inference steps, guidance scale 4.0, fixed seed, negative prompt sent.
- **Output size:** 1328 × 1328 px for 1:1, 1584 × 1056 px for 3:2.
- **Time:** 21 to 47 s per image, queue included.
- **Seeds:** the file number (maracas 20, trumpet 21, toucan 22, macaw 23, jaguar 24).
- **Limit reached:** the free ZeroGPU quota ran out after five images. Error text: "You have exceeded your free
  ZeroGPU quota (80s requested vs. 5s left). Try again in 23:46". Each call reserves 80 s of GPU time. The quota
  resets about 24 hours later, so from the evening of 10 Nov 2026. Hugging Face PRO gives 40 minutes of ZeroGPU a
  day; its price was not checked.
- **Result:** closest to the supplied sheet. Thick ink outlines, solid black shadow shapes, distressed dry-brush and
  halftone grain. All five subjects came out isolated on the grey ground and were used.
- **Not checked:** which Qwen-Image checkpoint and scheduler the Space runs.

## 2. Z-Image-Turbo, 4-bit (local)
- **Access:** model repository `filipstrand/Z-Image-Turbo-mflux-4bit`, run with the command
  `mflux-generate-z-image-turbo` (mflux 0.22.0, MLX on Apple silicon), called from `scripts/gen_local.py`.
- **Download:** 5.5 GB, cached in a folder set through `HF_HOME`.
- **Settings:** 9 steps, fixed seed, negative prompt passed with `--negative-prompt`.
- **Output size:** 1024 × 1024 px for 1:1, 896 × 1152 px for 3:4, 1216 × 832 px for 3:2 (not used).
- **Time:** about 60 to 70 s per image on the M5; 150 s for the first image, which includes loading the model.
- **Seeds:** file number + 1000 × version (v2: 2025 to 2035, v3: 3025 to 3035).
- **Result:** smoother and cleaner than Qwen-Image, with less grain and less dry-brush texture. It follows the
  wording of the prompt literally, see the prompt notes below.
- **Not checked:** whether the negative prompt has any effect on this distilled model.

## 3. BiRefNet (matting)
- **Access:** rembg 2.0.87 with session `birefnet-general`, onnxruntime 1.31.1, in `scripts/cut_generated.py`.
- **Steps:** 2× Lanczos upscale, BiRefNet mask, guided-filter refinement against the grey image, smoothstep between
  0.30 and 0.70, islands under 600 px dropped, edge colour decontaminated from the nearest opaque pixel.
- **Sticker:** 22 px cream border (`#FFF6E0`), the same as the sheet stickers.
- **Result:** clean mattes on all 16, checked on yellow, green, pink, dark green and lime grounds
  (`results/checks/cutouts-set1.jpg`).

## Prompts
Each prompt is `<subject sentence>. <style block>`. The subject sentences are in `SUBJECTS` in
`scripts/gen_subjects.py`; every full prompt is in `results/gen-log.tsv`.

**Style block v1 and v2** (`STYLE`):
> Bold screen-print poster illustration in the style of a Latin American street party poster. Thick black ink
> outlines and solid black shadow shapes, distressed dry-brush and halftone grain texture, flat saturated colours
> limited to golden yellow, hot magenta pink, orange, cyan and cream. One single subject, complete and uncropped,
> centred, filling most of the frame. Isolated on a plain flat light grey background, no cast shadow, no glow, no
> frame, no lettering.

**Style block v3** (`STYLE_V3`, local model only):
> Die-cut sticker illustration of one single object, screen-print style: thick black ink outline, solid black shadow
> shapes, halftone grain texture, flat saturated colours limited to golden yellow, hot magenta pink, orange, cyan
> and cream. The object is complete, uncropped and centred, with empty space around it. Plain flat white background
> with nothing else on it: no panel, no paper, no card, no colour blocks, no lettering.

**Negative prompt** (all versions):
> text, letters, watermark, signature, logo, border, frame, photo, 3d render, gradient background, blurry, cropped,
> multiple objects, cast shadow

## What each model did with the prompts
| Version | Model | Prompt | Made | Used | Observed |
|---|---|---|---|---|---|
| v1 | Qwen-Image | `STYLE` | 5 | 5 | Isolated subjects, sheet-like grain |
| v2 | Z-Image-Turbo | `STYLE` | 11 | 4 | "Poster" was taken literally: six subjects were drawn as a poster on a coloured panel, and the vinyl record carried garbled lettering. Margarita, accordion, sugar skull and monstera were isolated |
| v3 | Z-Image-Turbo | `STYLE_V3` | 7 | 7 | All isolated. "Die-cut sticker" made the model draw a white border on six of them. The heliconia prompt gave a trumpet-flower stem |

## Version used for each file
| File | Model | Version | Seed | Raw size |
|---|---|---|---|---|
| `20_maracas` | Qwen-Image | v1 | 20 | 1328 × 1328 |
| `21_trumpet` | Qwen-Image | v1 | 21 | 1584 × 1056 |
| `22_toucan` | Qwen-Image | v1 | 22 | 1328 × 1328 |
| `23_macaw` | Qwen-Image | v1 | 23 | 1328 × 1328 |
| `24_jaguar` | Qwen-Image | v1 | 24 | 1328 × 1328 |
| `25_mojito` | Z-Image-Turbo | v3 | 3025 | 896 × 1152 |
| `26_margarita` | Z-Image-Turbo | v2 | 2026 | 1024 × 1024 |
| `27_guitar` | Z-Image-Turbo | v3 | 3027 | 896 × 1152 |
| `28_accordion` | Z-Image-Turbo | v2 | 2028 | 1024 × 1024 |
| `29_calavera` | Z-Image-Turbo | v2 | 2029 | 1024 × 1024 |
| `30_monstera` | Z-Image-Turbo | v2 | 2030 | 1024 × 1024 |
| `31_heliconia` | Z-Image-Turbo | v3 | 3031 | 896 × 1152 |
| `32_disco_ball` | Z-Image-Turbo | v3 | 3032 | 1024 × 1024 |
| `33_vinyl` | Z-Image-Turbo | v3 | 3033 | 1024 × 1024 |
| `34_pineapple` | Z-Image-Turbo | v3 | 3034 | 896 × 1152 |
| `35_bongos` | Z-Image-Turbo | v3 | 3035 | 1024 × 1024 |

All raw images, including the unused v2 versions, are in `results/raw/` (19 MB).

## Comparison of the two generators
| | Qwen-Image | Z-Image-Turbo 4-bit |
|---|---|---|
| Match to the sheet | Close: grain, dry-brush, heavy black | Partial: correct palette and outline, smoother surfaces |
| Isolation with the first prompt | 5 of 5 | 4 of 11 |
| Raw size | 1328 px | 1024 px |
| Time per image | 21 to 47 s | 60 to 70 s |
| Limit | Free quota: five images a day at these settings | None; needs 5.5 GB of disk |
| Works offline | No | Yes, after the download |

## How to run them again
Use a Python environment with `gradio_client`, `rembg`, `opencv-python`, `scipy` and `Pillow`, and mflux installed
for the local model.

```sh
# Qwen-Image on Hugging Face; skips raw files that exist
python scripts/gen_subjects.py v4 25_mojito 27_guitar

# Z-Image-Turbo locally; downloads 5.5 GB on the first run
python scripts/gen_local.py v4 31_heliconia

# Matte and write cutout and sticker into the design system
python scripts/cut_generated.py <design system folder> 31_heliconia=v4
```

A new version number changes the seed. `gen_local.py` uses `STYLE_V3` for v3 and later; `gen_subjects.py` always
uses `STYLE`.

## Open
- One look across the set: regenerate `25` to `35` with Qwen-Image, five images a day on the free quota, so three
  days for eleven.
- Remove "die-cut sticker" from `STYLE_V3` to stop the generator-drawn white border, and test whether the subjects
  stay isolated.
- `31_heliconia`: describe the plant by shape ("hanging chain of red and yellow claw-shaped bracts") instead of by
  name.
