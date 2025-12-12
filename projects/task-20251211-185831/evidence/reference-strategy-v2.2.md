# Reference Image Strategy v2.2

## The Problem with v2.1

v2.1 prompts were standalone - each image generated independently. This causes:
- Inconsistent mushroom building style between shots
- Tiny beings look different in each frame
- Underground color palette drifts
- Tree design changes shot to shot
- Boot/shoe looks different between Shot 1 and Shot 3

**Solution**: Generate reference art FIRST, then use as input for all production frames.

---

## Reference Image Categories

We need 4 types of reference images:

| Reference Type | Purpose | Used In |
|----------------|---------|---------|
| **World Style Guide** | Establishes underground aesthetic | All underground shots |
| **Architecture Reference** | Mushroom buildings, crystal spires | Shots 1-end, 2, 3-start |
| **Character Reference** | Tiny beings design | Shots 2, 3-end |
| **Surface Reference** | Boot, sidewalk, crack | Shots 1-start, 3-end |

---

## PHASE 0: Generate Reference Art

### Reference 1: World Style Guide

**Purpose**: Establish the overall visual language of the underground world

```
Fantasy underground world style guide reference sheet, showing color palette
swatches and lighting examples, bioluminescent cyan and warm amber color scheme,
magical glow effects demonstration, atmosphere and fog examples, crystal light
refraction, root textures with golden veins, multiple small example vignettes
showing the aesthetic, dark cavern background with glowing elements, reference
sheet layout, concept art style, vertical composition 9:16, 8k detailed
```

**What to extract**: Color values, glow intensity, atmosphere density

---

### Reference 2: Architecture Sheet

**Purpose**: Lock down building designs for consistency

```
Fantasy miniature architecture reference sheet, multiple views of mushroom cap
buildings with carved windows and doors in the stems, crystalline tower designs
that glow from within, structures made from acorn shells and seed pods, grass
bridge construction details, central great tree with glowing root veins in bark,
showing front view side view and detail callouts, warm amber and cyan bioluminescent
lighting, fantasy concept art style, reference sheet layout with multiple examples,
vertical composition 9:16, 8k detailed
```

**What to extract**: Mushroom building proportions, window style, crystal shape, tree trunk pattern

---

### Reference 3: Character Design Sheet

**Purpose**: Consistent tiny being design across all shots

```
Tiny humanoid creature character design reference sheet, small fairy-like being
approximately 1cm tall relative to human scale, ambiguous but intelligent features,
slightly larger eyes than human proportions, wearing clothing made from woven
leaves and grass fibers, showing front view back view side view and detail callouts,
neutral pose and waving pose, subtle golden glow aura around the figure, fantasy
realism style not cartoon, muted earth tone clothing with slight magical shimmer,
character turnaround sheet layout, vertical composition 9:16, 8k detailed
```

**What to extract**: Body proportions, face style, clothing details, glow intensity

---

### Reference 4: Surface World Elements

**Purpose**: Consistent boot and sidewalk across surface shots

```
Realistic reference sheet for street photography elements, worn brown leather
work boot from multiple angles showing scuff marks and weathering, cracked grey
concrete sidewalk texture with prominent dark crevice, harsh daylight shadow
examples, dust particle reference, mundane urban realism, photographic reference
style, showing boot from below angle and side angle, crack detail close-up,
reference sheet layout, vertical composition 9:16, 8k photorealistic
```

**What to extract**: Boot color/wear pattern, crack shape, concrete texture

---

## PHASE 1: Generate Production Frames (Using References)

### Updated Prompt Format

Each production prompt now includes reference inputs:

```
[PROMPT TEXT]

REFERENCE INPUTS:
- Style: [World Style Guide image]
- Architecture: [Architecture Sheet image]
- Characters: [Character Design Sheet image] (if beings visible)
- Surface: [Surface World Elements image] (if surface visible)
```

---

## Updated Production Prompts

### Shot 1 Start: The Hook

```
Extreme low angle photograph looking straight up from ground level at a giant
worn leather boot descending from above, the boot fills the upper 60% of the
frame with dramatic foreshortening, motion blur on the boot suggesting downward
movement, below the boot is cracked grey concrete sidewalk with a prominent
dark crack/crevice in the center, dust particles visible in the harsh sunlight,
hyperrealistic street photography style, threatening perspective, tension,
vertical composition 9:16, photorealistic, 8k detail, dramatic shadows,
the boot is about to step down

REFERENCE INPUTS:
- Surface: [Surface World Elements] - match boot design and crack shape exactly
```

---

### Shot 1 End: City Discovery

