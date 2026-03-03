# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static website for the Rubin Alerts & AI Hackathon (April 1–3, 2026, SkAI Institute, Chicago IL). Pure HTML/CSS — no build step, no package manager, no JavaScript framework.

## Structure

- `index.html` — Home page (vision, hackathon goals, important dates)
- `program.html` — Hackathon schedule
- `participants.html` — Participant cards and registration info
- `travel.html` — Travel and lodging (Westin Michigan Ave, Chicago)
- `css/styles.css` — Single stylesheet with all CSS custom properties
- `assets/images/` — Site images

## Deployment

GitHub Pages from `main` branch at `https://rubinalerts26.github.io/`. No Jekyll; push to main to deploy.

To preview locally:
```
python3 -m http.server 8000
```

## Common Content Updates

**Add a participant** (`participants.html`):
```html
<div class="participant-card">
    <div class="participant-avatar">AB</div>
    <h4>Full Name</h4>
    <p class="participant-affiliation">Institution</p>
</div>
```

**Add a schedule row** (`program.html`):
```html
<tr>
    <td class="schedule-time">09:00 - 10:00</td>
    <td>Session Title</td>
    <td class="schedule-speaker">Speaker Name</td>
</tr>
```
Use `class="schedule-break"` on `<tr>` for breaks, with `colspan="2"` on the content cell.

**Add an important date** (`index.html`):
```html
<div class="date-item">
    <div class="date-badge">
        <span class="month">Apr</span>
        <span class="day">1</span>
    </div>
    <div class="date-content">
        <h4>Event Title</h4>
        <p>Description.</p>
    </div>
</div>
```

## Design Constraints

- No white backgrounds — all sections use blue tints
- Colors are CSS custom properties in `css/styles.css` under `:root`; always use variables (e.g. `var(--color-accent)`) rather than hardcoded hex values
- Navigation links use class `jiggle-link` for hover animation
- Color palette is derived from SkAI Institute branding (blues `#0a1628`–`#90cdf4`, purple accent `#8b5cf6`)
- Hero background uses the Vera C. Rubin telescope image (external URL in `.hero` CSS) with a semi-transparent gradient overlay for text legibility
- Contact email throughout: `rubinalerts@lists.skai-institute.org`
