# Complete Prompt Package v2.2: "The Tiny World You Almost Stepped On"

## What's New in v2.2
- **Reference image workflow** - Generate style guides FIRST for consistency
- **Character sheets** - Tiny beings look the same across all shots
- **Architecture reference** - Mushroom buildings are consistent
- **Surface reference** - Boot and crack match between shots

---

## QUICK OVERVIEW

**Concept**: 27-second TikTok discovering hidden miniature civilization in sidewalk cracks

**Production Phases**:
1. **Phase 0**: Generate 4 reference images (style, architecture, characters, surface)
2. **Phase 1**: Generate 6 production frames using references
3. **Phase 2**: Generate 3 videos from production frames
4. **Phase 3**: Add text overlays and audio

---

# PHASE 0: REFERENCE ART (Generate First)

These establish visual consistency across all shots. Generate these BEFORE any production frames.

## Reference 1: World Style Guide

**Purpose**: Color palette, lighting, atmosphere for all underground shots

```
Fantasy underground world style guide reference sheet, showing color palette
swatches and lighting examples, bioluminescent cyan and warm amber color scheme,
magical glow effects demonstration, atmosphere and fog examples, crystal light
refraction, root textures with golden veins, multiple small example vignettes
showing the aesthetic, dark cavern background with glowing elements, reference
sheet layout, concept art style, vertical composition 9:16, 8k detailed
```

**Save as**: `ref-01-world-style.png`

---

## Reference 2: Architecture Sheet

**Purpose**: Building designs that stay consistent across shots

```
Fantasy miniature architecture reference sheet, multiple views of mushroom cap
buildings with carved windows and doors in the stems, crystalline tower designs
that glow from within, structures made from acorn shells and seed pods, grass
bridge construction details, central great tree with glowing root veins in bark,
showing front view side view and detail callouts, warm amber and cyan bioluminescent
lighting, fantasy concept art style, reference sheet layout with multiple examples,
vertical composition 9:16, 8k detailed
```

**Save as**: `ref-02-architecture.png`

---

## Reference 3: Character Design Sheet

**Purpose**: Tiny beings look identical in every appearance

```
Tiny humanoid creature character design reference sheet, small fairy-like being
approximately 1cm tall relative to human scale, ambiguous but intelligent features,
slightly larger eyes than human proportions, wearing clothing made from woven
leaves and grass fibers, showing front view back view side view and detail callouts,
neutral pose and waving pose, subtle golden glow aura around the figure, fantasy
realism style not cartoon, muted earth tone clothing with slight magical shimmer,
character turnaround sheet layout, vertical composition 9:16, 8k detailed
```

**Save as**: `ref-03-characters.png`

---

## Reference 4: Surface World Elements

**Purpose**: Boot and sidewalk match between Shot 1 and Shot 3

```
Realistic reference sheet for street photography elements, worn brown leather
work boot from multiple angles showing scuff marks and weathering, cracked grey
concrete sidewalk texture with prominent dark crevice, harsh daylight shadow
examples, dust particle reference, mundane urban realism, photographic reference
style, showing boot from below angle and side angle, crack detail close-up,
reference sheet layout, vertical composition 9:16, 8k photorealistic
```

**Save as**: `ref-04-surface.png`

---

## Reference Quality Check

Before proceeding, verify:
- [ ] Style guide has clear cyan/amber color examples
- [ ] Architecture has recognizable mushroom building design
- [ ] Character sheet has clear figure proportions + waving pose
- [ ] Surface has distinctive boot design + crack shape

**If any reference is weak**: Regenerate it before continuing.

---

# PHASE 1: PRODUCTION FRAMES (Using References)

Generate in this order. Each prompt specifies which references to use as input.

## Frame 1: Underground City Aerial
**Used in**: Shot 1 End, Shot 2 Start
**References**: Style Guide + Architecture

```
Aerial view looking down at a breathtaking miniature fantasy city built inside
an underground cavern, mushroom cap buildings with carved windows in stems
matching the reference architecture design, crystalline spires glowing from
within, structures from acorn shells and natural materials, streets lit by
bioluminescent plants in cyan and amber matching reference color palette,
tiny silhouetted figures visible on streets below, cavern ceiling with hanging
roots, magical atmosphere with fog density matching reference, tilt-shift
photography effect, vertical composition 9:16, 8k ultra detailed
```

**Input references**:
- `ref-01-world-style.png` (color/atmosphere)
- `ref-02-architecture.png` (building designs)

**Save as**: `prod-01-city-aerial.png`

---

## Frame 2: Beings Looking Up
**Used in**: Shot 2 End
**References**: Style Guide + Architecture + Characters

