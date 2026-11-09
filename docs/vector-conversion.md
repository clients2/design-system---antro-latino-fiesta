# Antro Brixton asset sheet vector conversion

Converted on 7 Nov 2026 with Adobe image_vectorize. The SVG and the supplied sheet are not in this repository.

The supplied sheet is flattened. Its filename labels and all artwork are included in the trace. Adobe replaced the
original multicolour glow background with white. The result is a complete-sheet trace, not a collection of isolated
transparent assets. Photographic details and paint textures are approximated by traced paths. Vector paths can be edited
and recoloured in Adobe Illustrator; lettering is outlined rather than live text.

Validation: the SVG parses, on a 1536 × 1024 canvas, with 6,283 path elements, two gradients, no embedded raster images
and no external image links.

## Versions
| Version | Date | Change | Method | Result |
|---|---|---|---|---|
| v01 | 7 Nov 2026 | First trace of the supplied image | Adobe image_vectorize | Flat colours simplify photo detail; white background in place of the glow; 3,700,896 bytes |
| v02 | 7 Nov 2026 | Added `viewBox="0 0 1536 1024"` so the artwork scales predictably in SVG viewers | XML root attribute only, no path edits | All 6,283 paths retained. The delivered editable version |
