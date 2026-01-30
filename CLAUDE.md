# CLAUDE.md - AI Assistant Guide for free-numata

## Project Overview

This is a **marketing landing page** for "個別指導塾 free" (Individual Tutoring free), a tutoring school located in Numata City, Gunma Prefecture, Japan. The site showcases the school's services, pricing, and unique value propositions to attract students and parents.

**Business Focus:**
- One-on-two individual tutoring with professional instructors (no student tutors)
- Unlimited self-study space access for enrolled students
- Unique "tuition freeze" policy - prices locked at enrollment rate until graduation
- English proficiency exam (Eiken) preparation from Grade 5 to Pre-1
- Target audience: Elementary, middle, and high school students

## Tech Stack

| Category | Technology |
|----------|------------|
| **Markup** | HTML5 (semantic elements) |
| **Styling** | CSS3 (custom properties, flexbox, grid, animations) |
| **JavaScript** | Vanilla JS (no frameworks) |
| **Fonts** | Google Fonts (Noto Sans JP, Roboto) |
| **External Services** | Google Maps Embed, LINE Official Account |

**No build tools, package managers, or transpilation required.** Files can be edited directly and deployed as-is.

## File Structure

```
free-numata/
├── index.html     # Main HTML file (485 lines) - all content and inline JS
├── styles.css     # Complete stylesheet (472 lines) - all styling
└── CLAUDE.md      # This file
```

## Key Architecture Decisions

### Single-File Approach
- All HTML content is in `index.html`
- All CSS is in `styles.css`
- JavaScript is embedded at the bottom of `index.html`
- No external JS dependencies or CSS frameworks

### Mobile-First Responsive Design
- Base styles target mobile devices
- Single breakpoint at `768px` for desktop enhancements
- Mobile bottom CTA bar hidden on desktop

### CSS Custom Properties (Variables)
Located at `:root` in `styles.css:2-32`:
```css
--primary: #0ea5e9;       /* Sky Blue - main brand color */
--primary-dark: #0284c7;  /* Darker blue for hover states */
--line-color: #06C755;    /* LINE brand green for CTAs */
--text-main: #1e293b;     /* Dark slate for body text */
--text-sub: #64748b;      /* Muted text */
```

## Code Conventions

### HTML
- **Language**: Japanese (`<html lang="ja">`)
- **Semantic Elements**: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
- **ID-based Navigation**: Sections have IDs for smooth scroll anchoring (`#features`, `#tuition-rule`, `#flow`, `#course`, `#faq`)
- **JS Hooks**: Prefixed with `js-` (e.g., `js-hamburger`, `js-mobile-menu`, `js-header`)

### CSS
- **Naming**: Kebab-case for classes (e.g., `btn-primary`, `section-header`)
- **State Classes**: `active`, `visible`, `highlight`, `open`
- **Animation Classes**: `fade-up`, `fade-in`, `stagger-item`, `stagger-trigger`
- **Utility Classes**: `delay-1`, `delay-2`, `delay-3` for staggered animations

### JavaScript
- **Pattern**: Event delegation with `DOMContentLoaded`
- **State Management**: CSS class toggling (no inline styles)
- **Scroll Animations**: IntersectionObserver API with `rootMargin: '0px 0px -100px 0px'`
- **Stagger Effect**: Items animate sequentially with 100ms delays

## Section Reference

| Section ID | Purpose | Lines (HTML) |
|------------|---------|--------------|
| (hero) | Landing area with main CTA | 57-79 |
| `#features` | 6 feature cards in bento grid | 81-132 |
| `#tuition-rule` | Price protection policy explanation | 134-235 |
| `#flow` | 3-step enrollment process | 237-267 |
| `#course` | Pricing tables for 2 course types | 269-353 |
| `#faq` | 6 expandable Q&A items | 355-388 |
| (access) | Location, hours, Google Map | 390-407 |

## Important Business Information

### Contact Method
- Primary: LINE Official Account - `https://lin.ee/gJxUEir`
- No phone or email form - all inquiries through LINE

### Location
```
〒378-0056
群馬県沼田市高橋場町2215-10
Hours: 平日・土・祝日 16:00 - 22:00
```

