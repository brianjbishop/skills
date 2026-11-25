---
name: stack-prints
description: Model stacked 3D prints — multiple copies of a part printed vertically on top of each other in one job, separated by a small air gap so they pop apart after printing (the Multiboard ironing-stack technique). Use this skill whenever Brian wants to print multiple copies of a part at once, mentions "stack prints", "stacked printing", "print them on top of each other", "batch print vertically", "sprue", "snap-off prints", or asks how to fit more parts in one print job. Covers geometry rules, Blender (bpy) modeling patterns, Fusion 360 patterns, and Bambu Studio slicer settings. Always consult this skill before generating stacked-print geometry — the gap size and layer-height matching are precise and easy to get wrong.
---

# Stack Prints

Model vertical stacks of identical (or flat-topped) parts that print as ONE job and separate cleanly by hand afterward. Based on the Multiboard ironing-stack technique (youtube.com/watch?v=xs2urfM0MRM).

## How it works

Each part in the stack is separated by a **0.2mm air gap** that exactly matches the **0.2mm layer height**. The slicer bridges the first layer of the next part over the ironed top surface of the part below. The single bridged layer adheres weakly — enough to print on, weak enough to snap apart by hand.

**The gap must equal the layer height.** 0.2mm gap ↔ 0.2mm layers. If Brian prints at 0.16mm or 0.28mm layers, regenerate the model with a matching gap. This is the #1 failure mode: mismatched gap = fused parts or mid-air spaghetti.

## Geometry rules — check before modeling

1. **Flat top required.** The part's top face must be a large, flat, continuous surface at a single Z height. The next part's bottom bridges over it. Parts with domes, arms, or pillars sticking up CANNOT stack directly.
2. **Full vertical overlap.** The bottom footprint of part N+1 must be supported by the top face of part N. No cantilevers over the gap.
3. **Flat bottom required.** Same logic inverted — the bottom of each part is what bridges.
4. **Complex parts (connectors with radial arms, spheres, etc.) do not stack.** Options instead:
   - Reorient so a flat face is up/down (e.g. a T-connector lying flat).
   - Add a thin sacrificial "interface plate" between parts (1–2 layers thick, snaps off, leaves scars — last resort).
   - Use a **sprue/runner layout** instead: parts side by side on the bed, joined by 1mm breakaway tabs at neutral points, model-kit style. This is usually the right answer for connector-type parts.
5. **Panels, tiles, plates, and washers are ideal stack candidates.**

## Print settings (tell Brian these every time)

- **Layer height:** 0.2mm (must match the modeled gap)
- **Ironing: ON, all top surfaces** — this is mandatory, not optional. The ironed surface is what the next part bridges over. Without ironing the parts fuse.
- **Seam:** random (adds strength, hides the seam)
- **Walls:** 3 perimeters
- **Infill:** 15%
- **Supports:** none needed
- **Bambu Studio will throw errors/warnings about the 0.2mm gaps — they are safe to ignore.** The .3mf/STL is not broken.

## Honest tradeoffs (mention proactively)

- Ironing adds significant time — a stack can take LONGER than sequential individual prints. The win is unattended batching, not speed.
- The bottom face of each stacked part (except the first) comes out rougher than a bed-printed face. Fine for hidden faces; bad for double-sided cosmetic parts.
- Taller stacks = higher failure risk; one failure kills the whole stack. Start with 3–4 high, not 10.

## Blender pattern (bpy, via MCP)

Remember: `import bpy` explicitly in every code block. Build the base part as a single manifold mesh first (bmesh, remove_doubles, recalc_face_normals), then stack:

```python
import bpy

GAP = 0.2            # mm — MUST equal layer height
COUNT = 4            # stack height in parts

base = bpy.data.objects["PartName"]
part_h = base.dimensions.z

for i in range(1, COUNT):
    dup = base.copy()
    dup.data = base.data.copy()        # independent mesh
    dup.location.z = base.location.z + i * (part_h + GAP)
    bpy.context.collection.objects.link(dup)

# Export ALL stack objects into ONE STL:
bpy.ops.object.select_all(action='DESELECT')
for o in bpy.data.objects:
    if o.name.startswith("PartName"):
        o.select_set(True)
bpy.ops.wm.stl_export(
    filepath="/Users/2b/Desktop/part_stack_x4.stl",
    export_selected_objects=True,
)
```

Notes:
- An Array modifier (relative offset off, constant offset Z = part_h + GAP) also works; apply it before export.
- Verify the gap: `(dup2.location.z - dup1.location.z) - part_h` must equal GAP exactly. Float drift here ruins prints.
- Keep Brian's conventions: export to `~/Desktop` first (emoji Drive paths time out), then `cp` to the Google Drive project folder; versioned filenames, never overwrite.

## Fusion 360 pattern

1. Model the base part as one body; confirm flat top + flat bottom.
2. **Create > Pattern > Rectangular Pattern** → type: Bodies → direction: Z axis → Distance type: **Spacing** → spacing = part height + 0.2mm → quantity = stack count.
   - Or: Move/Copy (M), check "Create Copy", Z distance = part height + 0.2mm, repeat.
3. Spacing is center-to-center in "Spacing" mode? No — Fusion's rectangular pattern "Spacing" is distance between corresponding points, so **spacing = part height + gap** is correct as written.
4. Export: File > Export > STL with "One file" / all bodies selected, or right-click the component (not a single body) > Save as Mesh so all bodies land in one STL.
5. Do NOT combine/join the bodies — they must remain separate bodies with the air gap intact.

## Sprue/runner alternative (for non-stackable parts)

For connector-style parts (radial arms, spheres): lay all parts flat on the bed in print-optimal orientation, connect adjacent parts with breakaway tabs:
- Tab cross-section: ~1 × 2mm, 1–2 layers tall if possible
- Attach tabs at non-critical, non-mating surfaces (never on a socket mouth or fit surface)
- Tabs meet the part at a slight neck (0.6–0.8mm) so they snap flush
- One runner plate = one kit; boolean-union tabs to parts is fine since they're meant to break

## Workflow checklist

1. Confirm part passes geometry rules (flat top AND bottom) — else propose reorientation or sprue.
2. Ask/confirm layer height (default 0.2mm) → set GAP to match.
3. Build stack (Blender or Fusion per above), verify gap arithmetic.
4. Export as ONE file, versioned name (e.g. `part_stack_x4-v1.stl`).
5. Tell Brian the slicer settings: ironing ON all top surfaces, random seam, 3 walls, 15% infill, ignore gap warnings.
6. Recommend a 2-high test stack before committing to a tall one.