```
Ground level inside miniature underground city at base of great central tree
matching reference tree design, crowd of tiny humanoid figures matching character
reference gathered looking upward toward cavern ceiling, faces lit by ambient
bioluminescent glow matching reference lighting, one figure in foreground points
upward with arm raised in waving pose from character reference, figures wear
leaf and grass clothing from character reference, great tree trunk pulses with
golden light veins, wonder and concern on faces, dramatic upward perspective,
colors match world style reference, vertical composition 9:16, 8k detailed
```

**Input references**:
- `ref-01-world-style.png` (color/lighting)
- `ref-02-architecture.png` (tree design)
- `ref-03-characters.png` (figure design)

**Save as**: `prod-02-beings-lookup.png`

---

## Frame 3: Rising Through Cavern
**Used in**: Shot 3 Start
**References**: Style Guide + Architecture

```
Vertical view looking up through underground cavern toward bright opening above,
rising perspective, cavern walls show multiple civilization levels with cities
built into walls using architecture from reference sheet, glowing root networks
connecting settlements, bridges spanning void using grass bridge design from
reference, tiny window lights, crack of surface light above, vast scale, multiple
miniature cities at different levels, bioluminescent plants and crystals using
color palette from style reference, dramatic vertical composition, 9:16, 8k
```

**Input references**:
- `ref-01-world-style.png` (colors)
- `ref-02-architecture.png` (buildings, bridges)

**Save as**: `prod-03-cavern-rise.png`

---

## Frame 4: The Hook (Boot Above)
**Used in**: Shot 1 Start
**References**: Surface Elements

```
Extreme low angle photograph looking straight up from ground level at a giant
worn leather boot descending from above matching the boot design in surface
reference, the boot fills the upper 60% of frame with dramatic foreshortening,
motion blur suggesting downward movement, below the boot is cracked grey concrete
sidewalk with crack shape matching surface reference, dust particles visible in
harsh sunlight, hyperrealistic street photography style, threatening perspective,
tension, vertical composition 9:16, photorealistic, 8k detail, dramatic shadows
```

**Input references**:
- `ref-04-surface.png` (boot design, crack shape)

**Save as**: `prod-04-hook-boot.png`

**Note**: Leave bottom 20% clear for "Wait—" text overlay

---

## Frame 5: The Wave (Final Shot)
**Used in**: Shot 3 End
**References**: Surface Elements + Characters + Style Guide

```
Ground level photograph of cracked concrete sidewalk in daylight, crack shape
matching surface reference, at crack edge stands tiny humanoid figure matching
character reference design exactly, figure has subtle golden glow aura matching
the glow intensity from character reference, figure waves upward in the waving
pose from character reference, worn boot in background matching surface reference
boot design frozen mid-step, harsh daylight casting shadows, mundane surface
world contrasted with magical tiny glowing figure, other cracks hint at faint
glow using colors from style reference, vertical 9:16, 8k photorealistic
```

**Input references**:
- `ref-04-surface.png` (boot, crack, concrete)
- `ref-03-characters.png` (figure design, pose, glow)
- `ref-01-world-style.png` (glow color for figure + crack hints)

**Save as**: `prod-05-wave-final.png`

**Note**: Leave center clear for "They're everywhere. Look closer." text

---

## Frame 6 (Optional): Transition Dive
**Used in**: Shot 1 (if using sub-shot approach)
**References**: Style Guide

```
Falling through a dark void toward underground world, layers of soil and roots
visible on walls rushing past, motion blur suggesting rapid descent, warm
bioluminescent glow growing brighter below using colors from style reference,
sense of speed and depth, roots have golden vein texture from style reference,
vertical composition 9:16, 8k detailed
```

**Input references**:
- `ref-01-world-style.png` (glow colors, root texture)

**Save as**: `prod-06-dive-transition.png` (optional)

---

## Production Frame Quality Check

Before proceeding to video:
- [ ] Mushroom buildings look the same in Frames 1, 2, 3
- [ ] Tree design matches between Frame 1 and Frame 2
- [ ] Tiny beings in Frame 2 match character reference
- [ ] Tiny figure in Frame 5 matches character reference
- [ ] Boot in Frame 4 matches boot in Frame 5
- [ ] Crack shape matches between Frame 4 and Frame 5
- [ ] Color palette is consistent in all underground frames

**If inconsistency found**: Regenerate that frame with stronger reference emphasis

---

# PHASE 2: VIDEO GENERATION

Use the production frames as start/end inputs.

## Video 1: Hook + Discovery (8 seconds)
**Start**: `prod-04-hook-boot.png`
**End**: `prod-01-city-aerial.png`