### Pricing Structure (Course A - Full Support)
| Grade | Weekly 1 | Weekly 2 | Weekly 3 |
|-------|----------|----------|----------|
| Elementary | ¥14,000 | ¥23,000 | ¥32,000 |
| Middle | ¥16,000 | ¥26,000 | ¥36,000 |
| High | ¥18,000 | ¥30,000 | ¥42,000 |

### Pricing Structure (Course B - Standard)
| Grade | Weekly 1 | Weekly 2 | Weekly 3 |
|-------|----------|----------|----------|
| Elementary | ¥10,000 | ¥20,000 | ¥30,000 |
| Middle | ¥12,000 | ¥23,000 | ¥34,000 |
| High | ¥14,000 | ¥27,000 | ¥40,000 |

### Additional Fees
- Enrollment: ¥10,000
- Facility fee: ¥10,000 (first year only)
- Materials: ~¥1,500 per subject

## Development Workflow

### Local Development
```bash
# No build required - simply open in browser
open index.html
# Or use any local server
python -m http.server 8000
npx serve .
```

### Making Changes
1. Edit `index.html` for content/structure changes
2. Edit `styles.css` for styling changes
3. Refresh browser to see changes
4. Commit and push when ready

### Testing Checklist
- [ ] Mobile view (< 768px) - check hamburger menu, bottom CTA bar
- [ ] Desktop view (>= 768px) - check navigation, pricing cards side-by-side
- [ ] Scroll animations trigger correctly
- [ ] All section anchor links work
- [ ] LINE links open correctly
- [ ] Google Map loads

## Common Modification Tasks

### Adding a New Feature Card
Location: `index.html:87-130` (inside `.bento-grid`)
```html
<div class="bento-item stagger-item">
    <div class="icon-box">🆕</div>
    <div class="bento-content">
        <h4>Feature Title</h4>
        <p>Feature description text.</p>
    </div>
</div>
```

### Adding a New FAQ Item
Location: `index.html:361-386` (inside `.faq-grid`)
```html
<details class="faq-details stagger-item">
    <summary>Question text? <span class="icon">+</span></summary>
    <div class="faq-answer">Answer text here.</div>
</details>
```

### Updating Prices
Location: `index.html:294-304` (Course A) and `index.html:321-331` (Course B)
- Find the relevant `<table class="clean-table">` and update `<td>` values

### Changing Brand Colors
Location: `styles.css:2-32`
- Modify the CSS custom properties in `:root`

## Animation System

### Fade-Up Animation
Add class `fade-up` to any element. Optional delays: `delay-1`, `delay-2`, `delay-3`

### Stagger Animation (Multiple Items)
1. Add `stagger-trigger` to parent container
2. Add `stagger-item` to each child element
3. Items animate sequentially when container enters viewport

### Scroll Progress Bar
- Automatically managed by JS (`index.html:428-434`)
- Styled in `styles.css:54-57`

## Accessibility Notes

- `aria-label` on hamburger button
- Semantic HTML structure
- Color contrast maintained for readability
- `font-feature-settings: "palt"` for Japanese typography optimization

## External Dependencies

| Resource | URL | Purpose |
|----------|-----|---------|
| Noto Sans JP | Google Fonts | Japanese typography |
| Roboto | Google Fonts | English/numbers |
| Google Maps | maps.google.com | Embedded location map |
| LINE | lin.ee/gJxUEir | Customer contact |

## Git Workflow

- Branch naming: Feature branches may use `claude/` prefix for AI-assisted development
- Commit messages: Keep concise, describe what changed
- No CI/CD configured - manual deployment

## Troubleshooting

### Animations Not Working
- Ensure `body.js-active` class is added (JS must execute)
- Check if IntersectionObserver is supported in browser

### Mobile Menu Stuck
- Check `no-scroll` class on body element
- Verify `.active` class toggles correctly on `.js-mobile-menu`

### Fonts Not Loading
- Check internet connection (Google Fonts CDN)
- Verify `<link rel="preconnect">` tags in `<head>`

---

*This file serves as a reference for AI assistants working on this codebase. Update it when making significant architectural changes.*
