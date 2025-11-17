# PDF Export Instructions

## Current Status

✓ **HTML presentations generated** (125K + 135K)
❌ **PDF/PowerPoint export requires Chrome/Chromium**

---

## Why PDFs Can't Be Generated

Marp CLI requires a Chrome/Chromium browser to render presentations as PDFs. The browser engine is used to:
1. Render HTML/CSS with proper styling
2. Execute JavaScript (Mermaid diagrams)
3. Convert to PDF format with correct pagination

**Current system**: Chrome/Chromium not detected in PATH or Flatpak

---

## Options to Generate PDFs

### Option 1: Install Chrome/Chromium (Recommended)

**Via DNF (Fedora/RHEL)**:
```bash
sudo dnf install chromium
```

**Via Flatpak**:
```bash
flatpak install flathub org.chromium.Chromium
# Then set CHROME_PATH:
export CHROME_PATH=/var/lib/flatpak/exports/bin/org.chromium.Chromium
```

**Via Snap**:
```bash
sudo snap install chromium
```

**Then build PDFs**:
```bash
cd /home/joey/Documents/GitHub/docs
npm run build:pdf
```

### Option 2: Use Browser "Print to PDF"

**For immediate PDF needs**:

1. **Open HTML in browser**:
   ```bash
   firefox bootcamp-materials/presentations/exports/session-1-framework-intro.html
   ```

2. **Print to PDF**:
   - Press `Ctrl+P` (or `Cmd+P` on Mac)
   - Select "Print to PDF" or "Save as PDF"
   - Settings:
     - Layout: Landscape
     - Margins: None
     - Background graphics: Enabled
     - Scale: 100%
   - Save as `session-1-framework-intro.pdf`

3. **Repeat for SESSION-2**:
   ```bash
   firefox bootcamp-materials/presentations/exports/session-2-specification-implementation.html
   ```

**Pros**: Works immediately, no installation needed
**Cons**: Manual process, may have slight formatting differences

### Option 3: Use Online Conversion Service

**Cloudconvert** (free tier available):
1. Go to https://cloudconvert.com/html-to-pdf
2. Upload HTML files from `exports/` directory
3. Download generated PDFs

**Pros**: No local installation needed
**Cons**: Requires internet, privacy concerns for sensitive content

### Option 4: Use Docker with Chrome

**If Docker is available**:

```bash
# Pull Marp CLI Docker image (includes Chrome)
docker pull marpteam/marp-cli

# Build PDFs
docker run --rm -v $(pwd):/home/marp/app/ marpteam/marp-cli \
  bootcamp-materials/presentations/session-1-framework-intro.md \
  --pdf \
  --theme bootcamp-materials/presentations/themes/accenture-theme.css \
  --allow-local-files \
  -o bootcamp-materials/presentations/exports/session-1-framework-intro.pdf
```

**Pros**: Isolated environment, includes all dependencies
**Cons**: Requires Docker, larger download

---

## Current Deliverables

### ✓ Available Now (HTML)

**Session 1**: `exports/session-1-framework-intro.html` (125K)
- 40 pages, interactive navigation
- Mermaid diagrams render correctly
- Arrow keys to advance slides
- Press `P` for presenter mode

**Session 2**: `exports/session-2-specification-implementation.html` (135K)
- 54 pages, interactive navigation
- Full Accenture branding
- Press `F` for fullscreen

**Usage**:
```bash
# Open in browser for presentation
firefox bootcamp-materials/presentations/exports/session-1-framework-intro.html

# Or serve via local web server
cd bootcamp-materials/presentations/exports
python3 -m http.server 8000
# Then open: http://localhost:8000/session-1-framework-intro.html
```

### ⏸ Pending (PDF/PPTX)

**Requires**: Chrome/Chromium installation (see Option 1 above)

**Once installed, build with**:
```bash
npm run build:pdf    # Generates both PDFs
npm run build:pptx   # Generates both PowerPoint files
npm run build:all    # Generates all formats
```

---

## Verification

After installing Chrome/Chromium, verify it's detected:

```bash
# Check if Chrome is in PATH
which chromium chromium-browser google-chrome microsoft-edge

# Test with Marp
npx marp --version
npx marp --pdf --help  # Should not show Chrome warning
```

If Chrome is installed but not detected:

```bash
# Set CHROME_PATH manually
export CHROME_PATH=/usr/bin/chromium-browser  # Adjust path as needed
npm run build:pdf
```

---

## HTML vs PDF Trade-offs

### HTML Presentations (Current)

**Pros**:
- ✓ Interactive navigation (keyboard shortcuts)
- ✓ Mermaid diagrams render dynamically
- ✓ Presenter mode with notes
- ✓ Works on any device with browser
- ✓ Smaller file size

**Cons**:
- ✗ Requires internet for Mermaid.js CDN
- ✗ Can't annotate easily
- ✗ Harder to print

**Best for**: Live workshop delivery, screen sharing

### PDF Presentations (Pending)

**Pros**:
- ✓ Printable handouts
- ✓ Works offline
- ✓ Universal compatibility
- ✓ Participants can annotate

**Cons**:
- ✗ No interactive navigation
- ✗ Mermaid diagrams are static images
- ✗ Larger file size
- ✗ Requires Chrome/Chromium to generate

**Best for**: Printed workbooks, offline reference

---

## Next Steps

1. **For immediate workshop delivery**: Use HTML presentations (already available)
2. **For printed materials**: Use Option 2 (Browser Print to PDF) as temporary solution
3. **For production**: Install Chromium via Option 1 and generate proper PDFs

---

**Created**: 2025-11-17
**Status**: HTML ✓ | PDF/PPTX ⏸ (awaiting Chrome installation)