```
Dramatic camera movement: starts looking up at giant boot descending, boot
freezes mid-air for one beat, camera rapidly dives downward into crack in
sidewalk, falling through layers of concrete and soil into darkness, speed
increases during descent, warm bioluminescent light appears below, camera
emerges into vast underground cavern, slows as it floats above glowing
miniature city, dust particles throughout, motion blur during descent,
smooth deceleration at end, cinematic, 8 seconds
```

**Style reference** (if model supports): `ref-01-world-style.png`

---

## Video 2: Exploration (10 seconds)
**Start**: `prod-01-city-aerial.png`
**End**: `prod-02-beings-lookup.png`

```
Smooth floating camera exploring magical underground miniature city, camera
glides gently downward from aerial view, passing by glowing mushroom buildings
and crystal spires, descending into streets where tiny humanoid figures walk,
passing close to bioluminescent streetlamp, continuing toward central plaza
with great glowing tree, camera settles at ground level where crowd of tiny
figures looks upward, one figure points up, dreamy floating movement throughout,
particles of light drift upward, 10 seconds
```

**Style reference** (if model supports): `ref-01-world-style.png`

---

## Video 3: Connection (9 seconds)
**Start**: `prod-03-cavern-rise.png`
**End**: `prod-05-wave-final.png`

```
Camera rises upward through vast underground cavern revealing multiple levels
of miniature civilizations on walls, glowing cities and root networks visible
on all sides, ascending toward bright opening above, camera emerges from crack
into daylight, transitions to ground level view of sidewalk crack, tiny figure
at crack edge waves upward, camera slowly pulls back revealing frozen boot in
background and full sidewalk scene, subtle glow hints in other cracks, 9 seconds
```

**Style reference** (if model supports): `ref-01-world-style.png`

---

## Fallback Sub-Shots (If Needed)

If Video 1 is too complex:

**Video 1a** (3s): `prod-04-hook-boot.png` → boot frozen frame
```
Giant boot descends and freezes mid-step, dust suspended, tension, 3 seconds
```

**Video 1b** (2s): crack close-up → `prod-06-dive-transition.png`
```
Camera plunges into dark crack, rapid falling, glow appears below, 2 seconds
```

**Video 1c** (3s): `prod-06-dive-transition.png` → `prod-01-city-aerial.png`
```
Emerge from darkness above glowing city, camera slows, wonder, 3 seconds
```

---

# PHASE 3: FINAL ASSEMBLY

## Text Overlays

| Text | Timing | Position |
|------|--------|----------|
| "Wait—" | 0-2s | Bottom center |
| "They're everywhere. Look closer." | 24-27s | Center (fade in) |

## Audio

**Primary**: "Powerful songs like action movie music" by Tansa
- Search: "Powerful songs action movie Tansa" in TikTok sounds
- 50K videos/day, cinematic feel

**Sync points**:
- 0-2s: Tension build
- 2-3s: Drop/whoosh on dive
- 7-8s: Wonder swell on city reveal
- 24s: Resolution on text

## Export

- 9:16 vertical
- 27 seconds total
- TikTok native format

---

# COMPLETE FILE CHECKLIST

## Reference Files
- [ ] `ref-01-world-style.png`
- [ ] `ref-02-architecture.png`
- [ ] `ref-03-characters.png`
- [ ] `ref-04-surface.png`

## Production Frames
- [ ] `prod-01-city-aerial.png`
- [ ] `prod-02-beings-lookup.png`
- [ ] `prod-03-cavern-rise.png`
- [ ] `prod-04-hook-boot.png`
- [ ] `prod-05-wave-final.png`
- [ ] `prod-06-dive-transition.png` (optional)

## Videos
- [ ] `video-01-hook-discovery.mp4`
- [ ] `video-02-exploration.mp4`
- [ ] `video-03-connection.mp4`

## Final
- [ ] Combined with text overlays
- [ ] Audio added
- [ ] Exported for TikTok

---

# TROUBLESHOOTING

## "Buildings look different between shots"
→ Regenerate inconsistent frame with stronger reference weight
→ Some models: increase "reference strength" parameter

## "Character doesn't match reference"
→ Make character reference more prominent in prompt
→ Try: "exactly matching the character design reference"

## "Boot changed between Shot 1 and Shot 3"
→ Use same surface reference for both
→ Crop reference to show only the boot if needed

## "Colors drift in underground shots"
→ Use style guide as reference for ALL underground frames
→ Explicitly state "cyan and amber palette from reference"

## "Video loses consistency during motion"
→ Use both start AND end frames as inputs
→ Some models: add style reference as third input

---

# VERSION HISTORY

| Version | Key Change |
|---------|------------|
| v1 | Generic tree concept - FAILED |
| v2 | Miniature world redesign |
| v2.1 | Technical fallbacks added |
| v2.2 | **Reference image workflow** for consistency |
