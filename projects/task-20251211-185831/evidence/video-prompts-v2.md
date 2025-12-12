# Video Generation Prompts v2 - "The Tiny World"

## Overview
| Shot | Duration | Motion Type | Complexity |
|------|----------|-------------|------------|
| 1 | 8 sec | Dramatic dive | High |
| 2 | 10 sec | Floating explore | Medium |
| 3 | 9 sec | Rise + pull back | Medium |

---

## SHOT 1: "The Threat + Discovery" (8 seconds)
**Input**: Start Frame (shoe above) + End Frame (city aerial)

### Video Prompt - Standard Format

```
Dramatic camera movement sequence: starts looking up at giant boot descending,
boot freezes mid-air for one beat, then camera rapidly dives downward into the
crack in the sidewalk, falling through layers of concrete and soil into darkness,
speed increases during descent, suddenly warm bioluminescent light appears below,
camera emerges into vast underground cavern, slowing down as it floats above a
glowing miniature city, dust particles throughout, motion blur during fast descent,
smooth deceleration at end, cinematic, 8 seconds
```

### Motion Breakdown
| Timestamp | Camera Action | Speed | Notes |
|-----------|---------------|-------|-------|
| 0-1s | Static, looking up at shoe | None | Tension build |
| 1-2s | Shoe descends, stops | Slow→stop | The "Wait" moment |
| 2-3s | Hold, then begin descent | Pause→accelerate | Pivot moment |
| 3-5s | Rapid dive into crack | Fast | Motion blur, darkness |
| 5-7s | Fall through cavern | Fast→medium | Light appears |
| 7-8s | Emerge above city | Slow | Wonder reveal |

### Motion Specifications Table
| Element | Motion | Direction | Speed |
|---------|--------|-----------|-------|
| Camera | Tilt down→dive→float | Down, down, down→settle | Variable |
| Boot | Descend→freeze | Downward | Slow→stop |
| Dust particles | Fall | Down | Slow |
| Underground lights | Reveal | Appearing from below | Gradual |

### Simplified Prompt (If Needed)
```
Camera looks up at boot, boot stops, camera dives into crack, falls through darkness, emerges above glowing underground city, 8 seconds
```

---

## SHOT 2: "The Hidden World" (10 seconds)
**Input**: Start Frame (city aerial) + End Frame (beings looking up)

### Video Prompt - Standard Format

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

### Motion Breakdown
| Timestamp | Camera Action | Speed | Focus |
|-----------|---------------|-------|-------|
| 0-3s | Aerial glide downward | Slow | City overview |
| 3-5s | Pass mushroom buildings | Medium | Architecture |
| 5-7s | Enter street level | Medium | Life details |
| 7-9s | Approach central tree | Slow | Tree + crowd |
| 9-10s | Settle at crowd level | Slowing | Beings looking up |

### Motion Specifications Table
| Element | Motion | Direction | Speed |
|---------|--------|-----------|-------|
| Camera | Float/glide | Down + forward | Gentle |
| Light particles | Drift | Upward | Very slow |
| Tiny figures | Walking | Various | Natural |
| Bioluminescent glow | Pulse | Stationary | Subtle rhythm |
| Final crowd | Looking up | Stationary→one points | Dramatic |

### Simplified Prompt (If Needed)
```
Floating camera descends through glowing underground city, past mushroom buildings, into streets with tiny figures, arrives at crowd looking up, 10 seconds
```

---

## SHOT 3: "The Connection" (9 seconds)
**Input**: Start Frame (rising through cavern) + End Frame (wide shot)

### Video Prompt - Standard Format

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

### Motion Breakdown
| Timestamp | Camera Action | Speed | Focus |
|-----------|---------------|-------|-------|
| 0-3s | Rise through cavern | Medium | Multiple city levels |
| 3-5s | Approach surface | Accelerating | Light from above |
| 5-6s | Emerge from crack | Transition | Scale shift moment |
| 6-8s | Ground level, see wave | Settling | Tiny figure waves |
| 8-9s | Pull back to wide | Slow | Full scene reveal |

### Motion Specifications Table
| Element | Motion | Direction | Speed |
|---------|--------|-----------|-------|
| Camera | Rise→emerge→pull back | Up→level→back | Variable |
| Cavern cities | Passing by | Relative downward | Medium |
| Light above | Brightening | Stationary | Gradual |
| Tiny figure | Wave gesture | Arm up and down | Natural |
| Boot (background) | Static | None | Frozen |
| Other crack glows | Fade in | Stationary | Very subtle |

### Simplified Prompt (If Needed)
```
Camera rises through cavern past glowing cities, emerges from crack, tiny figure waves, camera pulls back to show full sidewalk scene, 9 seconds
```

---

## Technical Recommendations

### For Best Results

**Shot 1 (Most Complex)**:
- May need to be done in two parts: (1) shoe + dive into crack, (2) emerge above city
- The speed ramp is challenging - some models may not handle variable speed well
- Alternative: Use a consistent "falling" speed throughout

**Shot 2 (Medium Complexity)**:
- Floating camera is well-suited to most image-to-video models
- The "one figure points up" moment at the end needs clear framing in end image
- Gentle motion throughout - avoid abrupt changes

**Shot 3 (Medium Complexity)**:
- The scale shift from underground to surface is the challenge
- May benefit from a midpoint frame showing the transition
- The "wave" should be subtle but visible

### Fallback Options

If continuous shots are too complex, break into sub-shots:

**Shot 1 Alternative** (3 parts):
- 1a: Shoe descending and stopping (3s)
- 1b: Diving into crack (2s)
- 1c: Emerging above city (3s)

**Shot 3 Alternative** (2 parts):
- 3a: Rising through cavern (5s)
- 3b: Surface scene with wave and pullback (4s)

---

## Audio Sync Points

For editors adding music afterward:

| Timestamp | Beat Moment | Audio Cue |
|-----------|-------------|-----------|
| 0-2s | "Wait—" text | Tension/pause in music |
| 2-3s | Begin dive | Bass drop or whoosh |
| 7-8s | City reveal | Swelling strings/wonder sound |
| 18s | Camera rises | Building intensity |
| 24s | "They're everywhere" text | Music resolves |
| 27s | End | Final beat/silence |

**Recommended Sound**: "Powerful songs like action movie music" by Tansa
- Cinematic feel matches the epic scale shift
- Build-up structure works with the reveal
- Currently trending (50K videos/day)
