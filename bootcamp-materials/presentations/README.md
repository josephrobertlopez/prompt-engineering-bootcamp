# First-Principles Prompt Engineering Workshop

**Presentation Materials** | Accenture Corporate Style

---

## Overview

This directory contains complete workshop materials for teaching first-principles prompt engineering through discovery-based learning. Participants learn to build prompt file systems (knowledge-base.md, specification.md, implementation-plan.md) from scratch rather than copying templates.

**Format**: 2 × 90-minute sessions
**Audience**: Teams building AI workflows, prompt engineers, technical writers
**Pedagogy**: Discovery exercises + peer review + cognitive optimization

---

## Contents

```
presentations/
├── session-1-framework-intro.md          # SESSION 1: 3-Question Framework (23 slides, ~40 pages)
├── session-2-specification-implementation.md  # SESSION 2: Spec + Implementation (30 slides, ~54 pages)
├── test-sample.md                         # Theme testing slides (internal use)
├── INSTRUCTOR-NOTES.md                    # Comprehensive facilitation guide
├── themes/
│   └── accenture-theme.css               # Custom Marp theme (Accenture branding)
├── assets/
│   ├── logos/
│   │   └── accenture-logo.svg            # Placeholder logo (replace with official)
│   ├── heroes/
│   │   └── README.md                     # Instructions for hero images
│   └── overlays/
│       └── white-angular.svg             # Geometric overlay for title slides
└── exports/
    ├── session-1-framework-intro.html    # SESSION 1 HTML export
    ├── session-2-specification-implementation.html  # SESSION 2 HTML export
    └── test-sample.html                  # Theme test export
```

---

## Quick Start (Instructors)

### 1. Build Presentations

```bash
# Install dependencies (first time only)
npm install

# Build HTML exports for both sessions
npm run build:html

# Build PDF exports (requires Chrome/Chromium installed)
npm run build:pdf

# Build PowerPoint exports (requires Chrome/Chromium)
npm run build:pptx

# Build all formats at once
npm run build:all

# Development mode (live reload for editing)
npm run dev
```

### 2. Review Instructor Notes

Read [`INSTRUCTOR-NOTES.md`](./INSTRUCTOR-NOTES.md) for:
- Pre-workshop preparation checklist
- Minute-by-minute facilitation guide
- Troubleshooting tips
- Customization guidance

### 3. Prepare Materials

**Send to participants 1 week before:**
- FY26 Priorities Guide (PDF) - in `bootcamp-materials/references/`
- Interview questions (TXT) - in `bootcamp-materials/references/`
- Blank template files (markdown)
- Workshop agenda

**Bring to session:**
- HTML exports (in `exports/` directory)
- Printed 3-Question Framework diagram
- Backup USB drive with slides
- Timer for micro-breaks

---

## Technology Stack

### Marp (Markdown Presentation Ecosystem)

Presentations are written in **Markdown** and converted to slides using **Marp CLI**.

**Why Marp?**
- Version control friendly (plain text)
- Multi-format export (HTML, PDF, PowerPoint)
- Mermaid diagram support
- Custom theming (Accenture branding)

**Documentation**: https://marp.app/

### Mermaid Diagrams

Flowcharts and diagrams are written as code using **Mermaid** syntax, embedded directly in markdown.

**Example:**
```markdown
​```mermaid
flowchart LR
    A[Input] --> B[Process] --> C[Output]
​```
```

**Documentation**: https://mermaid.js.org/

### Custom Theme

`accenture-theme.css` implements Accenture corporate branding:

