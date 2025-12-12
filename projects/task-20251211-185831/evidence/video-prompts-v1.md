# Video Generation Prompts - "Nature's Awakening"

## Model Requirements
- Image-to-video model with start frame (required) and optional end frame
- Maximum 10 seconds per shot
- Target: 9 seconds per shot for 27-second total

---

## SHOT 1: "The Frozen World"
**Duration**: 9 seconds
**Input**: Start frame + End frame (recommended)

### Video Prompt

```
Slow cinematic push-in toward the frozen tree, gentle atmospheric movement,
light snow particles drifting slowly through the air, subtle mist swirling
at ground level, completely still tree branches with occasional tiny ice
sparkle, overcast clouds moving slowly overhead, at the end a small warm
golden light begins to glow at the base of the tree, magical awakening
beginning, smooth slow camera movement, ethereal atmosphere, 9 seconds
```

### Motion Specifications
| Element | Motion Type | Speed | Direction |
|---------|-------------|-------|-----------|
| Camera | Slow push/dolly | Very slow | Forward toward tree |
| Snow particles | Drift | Gentle | Diagonal down |
| Mist | Swirl | Subtle | Low to ground |
| Tree | Static | None | N/A |
| End glow | Fade in | Gradual | At tree base (frame 7-9 sec) |

### Technical Notes
- Keep tree completely still until the glow appears
- Snow movement should be barely perceptible
- Camera movement should be extremely smooth
- The golden glow at the end is the transition hook to Shot 2

---

## SHOT 2: "The Awakening"
**Duration**: 9 seconds
**Input**: Start frame + End frame (recommended)

### Video Prompt

```
Magical transformation sequence, golden-pink energy flowing upward through
the tree bark like glowing veins, frost visibly melting and dripping from
branches, buds rapidly swelling and emerging along the branches, first
flowers beginning to bloom open revealing luminescent petals, small particles
of light rising upward from the flowers, organic growing motion, magical
energy pulsing, medium close-up shot, static camera with subtle movement,
wonder and magic, 9 seconds
```

### Motion Specifications
| Element | Motion Type | Speed | Direction |
|---------|-------------|-------|-----------|
| Energy flow | Pulse/flow | Medium | Upward through bark |
| Frost | Melt/drip | Gradual | Downward drips |
| Buds | Swell/emerge | Progressive | Outward from branches |
| Flowers | Bloom open | Graceful | Petals unfurling outward |
| Light particles | Float | Gentle | Upward rising |
| Camera | Static/subtle | Minimal | Slight drift only |

### Technical Notes
- Motion should feel organic, like time-lapse nature footage
- Energy flow should look like bioluminescence
- Flowers bloom in sequence (bottom to top creates nice flow)
- Particles increase in density toward end of shot

---

## SHOT 3: "Full Bloom"
**Duration**: 9 seconds
**Input**: Start frame + End frame (recommended)

### Video Prompt

```
Spectacular magical bloom explosion, flowers rapidly opening across the
entire tree in waves, the landscape visibly transforming as green grass
pushes up through melting snow, other plants sprouting and blooming around
the tree, dozens of glowing butterflies taking flight and floating through
the scene, countless flower petals and light particles drifting through
the air, warm golden sunlight rays streaming down, camera slowly pulling
back to reveal the full magical garden, triumphant beautiful finale,
maximum wonder and magic, 9 seconds
```

### Motion Specifications
| Element | Motion Type | Speed | Direction |
|---------|-------------|-------|-----------|
| Flowers | Bloom waves | Fast then settling | Outward from tree center |
| Grass | Push up/grow | Medium | Upward through snow |
| Snow | Melt away | Quick | Receding outward |
| Butterflies | Flutter/float | Gentle varied | Various, upward bias |
| Petals | Drift/float | Gentle | Various, floating |
| Light particles | Float/sparkle | Gentle | Upward and outward |
| Light rays | Subtle movement | Slow | Downward from sky |
| Camera | Slow pull back | Gradual | Backward to reveal scene |

### Technical Notes
- This is the payoff shot - maximum visual interest
- Bloom should feel like an explosion of life
- Butterflies should have varied, natural flight paths
- Camera pull-back reveals the full transformation for maximum impact
- Final frame should be the most beautiful composition

---

## Transition Guidance

### Shot 1 → Shot 2
- Cut when the golden glow appears at tree base
- Shot 2 starts with that glow already visible and expanding

### Shot 2 → Shot 3
- Cut when first flowers are blooming
- Shot 3 starts mid-bloom and expands to full transformation

---

## Alternative Prompt Formats

Some image-to-video models prefer different structures. Here are alternatives:

### Simplified Format (if model prefers brief prompts)

**Shot 1**: `slow push toward frozen tree, drifting snow, golden glow appears at base`

**Shot 2**: `magical energy flows up tree, frost melts, buds grow, flowers begin blooming`

**Shot 3**: `explosive bloom across tree, landscape transforms green, butterflies fly, camera pulls back`

### Motion-Focused Format (if model needs explicit motion keywords)

**Shot 1**: `camera: slow push-in | elements: snow falling, mist swirling | action: light appearing`

**Shot 2**: `camera: static | elements: energy flowing up, ice melting down | action: flowers blooming`

**Shot 3**: `camera: slow pull-back | elements: particles floating, butterflies flying | action: full transformation`
