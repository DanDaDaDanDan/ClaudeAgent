# Video Generation Prompts v2.1 - "The Tiny World"

## Changes from v2
- Added explicit fallback sub-shot breakdown for Shot 1
- Added timing flexibility notes
- Clarified model requirements

---

## SHOT 1: "The Threat + Discovery" (8 seconds)

### PRIMARY APPROACH: Single Continuous Shot
**Input**: Start Frame (shoe) + End Frame (city aerial)

```
Dramatic camera movement sequence: starts looking up at giant boot descending,
boot freezes mid-air for one beat, then camera rapidly dives downward into the
crack in the sidewalk, falling through layers of concrete and soil into darkness,
speed increases during descent, suddenly warm bioluminescent light appears below,
camera emerges into vast underground cavern, slowing down as it floats above a
glowing miniature city, dust particles throughout, motion blur during fast descent,
smooth deceleration at end, cinematic, 8 seconds
```

### FALLBACK APPROACH: Three Sub-Shots
*Use this if your model can't handle the complexity*

#### Shot 1a: The Threat (3 seconds)
**Input**: Shoe frame only (or shoe start + shoe stopped end)

```
Giant boot descending from above toward cracked sidewalk, motion blur, boot
slows and freezes mid-step, dust particles suspended in air, tension moment,
extreme low angle looking up, 3 seconds
```

#### Shot 1b: The Dive (2 seconds)
**Input**: Crack close-up start + darkness with glow below end

```
Camera plunges downward into dark crack in concrete, rapid falling motion
through layers of soil and roots, darkness surrounds, warm light begins
glowing from far below, motion blur, speed lines, 2 seconds
```

#### Shot 1c: The Emergence (3 seconds)
**Input**: Dark cavern with light below + city aerial view

```
Camera falls through dark cavern, warm bioluminescent light grows brighter,
suddenly emerges above vast underground miniature city, camera slows,
floating gently, city revealed below with glowing mushroom buildings and
tiny lights, wonder moment, 3 seconds
```

### Timing Flexibility
- If model only produces 6-7 seconds, that's fine
- Can extend Shot 2 or 3 to compensate
- Minimum acceptable: 5 seconds (hook + dive + reveal)

---

## SHOT 2: "The Hidden World" (8-10 seconds)

**Input**: City aerial start + Beings looking up end

```
Smooth floating camera movement exploring a magical underground miniature city,
camera glides gently downward from aerial view, passing by glowing mushroom
buildings and crystal spires, descending into the streets where tiny humanoid
figures walk, passing close to a bioluminescent streetlamp, continuing toward
a central plaza with a great glowing tree, camera settles at ground level where
a crowd of tiny figures has gathered looking upward, one figure points up,
dreamy floating movement throughout, gentle exploration feel, particles of light
drift upward, 10 seconds
```

### Timing Flexibility
- Target: 10 seconds
- Acceptable range: 8-10 seconds
- If model caps at 8s, redistribute 2s to Shot 3

### Simplified Prompt
```
Floating camera descends through glowing underground city, past mushroom
buildings, into streets with tiny figures, arrives at crowd looking up,
one figure points upward, 8-10 seconds
```

---

## SHOT 3: "The Connection" (9-11 seconds)

**Input**: Rising cavern view + Wide sidewalk shot

```
Camera rises upward through a vast underground cavern revealing multiple levels
of miniature civilizations built into the walls, glowing cities and root networks
visible on all sides, ascending toward a bright opening above, camera emerges
from the crack into daylight, transitions to ground level view of sidewalk crack,
a tiny figure stands at the edge of the crack and waves upward, camera slowly
pulls back to reveal the frozen boot in background and full sidewalk scene,
hold on wide shot with subtle glow hints in other cracks, upward movement then
pullback, dramatic scale shift, 9 seconds
```

### FALLBACK: Two Sub-Shots

#### Shot 3a: The Rise (5 seconds)
```
Camera rises through underground cavern, multiple glowing cities visible on
cavern walls, ascending toward bright crack opening above, awe-inspiring
scale, 5 seconds
```

#### Shot 3b: The Wave (4-6 seconds)
```
Ground level view of sidewalk crack, tiny glowing figure at crack edge waves
upward, camera slowly pulls back revealing frozen boot and full sidewalk,
other cracks have subtle glow, 4-6 seconds
```

### Timing Flexibility
- Target: 9 seconds
- Can expand to 11 if Shot 2 was shortened
- The "wave" moment must be at least 2 seconds for impact

---

## TOTAL RUNTIME GUIDE

| Scenario | Shot 1 | Shot 2 | Shot 3 | Total |
|----------|--------|--------|--------|-------|
| Ideal | 8s | 10s | 9s | 27s |
| Minimum | 5s | 8s | 9s | 22s |
| Extended | 8s | 8s | 11s | 27s |

**Acceptable range**: 22-30 seconds (still in viral sweet spot)

---

## MODEL COMPATIBILITY NOTES

### High-End Models (Runway Gen-3, Pika 1.5+, Kling)
- Use primary single-shot approach
- Can handle complex camera movements
- Speed ramping may work

### Mid-Range Models (Older Runway, Pika 1.0)
- Use fallback sub-shot approach for Shot 1
- Simpler camera movements
- Avoid speed ramping

### Entry-Level Models
- Use all fallback approaches
- Keep each sub-shot under 4 seconds
- Prioritize start/end frame alignment over motion complexity

---

## AUDIO SYNC POINTS (Unchanged)

| Timestamp | Beat Moment | Audio Cue |
|-----------|-------------|-----------|
| 0-2s | "Wait—" text | Tension/pause |
| 2-3s | Begin dive | Bass drop/whoosh |
| 7-8s | City reveal | Wonder swell |
| 18s | Camera rises | Building intensity |
| 24s | Text appears | Music resolves |
