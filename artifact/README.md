Use this system for video and still promos of the Latino Fiesta nights at Antro Brixton, London. It is a working system for that venue's event material. Build every frame from the layers in `assets/`; never redraw the logo, the lettering or the illustrations. Set yellow and green as the majority of every set of clips.

## Content

Set only the words below. Add no date, time, price, ticket offer, DJ name or drink deal unless the venue supplies it.

| Use | Exact copy | Source layer |
|---|---|---|
| Event title | Latino Fiesta | `Parts/03a_latino.png`, `03b_fiesta.png`, `03c_swash.png` |
| Venue | Antro Brixton | `Parts/02a_crown.png`, `02b_wordmark.png` |
| Frequency | Every Weekend | `Parts/16a_ticks.png`, `16b_crown.png`, `16c_every_weekend.png` |
| Music | Salsa, Reggaeton, Bachata, Cumbia, Latin Beats | `Parts/04a_salsa.png` to `04e_latin_beats.png` |
| Offer | Cocktails, Latin Music, Dancing, Good Vibes | `Parts/17a` to `17d`, chip and icon |
| Address | 30 ACRE LANE · BRIXTON SW2 5SG | set in `info` |
| Handle | @ANTROBRIXTON | set in `info` |

Write in English, as the sheet does. Do not add exclamation marks, slogans or Spanish phrases that the venue has not written. Keep the capitals of each source layer. Use no emoji.

## Colour

Choose one palette per scene. Each palette names a colour token for every job in the frame.

| Palette | Ground | Rays | Leaves | Paint | Second paint | Aguayo band |
|---|---|---|---|---|---|---|
| `sol` | `sun` | `mango` | `jungle`, `emerald`, `lime` | `pink` | `jungle` | `aguayo_b` |
| `selva` | `jungle` | `emerald` | `lime`, `sun`, `deep` | `sun` | `pink` | `aguayo_c` |
| `lima` | `lime` | `sun` | `emerald`, `deep`, `jungle` | `pink` | `sun` | `aguayo_c` |
| `noche` | `deep` | `emerald` | `jungle`, `lime`, `emerald` | `sun` | `pink` | `aguayo_b` |
| `mango` | `mango` | `sun` | `jungle`, `emerald`, `deep` | `pink` | `sun` | `aguayo_a` |
| `rosa` | `pink` | `magenta` | `sun`, `lime`, `jungle` | `sun` | `jungle` | `aguayo_a` |

- Use `sol`, `selva`, `lima` and `noche` for at least nine clips in ten. Keep `mango` and `rosa` as the minority.
- Fill the ground with one flat colour and one rays element. Use no gradient.
- Show the art at full value. Never dim, desaturate or blur it to make type readable: move the type or put it on a brush strip.
- Set `ink` type on `sun`, `lime`, `mango` and `jungle`. Set `sun` type on `ink`. Set `cream` type on `pink` only at large sizes (3.4:1).

## Type

- Use the hand lettering in `assets/Parts` first. It is the voice of the sheet.
- Set a new display word in `display` (Knewave) with a knocked-out dry-brush grain, in `sun` or `ink`, rotated with the lettering beside it.
- Set address and handle lines in `info` (Barlow Condensed Black Italic), uppercase, on a brush strip from `assets/Paint`, rotated -3° to -4°: `sun` on an `ink` strip for the address, `cream` on a `pink` strip for the handle.
- Never use Bebas Neue, a neutral sans or a centred line with a glow. Never set a title in a pixel font.
- Render type to PNG before it enters a compositor, so every engine shows the same letters.

## Composition

Build each scene from back to front in this order.

1. Ground: one flat colour from the palette.
2. Rays: `rays_20`, `rays_12` or `rays_wavy_16`, tinted, turning about 16° a second.
3. Fabric: an aguayo band or a `picado` row along one edge, where the scene has one.
4. Leaves: `assets/Leaves`, entering from the corners and bleeding off the frame.
5. Paint: a `splat` or `brush` behind the subject, tinted with the palette's paint.
6. Subject: one sticker from `assets/Stickers`, large, with a hard shadow.
7. Lettering: last and on top, with a hard shadow.

- Fill the frame. Leave no empty field above the fold of a vertical clip.
- Crop large things at the frame edge. In the `huge` scene the title runs off both sides, then the complete lockup lands by the last four beats.
- Use a sticker when the subject's edge would merge with the ground: its `cream` die-cut border separates it.
- Use one subject per scene. A genre scene shows one genre strip, one subject and one flower.
- Give every raised layer a hard shadow in `ink` or `deep`: `hard-s` for icons, `hard-m` for chips, `hard-l` for subjects, `hard-xl` for the largest type. Use no blurred shadow.
- Keep glow to `noche` scenes. Everywhere else the look is flat screen print with the `grit-opacity` overlay.

Lay out for the tall frame when height exceeds 1.4 × width, so 4:5 uses the square layouts.

| Scene | What it shows |
|---|---|
| `title` | Lettering slams over the jungle, then congas and flowers |
| `face` | Face sticker over paint, then the Every Weekend badge |
| `couple` | Dancing couple under a `picado` row, then the title |
| `building` | Logo, venue sticker and palms, then the address |
| `logo` | Logo, address and handle |
| `stack` | The five genre strips land one per beat |
| `perks` | Four tiles: Cocktails, Latin Music, Dancing, Good Vibes |
| `huge` | The title cropped, then the complete lockup |
| `tiles` | Coloured tile grid of icons, then the title on top |
| `genre` | One genre strip with its subject and flower |

## Iconography

The four icons in `Parts/17a` to `17d` are the only icon set: cocktail, level bars, dancers, flame. Use them with their chips. The crowns in `02a_crown` and `16b_crown` are the only marks besides the wordmark. Do not substitute another icon set.

## Imagery

The illustrations are the face, the couple, the congas, the palm, the flower and the venue. Recolour only the layers provided in several colours (`08_palm_*`, `09_flower_*`, `07_congas_*`). Keep the face and the couple as supplied. Tint alpha shapes (`Paint`, `Rays`, `Masks`) with flat palette colours at render time.
