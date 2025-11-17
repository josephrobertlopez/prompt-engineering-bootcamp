# Logo Assets

## Current Status

⚠️ **PLACEHOLDER LOGOS IN USE** - Replace with official branded assets before production use

This directory contains placeholder logo files that approximate the visual style of Accenture and Capital One brands. These **must be replaced** with official brand assets before deploying presentations.

---

## Files

### Accenture Logo
**File**: `accenture-logo.svg`
**Status**: 🔴 Placeholder
**Colors**: Purple (#A100FF) with greater-than accent
**Size**: 200×50px

**Official Asset Required**:
- Format: SVG or high-res PNG (transparent background)
- Source: Accenture Brand Portal (internal)
- Guidelines: Accenture Brand Standards documentation
- Min resolution: 300 DPI for print, vector preferred

**Where to obtain**:
1. Internal brand portal: `https://brandhub.accenture.com` (VPN required)
2. Marketing/Communications team
3. Brand & Creative Services department

### Capital One Logo
**File**: `capital-one-logo.svg`
**Status**: 🔴 Placeholder
**Colors**: Navy (#004879) with orange swoosh (#DA6A26)
**Size**: 220×50px

**Official Asset Required**:
- Format: SVG or high-res PNG (transparent background)
- Source: Capital One Brand Center (internal)
- Guidelines: Capital One Brand Guidelines
- Min resolution: 300 DPI for print, vector preferred

**Where to obtain**:
1. Internal brand center: Capital One Brand Portal (internal access)
2. Marketing/Brand team
3. External Affairs department

---

## Usage in Presentations

### Marp Theme Integration

Logos are referenced in `themes/accenture-theme.css`:

```css
footer .logo {
  width: 120px;
  background-image: url('../assets/logos/accenture-logo.svg');
}
```

**To update**:
1. Replace `accenture-logo.svg` with official file (keep same filename)
2. Or update CSS to reference new filename
3. Rebuild presentations: `npm run build:html`

### Manual Slide Integration

For custom logo placement:

```markdown
<!-- In your .md slide file -->
![Accenture Logo](assets/logos/accenture-logo.svg)
```

---

## Brand Guidelines Compliance

### Accenture
- **Primary Color**: Purple (#A100FF)
- **Typography**: Graphik (licensed font)
- **Logo Variants**: Full color, white, black
- **Clear Space**: Minimum 1x logo height around logo
- **Minimum Size**: 0.5" width in print, 120px on screen
- **Don't**: Stretch, rotate, recolor, add effects

**Reference**: Accenture Brand Standards Manual (internal document)

### Capital One
- **Primary Colors**: Navy (#004879), Orange (#DA6A26)
- **Typography**: Optimist (proprietary font)
- **Logo Variants**: Horizontal, stacked, white
- **Clear Space**: Minimum clear space equal to height of "Capital"
- **Minimum Size**: 0.625" width in print, 125px on screen
- **Don't**: Alter proportions, change colors, add shadows

**Reference**: Capital One Brand Guidelines (internal document)

---

## File Format Requirements

### For Digital Presentations (Preferred)
- **Format**: SVG (vector)
- **Background**: Transparent
- **Color Mode**: RGB
- **Benefits**: Scales perfectly, small file size

### For Print Materials (Alternative)
- **Format**: PNG with transparency
- **Resolution**: 300 DPI minimum
- **Color Mode**: CMYK (for offset printing) or RGB (for digital)
- **Size**: 2x-3x display size for retina screens

### Not Recommended
- ❌ JPG (no transparency, compression artifacts)
- ❌ Low-resolution PNG (<150 DPI)
- ❌ Raster formats for vector logos

---

## Trademark & Legal

### Accenture
**Status**: Registered trademark of Accenture
**Usage Rights**: Internal use only (employees and authorized partners)
**Approval Required**: Yes, from Brand team for external-facing materials
**Copyright**: © 2025 Accenture. All rights reserved.

### Capital One
**Status**: Registered trademark of Capital One Financial Corporation
**Usage Rights**: Internal use only (employees and authorized partners)
**Approval Required**: Yes, from Brand/Legal for external use
**Copyright**: © 2025 Capital One. All rights reserved.

⚠️ **Important**: Using these logos without proper authorization may violate trademark law. Always obtain approval for external-facing materials.

---

## Replacement Checklist

Before deploying presentations to external audiences:

- [ ] Obtained official Accenture logo from brand portal
- [ ] Obtained official Capital One logo from brand center
- [ ] Verified logo format (SVG or high-res PNG)
- [ ] Replaced placeholder files in `assets/logos/`
- [ ] Tested logo rendering in HTML export
- [ ] Tested logo rendering in PDF export (if used)
- [ ] Verified clear space and minimum size requirements
- [ ] Obtained approval from Brand team (if external use)
- [ ] Removed placeholder notice comments from SVG files
- [ ] Rebuilt presentations: `npm run build:all`

---

## Troubleshooting

**Logo doesn't appear in footer:**
1. Check file path in `themes/accenture-theme.css`
2. Verify file exists in `assets/logos/` directory
3. Rebuild presentations: `npm run build:html`
4. Check browser console for 404 errors

**Logo appears pixelated:**
1. Ensure using vector SVG (not raster PNG)
2. Check PNG resolution if raster (should be ≥300 DPI)
3. Verify logo size in CSS matches source dimensions

**Logo has wrong colors:**
1. Open SVG in text editor, check `fill` attributes
2. Compare to brand guidelines color codes
3. Replace with official brand asset (not placeholder)

---

## Contact

**For Accenture brand assets:**
- Brand Portal: `https://brandhub.accenture.com`
- Email: `brand.team@accenture.com` (example)
- Slack: `#brand-support` (if available)

**For Capital One brand assets:**
- Brand Center: Internal portal (check intranet)
- Email: Brand team contact
- Slack: `#brand-guidelines` (if available)

**For technical issues:**
- Review `BUILD.md` in parent directory
- Check Marp theme documentation
- File issue in repository

---

**Last Updated**: 2025-11-17
**Placeholder Version**: 1.0
**Production Ready**: ❌ No - Official assets required