```
Aerial view looking down at a breathtaking miniature fantasy city built inside
an underground cavern, mushroom cap buildings with carved windows in stems,
crystalline spires glowing from within, structures from natural materials,
streets lit by bioluminescent plants in cyan and amber, tiny silhouetted
figures visible on streets below, cavern ceiling with hanging roots, magical
atmosphere, tilt-shift photography effect, vertical composition 9:16, 8k

REFERENCE INPUTS:
- Style: [World Style Guide] - match color palette and glow intensity
- Architecture: [Architecture Sheet] - match building designs exactly
```

---

### Shot 2 Start: City Aerial

```
Sweeping aerial view of fantastical miniature underground city, mushroom cap
buildings with windows carved into stems matching reference design, crystalline
towers glowing from within, woven grass bridge walkways, central plaza with
great tree whose roots glow with golden veins, tiny humanoid figures walking
bioluminescent streets, organic magical architecture, warm amber streetlights
from glowing flowers, cyan crystal accents, atmospheric fog, vertical 9:16, 8k

REFERENCE INPUTS:
- Style: [World Style Guide] - match atmosphere and lighting
- Architecture: [Architecture Sheet] - match all building designs
- Characters: [Character Design Sheet] - match figure proportions (silhouettes ok)
```

---

### Shot 2 End: Beings Looking Up

```
Ground level inside miniature underground city at base of great central tree,
crowd of tiny humanoid figures gathered looking upward toward cavern ceiling,
faces lit by ambient bioluminescent glow, one figure in foreground points
upward with arm raised, figures wear leaf and grass clothing matching reference,
great tree trunk pulses with golden light veins matching reference design,
wonder and concern on faces, dramatic upward perspective, vertical 9:16, 8k

REFERENCE INPUTS:
- Style: [World Style Guide] - match lighting and color palette
- Architecture: [Architecture Sheet] - match tree design exactly
- Characters: [Character Design Sheet] - match figure design, clothing, proportions
```

---

### Shot 3 Start: Rising Through Cavern

```
Vertical view looking up through underground cavern toward bright opening above,
rising perspective, cavern walls show multiple civilization levels with cities
built into walls matching reference architecture, glowing root networks connecting
settlements, bridges spanning void, tiny window lights, crack of surface light
above, vast scale, multiple miniature cities at different levels, bioluminescent
plants and crystals matching reference colors, vertical 9:16, 8k

REFERENCE INPUTS:
- Style: [World Style Guide] - match color palette throughout
- Architecture: [Architecture Sheet] - match building styles at all levels
```

---

### Shot 3 End: The Wave

```
Ground level photograph of cracked concrete sidewalk in daylight, prominent
crack in center matching reference crack shape, tiny humanoid figure at crack
edge matching character reference design with subtle golden glow aura, figure
waves upward enthusiastically, worn boot in background matching reference boot
design frozen mid-step, harsh daylight, mundane surface contrasted with magical
tiny figure, other cracks hint at faint glow, vertical 9:16, 8k photorealistic

REFERENCE INPUTS:
- Surface: [Surface World Elements] - match boot and crack exactly
- Characters: [Character Design Sheet] - match figure design with glow effect
- Style: [World Style Guide] - match glow color for figure aura
```

---

## Video Generation with References

### How to Use References for Video

Most image-to-video models accept:
1. **Start frame** (required)
2. **End frame** (optional but recommended)
3. **Style reference** (some models)

**Strategy**:
- Start and end frames are already generated with consistent references
- The video model interpolates between them
- Consistency is inherited from the frames

### If Model Supports Style Reference

```
Video prompt: [motion description]

INPUTS:
- Start frame: [Production Shot X Start]
- End frame: [Production Shot X End]
- Style reference: [World Style Guide] (if supported)
```

---

## Complete Generation Order

### Phase 0: References (Generate First)
1. World Style Guide
2. Architecture Sheet
3. Character Design Sheet
4. Surface World Elements

### Phase 1: Production Frames (Use References)
5. Shot 1 End (city) - uses Style + Architecture
6. Shot 2 Start (city aerial) - uses Style + Architecture + Characters
7. Shot 2 End (beings) - uses Style + Architecture + Characters
8. Shot 3 Start (cavern) - uses Style + Architecture
9. Shot 1 Start (boot) - uses Surface
10. Shot 3 End (wave) - uses Surface + Characters + Style

### Phase 2: Videos (Use Production Frames)
11. Video 1: Frame 9 → Frame 5
12. Video 2: Frame 6 → Frame 7
13. Video 3: Frame 8 → Frame 10

---

## Consistency Checklist

Before moving to production frames:
- [ ] World Style Guide establishes clear color palette
- [ ] Architecture Sheet has recognizable mushroom building design
- [ ] Character Design Sheet has clear proportions and glow effect
- [ ] Surface Reference has distinctive boot and crack

Before moving to videos:
- [ ] All production frames use consistent references
- [ ] Mushroom buildings look the same across shots
- [ ] Tiny beings have consistent design
- [ ] Boot matches between Shot 1 and Shot 3
- [ ] Color palette is consistent underground
