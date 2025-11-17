# BUILD Guide: Marp Presentations

**Purpose**: Instructions for building, customizing, and exporting workshop presentations
**Audience**: Instructors, content developers, technical writers

---

## Prerequisites

### Required Software

1. **Node.js 18+** (for Marp CLI)
   ```bash
   # Check version
   node --version  # Should be >= 18.0.0

   # Install via package manager
   # macOS
   brew install node

   # Ubuntu/Debian
   sudo apt install nodejs npm

   # Fedora/RHEL
   sudo dnf install nodejs npm
   ```

2. **npm** (comes with Node.js)
   ```bash
   npm --version  # Should be >= 9.0.0
   ```

3. **Chrome/Chromium** (for PDF/PowerPoint export only)
   ```bash
   # macOS
   brew install chromium

   # Ubuntu/Debian
   sudo apt install chromium-browser

   # Fedora/RHEL
   sudo dnf install chromium
   ```

### Installation

1. **Clone repository and navigate to presentations directory**:
   ```bash
   cd bootcamp-materials/presentations/
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

   This installs:
   - `@marp-team/marp-cli` - Markdown presentation tool
   - Mermaid.js support (via CDN)

---

## Build Commands

### Quick Reference

```bash
# Build both sessions as HTML
npm run build:html

# Build individual session HTML
npm run build:html:s1    # SESSION-1 only
npm run build:html:s2    # SESSION-2 only

# Build PDF (requires Chrome/Chromium)
npm run build:pdf        # Both sessions
npm run build:pdf:s1     # SESSION-1 only
npm run build:pdf:s2     # SESSION-2 only

# Build PowerPoint (requires Chrome/Chromium)
npm run build:pptx       # Both sessions
npm run build:pptx:s1    # SESSION-1 only
npm run build:pptx:s2    # SESSION-2 only

# Build all formats
npm run build:all        # HTML + PDF + PPTX for both sessions

# Development mode (live reload)
npm run dev              # Watch SESSION-1, auto-rebuild on changes
```

### Build Output

All exports are saved to `exports/` directory:

```
exports/
├── session-1-framework-intro.html
├── session-1-framework-intro.pdf        # Requires Chrome
├── session-1-framework-intro.pptx       # Requires Chrome
├── session-2-specification-implementation.html
├── session-2-specification-implementation.pdf
└── session-2-specification-implementation.pptx
```

---

## File Structure

### Presentation Files

```
presentations/
├── session-1-framework-intro.md         # SESSION 1 content
├── session-2-specification-implementation.md  # SESSION 2 content
├── test-sample.md                        # Theme test file
├── themes/
│   └── accenture-theme.css              # Custom Marp theme
├── assets/
│   ├── logos/
│   │   └── accenture-logo.svg           # Footer logo
│   ├── heroes/
│   │   └── README.md                    # Hero image instructions
│   └── overlays/
│       └── white-angular.svg            # Geometric overlays
├── exports/                             # Build outputs
├── package.json                         # Build scripts
└── README.md                            # User documentation
```

### Markdown Frontmatter

Each presentation starts with YAML configuration:

```markdown
---
marp: true                  # Enable Marp processing
theme: accenture-theme      # Use custom theme
paginate: true              # Show slide numbers
headingDivider: 2           # Auto-create slides at ## headings
---

<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true, theme: 'base' });
</script>
```

**Key settings**:
- `theme`: accenture-theme (custom CSS from `themes/` directory)
- `paginate`: true (slide numbers in footer)
- `headingDivider`: 2 (creates new slide at every `##` heading)
- Mermaid script: Required for diagrams to render

---

## Editing Slides

### Markdown Syntax

**Slide separator**:
```markdown
---
```

**Slide with custom class**:
```markdown
<!-- _class: hero -->

# Title Slide with Hero Background
```

**Available slide classes** (from accenture-theme.css):
- `hero` - Title slide with dark overlay (for hero images)
- `exercise` - Hands-on activity slide (purple left border)
- `break` - Micro-break slide (purple background)
- `checkpoint` - Validation/review slide
- `poll` - Q&A/discussion slide

