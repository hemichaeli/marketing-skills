---
name: image-nanobanana
version: 1.0.0
description: Generate campaign images via the Higgsfield MCP server using nano_banana_2 or nano_banana models. Produces photorealistic stills, product shots, branded visuals, and social media imagery. Optionally uses a reference image for brand or character consistency. Triggers on: "generate a campaign image", "make a marketing visual", "product shot for campaign", "brand image via Higgsfield", "nano banana image", or when called from campaign-council stage 5 for image assets. Requires the Higgsfield MCP server to be connected.
---

# Image Nanobanana - Campaign Image Generator

Generate photorealistic and branded images for marketing campaigns via the connected Higgsfield MCP server.

## Models

- `nano_banana_2` - high quality, 4K, best for hero images and product shots
- `nano_banana` - faster, good for social media and supporting visuals

## How to use

1. Get the visual direction from campaign ART.md or from the user directly (brand colors, motif, mood).
2. Compose a detailed prompt that matches the campaign visual direction.
3. Call `generate_image` via the Higgsfield MCP with the appropriate model and parameters.
4. If a reference image is provided for brand or character consistency, pass it as `medias` with role `image`.

## Prompt structure

Describe in this order: subject and composition, background and setting, lighting, mood and style, brand color callouts.

Example: "Premium supplement bottle centered on a clean white marble surface, soft studio lighting from the left, minimal shadows, clinical yet warm, brand blue accents in label, 4K product photography style."

## Aspect ratios

Match the campaign channel:
- 1:1 for Instagram feed, Facebook feed
- 16:9 for LinkedIn, YouTube thumbnail, email header
- 9:16 for Instagram Stories, Reels, TikTok
- 4:5 for Instagram portrait feed

## Output

Present the generated image in chat via the Higgsfield MCP widget. In Claude Code, also save to `outputs/campaign-council/<slug>/assets/images/`.

## When called from campaign-council

campaign-council calls this skill during stage 5 execution. At that point:
1. Read ART.md for visual direction
2. Read COPY.md for messaging context
3. Generate the image(s) listed in PLAN.md asset list
4. Return URLs or file paths to campaign-council for the final asset package