- **Colors**: White backgrounds, purple accents (#A100FF)
- **Typography**: Graphik font family (fallback: Inter, Open Sans)
- **Slide classes**:
  - `hero` - Title slides with dark overlay
  - `exercise` - Hands-on activity slides (purple left border)
  - `break` - Micro-break slides (purple background)
  - `checkpoint` - Validation/review slides
  - `poll` - Q&A/discussion slides

**Customization**: Edit `themes/accenture-theme.css` to adjust colors, fonts, or layouts.

---

## Editing Slides

### Markdown Syntax

**Slide separator:**
```markdown
---
```

**Slide with custom class:**
```markdown
<!-- _class: hero -->

# Title Slide Content
```

**Headers:**
```markdown
# H1 (large header with purple underline)
## H2 (purple text)
### H3 (dark text)
```

**Emphasis:**
```markdown
**Bold text** (displays in purple due to theme)
*Italic text* (displays in gray)
```

**Lists:**
```markdown
- Bullet point
- Another point

1. Numbered item
2. Second item
```

**Code blocks:**
```markdown
​```markdown
# Example code
​```
```

**Mermaid diagrams:**
```markdown
​```mermaid
flowchart LR
    A --> B --> C
​```
```

### Frontmatter Configuration

Each presentation starts with YAML frontmatter:

```markdown
---
marp: true                  # Enable Marp processing
theme: accenture-theme      # Use custom theme
paginate: true              # Show slide numbers
headingDivider: 2           # Auto-create slides at ## headings
---
```

**Mermaid.js setup** (required for diagrams):
```markdown
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true, theme: 'base' });
</script>
```

---

## Build Scripts Explained

Located in `package.json`:

```json
{
  "scripts": {
    "build:html": "...",      // Build both sessions as HTML
    "build:html:s1": "...",   // Build SESSION 1 only (HTML)
    "build:html:s2": "...",   // Build SESSION 2 only (HTML)
    "build:pdf:s1": "...",    // Build SESSION 1 as PDF
    "build:pdf:s2": "...",    // Build SESSION 2 as PDF
    "build:pdf": "...",       // Build both sessions as PDF
    "build:pptx:s1": "...",   // Build SESSION 1 as PowerPoint
    "build:pptx:s2": "...",   // Build SESSION 2 as PowerPoint
    "build:pptx": "...",      // Build both sessions as PowerPoint
    "build:all": "...",       // Build all formats (HTML + PDF + PPTX)
    "dev": "..."              // Live reload for editing SESSION 1
  }
}
```

**Common commands:**

```bash
# Edit and preview SESSION 1 with live reload
npm run dev

# Build just SESSION 2 HTML
npm run build:html:s2

# Build everything
npm run build:all
```

---

## Export Formats

### HTML (Recommended for Delivery)

**Pros:**
- Interactive navigation (arrow keys, click to advance)
- Mermaid diagrams render perfectly
- Fullscreen presenter mode (press `P`)
- Works on any device with browser
- No software installation required

**Cons:**
- Requires internet for Mermaid.js (or embed locally)
- Participants can't annotate easily

**Use cases:**
- Live workshop delivery
- Self-paced online learning
- Sharing via web link

### PDF

**Pros:**
- Printable handouts
- Works offline
- Participants can annotate
- Universal compatibility

**Cons:**
- Requires Chrome/Chromium for export
- Mermaid diagrams render as static images
- Larger file size

**Use cases:**
- Printed workbooks
- Offline reference
- Archival

### PowerPoint (PPTX)

**Pros:**
- Editable by participants (if sharing source)
- Compatible with corporate environments
- Familiar interface

**Cons:**
- Requires Chrome/Chromium for export
- Formatting may shift slightly
- Loses some Marp-specific features

**Use cases:**
- Organizations that mandate PowerPoint
- Collaborative editing workflows

---

## Known Limitations

### PDF/PPTX Export Requires Browser

**Error message:**
```
The CHROME_PATH environment variable must be set...
```

**Solution:**
Install Chrome, Chromium, or Edge:

```bash
# Fedora/RHEL
sudo dnf install chromium

# Ubuntu/Debian
sudo apt install chromium-browser

# macOS
brew install chromium
```

Alternatively, set `CHROME_PATH` environment variable:
```bash
export CHROME_PATH=/path/to/chrome
npm run build:pdf
```

### Mermaid Diagrams in PDF

Mermaid diagrams are rendered as static images in PDF exports. If diagrams appear broken:

1. Ensure Mermaid.js loads correctly in HTML export first
2. Check Chrome/Chromium has network access to CDN
3. Increase `--timeout` flag in build script if large diagrams

---

## Customization

### Changing Brand Colors

Edit `themes/accenture-theme.css`:

```css
:root {
  --accenture-purple: #A100FF;  /* Change to your brand color */
  --accenture-dark: #222222;
  --accent-blue: #4A90E2;       /* Secondary accent */
  --accent-green: #7ED321;      /* Tertiary accent */
}
```

### Adding Logo

1. Replace `assets/logos/accenture-logo.svg` with your official logo
2. Update theme CSS if needed (logo sizing)
3. Rebuild presentations

### Adding Hero Images

1. Add landscape images (1920×1080 recommended) to `assets/heroes/`
2. Reference in markdown:

```markdown
<!-- _class: hero -->
![bg](assets/heroes/mountain-landscape.jpg)

# Your Title Here
```

### Adjusting Timing

Edit slide content directly in `.md` files. Key timing sections:

**SESSION 1:**
- Exercise slide (currently "30 minutes") - adjust if needed
- Micro-breaks (currently "2 minutes") - can extend to 3-5 min

**SESSION 2:**
- Peer review circle (currently "20 minutes") - scale based on group size
- Advanced patterns (slides 19-21) - optional, cut if running behind

See `INSTRUCTOR-NOTES.md` for detailed timing breakdowns.

---

## Troubleshooting

### Mermaid Diagrams Don't Render

**Symptom**: Diagrams show as code blocks instead of visual diagrams

**Fixes:**
1. Ensure `<script type="module">` block is present in frontmatter
2. Check browser console for JavaScript errors (HTML export)
3. Verify internet connection (Mermaid.js loads from CDN)
4. Test with `npm run dev` to see live rendering

### Build Fails with "Cannot find module"

**Symptom**: `npm run build:html` fails immediately

**Fixes:**
```bash
# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Verify Marp CLI is installed
npx marp --version
```

### Slides Look Different in PDF vs HTML

**Expected**: Some formatting differences are normal (fonts, spacing)

**If severe**:
1. Check if custom fonts are embedded (PDF may use fallbacks)
2. Simplify complex CSS (PDF renderer has limitations)
3. Test with `--pdf-notes` flag for debugging

### Theme Not Applying

**Symptom**: Slides use default Marp theme instead of Accenture theme

**Fixes:**
1. Verify frontmatter has `theme: accenture-theme`
2. Check `--theme` flag in build script points to correct CSS file
3. Ensure CSS file has `@theme accenture` at top
4. Rebuild with `npm run build:html`

---

## Contributing

### Reporting Issues

Found a bug or have a suggestion? Create an issue with:
- Description of problem
- Steps to reproduce
- Expected vs. actual behavior
- Screenshots (if visual issue)

### Suggesting Improvements

**Content improvements:**
- New slide examples
- Clearer explanations
- Additional exercises

**Technical improvements:**
- Theme enhancements
- Build script optimizations
- Accessibility improvements

### Code Style

**Markdown:**
- Use 2-space indentation for lists
- One blank line between sections
- Wrap lines at 100 characters (soft limit)

**CSS:**
- Follow existing naming conventions
- Comment non-obvious rules
- Test across export formats (HTML, PDF, PPTX)

---

## License

Workshop materials (slides, exercises, instructor notes) are proprietary.
Technical implementation (Marp configuration, theme CSS) can be adapted for internal use.

Accenture branding assets (logo, colors) are trademarks of Accenture. Replace with your organization's branding if adapting for non-Accenture use.

---

## Support

**For workshop facilitation questions:**
- Review `INSTRUCTOR-NOTES.md` first
- Check FAQ section in notes
- Contact workshop development team

**For technical issues (Marp, builds):**
- See Troubleshooting section above
- Consult Marp documentation: https://marp.app/
- File issue in this repository

---

## Changelog

### v1.0.0 (2025-11-17)

**Initial release:**
- SESSION 1: Framework Introduction (23 slides)
- SESSION 2: Specification + Implementation (30 slides)
- Custom Accenture theme with purple branding
- Mermaid diagram integration
- Comprehensive instructor notes
- Multi-format export (HTML, PDF, PPTX)
- Build automation via npm scripts

---

**Maintained by**: Workshop Development Team
**Last updated**: 2025-11-17
