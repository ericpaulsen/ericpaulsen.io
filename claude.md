# Claude.md - Project Context for AI Agents

## Project Overview

Personal website for Eric Paulsen - a multi-page static site showcasing technical leadership, fractional CTO services, media appearances, and projects.

**Live URL:** https://ericpaulsen.io  
**Hosting:** Vercel (project name: `ericpaulsen.io`)  
**Repository:** This is the `v2-multipage` branch

## Tech Stack

- **Pure HTML/CSS** - No frameworks, no build step
- **Static hosting** on Vercel
- **Formspree** for contact form handling (CTO inquiry page)
- **Google Analytics** (ID: `G-CFDST09EG9`)

## File Structure

```
├── claude.md           # This file
├── vercel.json         # Vercel configuration
├── firebase.json       # Legacy (can be removed)
└── public/
    ├── index.html      # Homepage
    ├── about.html      # About Me page
    ├── media.html      # Media appearances (podcasts, articles, speaking)
    ├── projects.html   # Technical projects
    ├── cto.html        # Fractional CTO inquiry form
    ├── 404.html        # Custom error page
    ├── main.css        # All styles (design system)
    └── favicon.png     # Site favicon
```

## Design System

### Colors (CSS Variables in `main.css`)
- `--bg-primary: #282c34` - Main background (dark charcoal)
- `--bg-secondary: #1e2128` - Card backgrounds
- `--text-primary: #FFFFFF` - Main text
- `--text-secondary: #a8adb8` - Muted text
- `--accent: #61dafb` - Accent color (cyan)
- `--border-color: #3d4350` - Borders

### Typography
- **Font:** IBM Plex Mono (Google Fonts)
- All sizing uses CSS custom properties (`--font-size-sm`, `--font-size-base`, etc.)

### Icons
- **Font Awesome** (kit ID: `17ce3b44e2`)
- **Bootstrap Icons** (CDN)

## Navigation Order

```
Home | About | Media | Projects | Fractional CTO
```

All pages share the same navigation component. When adding/modifying nav, update ALL HTML files.

## Deployment

### Deploy to Vercel
```bash
cd /Users/ericpaulsen/.cursor/worktrees/ericpaulsen.io/yae
NODE_TLS_REJECT_UNAUTHORIZED=0 vercel --prod --yes
```

Note: The `NODE_TLS_REJECT_UNAUTHORIZED=0` is needed due to local TLS certificate issues.

### Local Testing
```bash
cd public
python3 -m http.server 8000
# Open http://localhost:8000
```

## Safari Compatibility Notes

Safari has specific CSS quirks that required workarounds:
- Use `top/left/right/bottom: 0` instead of `inset: 0`
- Use `grid-gap` alongside `gap` for older Safari
- Dashed borders on narrow elements use `repeating-linear-gradient` instead
- Add `-webkit-transform` prefixes for transforms

## External Services

### Formspree (Contact Form)
- Form ID: `xnjjjdnj`
- Endpoint: `https://formspree.io/f/xnjjjdnj`
- Used on: `cto.html`

### Social Links
- X (Twitter): https://x.com/ericpaulsenio
- GitHub: https://github.com/ericpaulsen
- Substack: https://substack.com/@ericpaulsen
- Email: hello@ericpaulsen.io

## Key Context

- Eric is Field CTO at Coder (coder.com)
- Previously founding Sales Engineer at Coder
- Focus areas: AI adoption, developer platforms, cloud infrastructure
- Target sectors: Financial Services, Cybersecurity, Semiconductor, AI, Public Sector
- Technologies: Kubernetes, Docker, Terraform, Linux, Python, AWS Bedrock

## Common Tasks

### Adding a new page
1. Create new HTML file in `public/`
2. Copy navigation structure from existing page
3. Update nav in ALL other HTML files
4. Add page-specific styles to `main.css`
5. Deploy with `vercel --prod`

### Adding media items
Edit `public/media.html` - follow the existing card structure with:
- `data-type` attribute for filtering (podcast/article/speaking/webinar)
- Appropriate thumbnail class (`media-thumbnail-speaking`, etc.)
- Tags in the `.tags` container

### Updating styles
All styles are in `public/main.css` - uses CSS custom properties for consistency.

