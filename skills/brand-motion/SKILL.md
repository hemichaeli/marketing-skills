---
name: brand-motion
version: 1.0.0
description: Create brand motion and animation assets for marketing campaigns including animated logo reveals, transition sequences, lower thirds, looping visual elements, and animated GIFs. Uses FFmpeg for composition and can incorporate existing brand assets. Triggers on: "create brand animation", "make a logo reveal", "animated brand element", "lower third", "motion asset for campaign", "animated GIF for email", or when called from campaign-council stage 5 for motion assets.
---

# Brand Motion - Campaign Animation Creator

Create brand motion and animation assets for marketing campaigns using FFmpeg and available media tools.

## What this skill produces

- Animated logo reveals (fade-in, slide-in, scale-up, particle dissolve)
- Lower thirds and title cards for video
- Transition sequences between campaign video segments
- Looping ambient background animations
- Animated GIFs for email and social media
- End cards with CTA text overlay
- Kinetic typography clips (text animating in sync with messaging)

## How to use

1. Get the brand identity from campaign ART.md or PLAN.md: colors (hex), logo file, typography, motif.
2. Determine the motion asset type needed.
3. Source existing brand assets (logo, color palette, font files).
4. Use FFmpeg to compose the animation. For complex multi-layer compositing, reference the ffmpeg-editor skill.
5. Export in the correct format for the intended channel.

## Export formats

| Use case | Format | Notes |
|---|---|---|
| Video insert (ad, reel) | .mp4 H.264 | With alpha if overlay |
| Email and social static | .gif | Max 3MB for email |
| Web animation | .webm | Smaller than MP4 |
| Story/Reel loop | .mp4 | Square or 9:16 |

## Asset naming convention

`<project-slug>-<type>-<version>.<ext>`

Examples:
- `genomax2-logo-reveal-v1.mp4`
- `quantum-lower-third-v2.gif`
- `bold-endcard-cta-v1.mp4`

## Common FFmpeg patterns for brand motion

**Fade-in logo:**
```
ffmpeg -i logo.png -vf "fade=in:0:30,scale=1920:1080:force_original_aspect_ratio=decrease,pad=1920:1080:(ow-iw)/2:(oh-ih)/2" -t 3 logo_reveal.mp4
```

**Looping GIF from video clip:**
```
ffmpeg -i clip.mp4 -vf "fps=15,scale=640:-1:flags=lanczos" -loop 0 output.gif
```

For more complex compositions (layers, masks, keyframes), defer to the ffmpeg-editor skill.

## Output

Deliver the motion asset file(s). In Claude Code, save to `outputs/campaign-council/<slug>/assets/motion/`. In claude.ai, present as a downloadable file link.

## When called from campaign-council

campaign-council calls this skill during stage 5 execution. At that point:
1. Read ART.md for brand colors, motif, and typography
2. Read PLAN.md for the specific motion asset spec
3. Produce the asset(s) listed
4. Return file paths or download links to campaign-council