**Text formatting**:
```markdown
# H1 Heading (large, purple underline)
## H2 Heading (purple text)
### H3 Heading (dark text)

**Bold text** (displays in purple via theme)
*Italic text* (displays in gray)

- Bullet point
- Another point

1. Numbered item
2. Second item
```

**Code blocks**:
```markdown
​```python
def example():
    return "syntax highlighted code"
​```
```

**Mermaid diagrams**:
```markdown
​```mermaid
flowchart LR
    A[Input] --> B{Process}
    B --> C[Output]

    style A fill:#A100FF,stroke:#A100FF,color:#fff
    style C fill:#4A90E2,stroke:#4A90E2,color:#fff
​```
```

**Mermaid color scheme** (Accenture brand):
- Purple: `#A100FF` (primary accent)
- Blue: `#4A90E2` (secondary accent)
- Green: `#7ED321` (tertiary accent)
- White backgrounds: `#FFFFFF`

---

## Theme Customization

### Editing accenture-theme.css

The custom theme is located at `themes/accenture-theme.css`.

**Brand colors**:
```css
:root {
  --accenture-purple: #A100FF;  /* Primary brand color */
  --accenture-dark: #222222;    /* Text color */
  --accenture-grey: #666666;    /* Secondary text */
  --accent-blue: #4A90E2;       /* Diagrams */
  --accent-green: #7ED321;      /* Diagrams */
  --bg-white: #FFFFFF;          /* Slide background */
  --bg-light-grey: #F5F5F5;     /* Code blocks */
}
```

**Typography**:
```css
section {
  font-family: 'Inter', 'Open Sans', -apple-system, sans-serif;
  font-size: 28px;
  line-height: 1.6;
}
```

*Note*: Graphik font requires licensing. Current fallbacks: Inter, Open Sans.

**Footer layout**:
```css
footer {
  /* Logo left | Copyright center | Slide # right */
  display: flex;
  justify-content: space-between;
}
```

### Testing Theme Changes

1. **Edit** `themes/accenture-theme.css`
2. **Test** with sample deck:
   ```bash
   npm run dev
   # Opens browser with live reload
   # Edit session-1-framework-intro.md to see changes
   ```

3. **Verify** in all export formats:
   ```bash
   npm run build:html:s1  # Quick HTML test
   npm run build:pdf:s1   # PDF render test
   ```

---

## Mermaid Diagrams

### Basic Flowchart

