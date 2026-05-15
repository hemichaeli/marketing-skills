---
name: video-higgsfield
version: 1.0.0
description: Generate short cinematic marketing videos via the Higgsfield MCP server using Seedance 2.0. Produces 3-9 second clips for campaigns, social content, and product showcases, optionally using a reference image as the first frame for brand consistency. Triggers on: "generate a campaign video", "make a marketing video with Higgsfield", "Seedance clip", "first-frame video from this image", "video asset for campaign", or when called from campaign-council stage 5 for video assets. Requires the Higgsfield MCP server to be connected.
---

# Video Higgsfield - Campaign Video Generator

Generate short cinematic marketing videos via the connected Higgsfield MCP server using Seedance 2.0.

## Model

`seedance_2_0` - default for all marketing campaign videos. Strong motion fidelity, reference-driven identity preservation.

## How to use

1. Get the visual direction from campaign ART.md or from the user.
2. Compose a concise motion prompt following the structure below.
3. Call `generate_video` via the Higgsfield MCP with model `seedance_2_0`.
4. Optionally provide a reference image as the starting frame.

## Prompt structure

Describe in this order: subject and action, camera movement, lighting and mood, style reference.

Example: "Premium skincare bottle slowly rotating on a marble surface. Smooth dolly-in shot. Warm studio lighting with soft shadows. Luxury editorial product video."

Example: "Young professional opens a laptop in a modern co-working space. Handheld medium shot, natural light. Energetic morning atmosphere. Authentic lifestyle documentary style."

## Parameters

- **Duration**: 3-9 seconds. Use 3-5s for ads, 6-9s for showcase clips.
- **Aspect ratio**: 16:9 for YouTube and LinkedIn, 9:16 for Reels and TikTok and Stories, 1:1 for feed
- **Start image**: pass as `medias` with role `start_image` for first-frame consistency

## Output

Present the generated video in chat via the Higgsfield MCP widget. In Claude Code, save to `outputs/campaign-council/<slug>/assets/videos/`.

## When called from campaign-council

campaign-council calls this skill during stage 5 execution. At that point:
1. Read ART.md for visual direction and brand motif
2. Read PLAN.md for the specific video asset spec (channel, duration, message)
3. Generate the video(s) listed in PLAN.md
4. Return the result URL or file path to campaign-council
