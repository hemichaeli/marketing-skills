---
name: website-stitch
version: 1.0.0
description: Build and deploy campaign landing pages and microsites that match campaign brand identity and conversion goals. Creates responsive pages in HTML with Tailwind CSS or React, pushes to GitHub, and deploys via Netlify or Vercel. Triggers on: "build a campaign landing page", "create a microsite", "make a campaign website", "stitch a landing page", "landing page for campaign", or when called from campaign-council stage 5 for web assets. Requires GitHub and Netlify or Vercel connectors.
---

# Website Stitch - Campaign Landing Page Builder

Build and deploy campaign landing pages and microsites that match campaign brand identity and conversion goals.

## What this skill produces

- Single-page campaign landing pages
- Multi-section microsites (hero, features, social proof, CTA, footer)
- Email capture pages with Netlify Forms integration
- Event registration pages
- Product launch pages

## Required information before building

Gather these from BRIEF.md, ART.md, and COPY.md:
- Campaign slug and project name
- Primary conversion goal (email capture / demo request / purchase / registration)
- Headline and sub-headline (from COPY.md)
- Key benefits (3 max, from COPY.md)
- CTA button text and destination URL
- Brand colors in hex (from ART.md)
- Logo file or URL
- Any form fields required (name, email, phone, company)

## How to use

1. Read the campaign files (BRIEF.md, COPY.md, ART.md) for all required inputs.
2. Build the page as a single HTML file (with embedded Tailwind CSS via CDN and vanilla JS) or as a React component for interactive flows.
3. Push to GitHub via the GitHub MCP connector.
4. Deploy via Netlify or Vercel connector. Netlify Forms handles email capture without a backend.
5. Return the deployed URL to the user.

## Tech stack defaults

| Need | Stack |
|---|---|
| Simple landing page | HTML + Tailwind CSS CDN + vanilla JS |
| Interactive form flow | React + Tailwind |
| Email capture | Netlify Forms (attribute `netlify` on the form tag) |
| Deployment | Netlify (default) or Vercel |
| Source control | GitHub |

## Page structure (single-page default)

```
[Hero section]
  - Full-width background (brand color or image)
  - Headline (H1, from COPY.md)
  - Sub-headline (from COPY.md)
  - Primary CTA button

[Benefits section]
  - 3-column grid
  - Icon + benefit title + one-line description per column

[Social proof or product section]
  - Optional: testimonial, screenshot, or feature highlight

[CTA section]
  - Repeat CTA
  - Email capture form if goal is lead gen

[Footer]
  - Logo, copyright, privacy link
```

## Related skills

- **cro**: Apply CRO principles to improve conversion rate
- **copywriting**: Use for headline and CTA copy
- **ab-testing**: Structure a test between page variants after launch

## Output

Deliver: GitHub repo URL, live deployed URL. In Claude Code, also save to `outputs/campaign-council/<slug>/web/index.html`.

## When called from campaign-council

campaign-council calls this skill during stage 5 execution. At that point:
1. Read COPY.md for all text content
2. Read ART.md for visual direction and brand colors
3. Read BRIEF.md for the conversion goal and audience
4. Build and deploy
5. Return the live URL to campaign-council for inclusion in the final asset package