```markdown
​```mermaid
flowchart LR
    Start[Raw Materials] --> Q1{What stays constant?}
    Q1 --> KB[knowledge-base.md]

    Start --> Q2{What's unique?}
    Q2 --> Spec[specification.md]

    Start --> Q3{How to execute?}
    Q3 --> Impl[implementation-plan.md]

    style KB fill:#A100FF,stroke:#A100FF,color:#fff
    style Spec fill:#4A90E2,stroke:#4A90E2,color:#fff
    style Impl fill:#7ED321,stroke:#7ED321,color:#fff
​```
```

### Comparison Table

```markdown
​```mermaid
flowchart TD
    A[Session 1] --> B[knowledge-base.md<br/>Built from scratch]
    C[Session 2] --> D[specification.md<br/>+ implementation-plan.md]

    B --> E[✓ Complete]
    D --> F[→ Today]
​```
```

### Styling Nodes

```markdown
style NodeID fill:#COLOR,stroke:#COLOR,color:#fff
```

**Common patterns**:
- Purple boxes: `fill:#A100FF,stroke:#A100FF,color:#fff`
- Blue boxes: `fill:#4A90E2,stroke:#4A90E2,color:#fff`
- Green boxes: `fill:#7ED321,stroke:#7ED321,color:#fff`
- White with purple border: `fill:#FFFFFF,stroke:#A100FF,color:#222`

### Debugging Mermaid

**Diagram doesn't render**:
1. Check Mermaid.js script is in frontmatter
2. Verify syntax with [Mermaid Live Editor](https://mermaid.live/)
3. Check browser console for JavaScript errors (HTML export)
4. Ensure CDN is accessible (diagrams load from `cdn.jsdelivr.net`)

**Diagram renders in HTML but not PDF**:
- This is normal - PDF renders diagrams as static images
- If image is missing, increase build timeout:
  ```json
  {
    "scripts": {
      "build:pdf": "marp ... --timeout 60000"
    }
  }
  ```

---

## Export Formats

### HTML (Interactive)

**Pros**:
- Interactive navigation (arrow keys, click)
- Mermaid diagrams render dynamically
- Presenter mode (`P` key)
- Works on any device with browser

**Cons**:
- Requires internet for Mermaid.js CDN
- Participants can't annotate easily

**Use cases**:
- Live workshop delivery
- Self-paced online learning
- Screen sharing during virtual sessions

**Keyboard shortcuts** (HTML):
- `→` / `↓` - Next slide
- `←` / `↑` - Previous slide
- `Home` - First slide
- `End` - Last slide
- `P` - Presenter view (notes + timer)
- `F` - Fullscreen

### PDF (Printable)

**Pros**:
- Printable handouts
- Works offline
- Universal compatibility
- Participants can annotate

**Cons**:
- Requires Chrome/Chromium for export
- Mermaid diagrams render as static images
- Larger file size

**Use cases**:
- Printed workbooks
- Offline reference
- Archival documentation

**Export settings**:
```bash
marp presentation.md \
  --pdf \
  --allow-local-files \
  --theme themes/accenture-theme.css \
  -o exports/presentation.pdf
```

### PowerPoint (Editable)

**Pros**:
- Editable by participants
- Compatible with corporate environments
- Familiar interface

**Cons**:
- Requires Chrome/Chromium for export
- Formatting may shift slightly
- Loses some Marp features (speaker notes)

**Use cases**:
- Organizations requiring PowerPoint
- Collaborative editing workflows
- Customization by instructors

**Export settings**:
```bash
marp presentation.md \
  --pptx \
  --allow-local-files \
  --theme themes/accenture-theme.css \
  -o exports/presentation.pptx
```

---

## Troubleshooting

### "CHROME_PATH environment variable must be set"

**Problem**: PDF/PPTX export fails with Chrome error

**Solution**:
1. Install Chrome/Chromium (see Prerequisites)
2. Or set CHROME_PATH manually:
   ```bash
   # Find Chrome location
   which chromium-browser  # Linux
   which chromium          # macOS

   # Set environment variable
   export CHROME_PATH=/usr/bin/chromium-browser
   npm run build:pdf
   ```

### Mermaid diagrams show as code blocks

**Problem**: Diagrams don't render, show raw markdown code

**Solution**:
1. Verify Mermaid.js script in frontmatter:
   ```markdown
   <script type="module">
   import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
   mermaid.initialize({ startOnLoad: true, theme: 'base' });
   </script>
   ```

2. Check syntax with [Mermaid Live Editor](https://mermaid.live/)
3. Ensure internet connection (CDN access required)
4. Check browser console for errors

### Theme not applying

**Problem**: Slides use default Marp theme instead of Accenture theme

**Solution**:
1. Verify frontmatter: `theme: accenture-theme`
2. Check CSS file exists: `themes/accenture-theme.css`
3. Verify CSS has `@theme accenture` directive at top
4. Rebuild: `npm run build:html`

### Build fails with "Cannot find module"

**Problem**: `npm run build:html` fails immediately

**Solution**:
```bash
# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install

# Verify Marp CLI
npx marp --version
```

### Slides look different in PDF vs HTML

**Expected**: Minor formatting differences are normal

**If severe**:
1. Check font embedding (PDF uses fallbacks if Graphik unavailable)
2. Simplify complex CSS (PDF renderer has limitations)
3. Test with `--pdf-notes` for debugging:
   ```bash
   npx marp session-1-framework-intro.md --pdf --pdf-notes -o test.pdf
   ```

---

## Advanced Topics

### Adding Hero Images

1. **Add image** to `assets/heroes/`:
   ```bash
   cp mountain-landscape.jpg assets/heroes/
   ```

2. **Reference in markdown**:
   ```markdown
   <!-- _class: hero -->
   ![bg](assets/heroes/mountain-landscape.jpg)

   # First-Principles Prompt Engineering
   ```

**Image requirements**:
- Resolution: 1920×1080 (or higher)
- Format: JPG or PNG
- File size: < 2MB (for performance)
- Aspect ratio: 16:9

### Creating Geometric Overlays

1. **Edit SVG** in `assets/overlays/`:
   ```svg
   <svg width="800" height="600">
     <polygon points="..." fill="rgba(255,255,255,0.2)"/>
   </svg>
   ```

2. **Apply via CSS** in theme:
   ```css
   section.hero::before {
     background-image: url('../assets/overlays/white-angular.svg');
   }
   ```

### Embedding Local Fonts

1. **Add font files** to `assets/fonts/`:
   ```
   assets/fonts/
   ├── Graphik-Regular.woff2
   ├── Graphik-Bold.woff2
   └── Graphik-Light.woff2
   ```

2. **Reference in theme**:
   ```css
   @font-face {
     font-family: 'Graphik';
     src: url('../assets/fonts/Graphik-Regular.woff2') format('woff2');
     font-weight: 400;
   }

   section {
     font-family: 'Graphik', 'Inter', sans-serif;
   }
   ```

3. **Rebuild**:
   ```bash
   npm run build:html
   ```

### Custom Slide Classes

Add new slide types to `themes/accenture-theme.css`:

```css
/* Poll slide */
section.poll {
  background: linear-gradient(135deg, #FFFFFF 0%, #FAF5FF 100%);
}

section.poll h2 {
  color: var(--accenture-purple);
}
```

Use in markdown:
```markdown
<!-- _class: poll -->

## Quick Poll

Raise your hand if...
```

---

## CI/CD Integration

### GitHub Actions Example

```yaml
# .github/workflows/build-presentations.yml
name: Build Presentations

on:
  push:
    paths:
      - 'bootcamp-materials/presentations/**'

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm install
        working-directory: bootcamp-materials/presentations

      - name: Build HTML
        run: npm run build:html
        working-directory: bootcamp-materials/presentations

      - name: Upload artifacts
        uses: actions/upload-artifact@v3
        with:
          name: presentations
          path: bootcamp-materials/presentations/exports/
```

### GitLab CI Example

```yaml
# .gitlab-ci.yml
build-presentations:
  image: node:18
  script:
    - cd bootcamp-materials/presentations
    - npm install
    - npm run build:html
  artifacts:
    paths:
      - bootcamp-materials/presentations/exports/
    expire_in: 1 week
  only:
    changes:
      - bootcamp-materials/presentations/**
```

---

## Resources

**Marp Documentation**:
- Official site: https://marp.app/
- Marp CLI: https://github.com/marp-team/marp-cli
- Marp Core: https://github.com/marp-team/marp-core

**Mermaid Documentation**:
- Official site: https://mermaid.js.org/
- Live editor: https://mermaid.live/
- Syntax reference: https://mermaid.js.org/syntax/flowchart.html

**Accenture Brand Guidelines**:
- (Internal link to official brand portal)
- (Internal link to Graphik font licensing)

---

## Maintenance

### Updating Marp CLI

```bash
cd bootcamp-materials/presentations
npm update @marp-team/marp-cli
npm run build:html  # Test after update
```

### Updating Mermaid

Mermaid loads from CDN, so update the version in frontmatter:

```markdown
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true, theme: 'base' });
</script>
```

### Backing Up Custom Assets

```bash
# Backup theme and assets
tar -czf accenture-theme-backup.tar.gz \
  themes/accenture-theme.css \
  assets/logos/ \
  assets/heroes/ \
  assets/overlays/
```

---

**Version**: 1.0
**Last Updated**: 2025-11-17
**Maintainer**: Workshop Development Team
