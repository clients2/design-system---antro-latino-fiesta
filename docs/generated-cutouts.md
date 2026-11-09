# Generated cutouts, 9 Nov 2026

Sixteen subjects that are not on the supplied sheet, generated in its screen-print style by Claude Fable 5.2 and cut with
the same matting method as the sheet layers. Each has a cutout in `assets/cutouts/` and a die-cut sticker in
`assets/stickers/` (`<name>_die.png`). They are additions to the venue's artwork, not the venue's own illustrations.

| File | Subject | Generator |
|---|---|---|
| `20_maracas` | Crossed pair of maracas | Qwen-Image |
| `21_trumpet` | Trumpet | Qwen-Image |
| `22_toucan` | Toucan on a branch | Qwen-Image |
| `23_macaw` | Scarlet macaw in flight | Qwen-Image |
| `24_jaguar` | Roaring jaguar head | Qwen-Image |
| `25_mojito` | Mojito | Z-Image-Turbo |
| `26_margarita` | Margarita | Z-Image-Turbo |
| `27_guitar` | Spanish guitar | Z-Image-Turbo |
| `28_accordion` | Accordion | Z-Image-Turbo |
| `29_calavera` | Sugar skull with marigolds | Z-Image-Turbo |
| `30_monstera` | Monstera leaf | Z-Image-Turbo |
| `31_heliconia` | Flower stem | Z-Image-Turbo |
| `32_disco_ball` | Disco ball | Z-Image-Turbo |
| `33_vinyl` | Vinyl record | Z-Image-Turbo |
| `34_pineapple` | Pineapple | Z-Image-Turbo |
| `35_bongos` | Bongos | Z-Image-Turbo |

## Method
- Qwen-Image (Hugging Face Space, 20 steps) for `20` to `24`; Z-Image-Turbo (4-bit, run locally with mflux, 9 steps) for the rest.
- Matte: 2× Lanczos upscale, BiRefNet, guided refinement, islands under 600 px dropped, edge colour decontaminated.
- Sticker: 22 px cream border, the same as the sheet stickers.

## Known differences from the sheet layers
- `20` to `24` carry the distressed halftone grain of the sheet. `25` to `35` are smoother.
- `25`, `27`, `31`, `32`, `34` and `35` have a white sticker border drawn by the generator inside the cutout.
- `31_heliconia` reads as a trumpet-flower stem, not a heliconia.
- The video scripts do not use these layers yet.
