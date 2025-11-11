# AI Configuration Files - Examples

**Purpose:** Show how to configure AI coding assistants with project-specific instructions

**Focus:** GitHub Copilot + Windsurf + VSCode (industry-standard tools)

---

## 🟡🟢 Recommended Configurations (Tier 1-2)

### 1. GitHub Copilot Instructions (🟡 Tier 2 - Official)

**File:** `.github/copilot-instructions.md`

**Status:** Official Microsoft/GitHub standard
**Documentation:** https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot
**IDE Support:** VSCode, Visual Studio, JetBrains, Neovim
**Maturity:** ~2 years, official standard

**When to use:**
- ✅ Using GitHub Copilot (most common AI assistant)
- ✅ Want official Microsoft-backed standard
- ✅ Team uses VSCode, Visual Studio, or JetBrains
- ✅ Need cross-IDE consistency

**Example:** [.github/copilot-instructions.md](.github/copilot-instructions.md)

---

### 2. Windsurf Rules (🟠 Tier 3 - Growing)

**File:** `.windsurfrules`

**Status:** Codeium Windsurf IDE standard
**Documentation:** https://docs.windsurf.com (Cascade AI)
**IDE Support:** Windsurf (VSCode-based)
**Maturity:** New (2024), growing adoption

**When to use:**
- ✅ Using Windsurf IDE (Codeium's VSCode-based AI IDE)
- ✅ Want Cascade AI integration
- ✅ Prefer VSCode-based experience with integrated AI

**Example:** [.windsurfrules](.windsurfrules)

---

## 🟠 Alternative Configurations (Tier 3)

### 3. Cursor Rules (🟠 Tier 3 - IDE-specific)

**File:** `.cursorrules`

**Status:** Cursor IDE specific
**Documentation:** https://cursor.sh/docs
**IDE Support:** Cursor only (VSCode fork)
**Maturity:** ~1 year, niche adoption

**When to use:**
- ⚠️ Only if team committed to Cursor IDE
- ⚠️ Not recommended for general use (IDE lock-in)

**Note:** Included for completeness but **NOT recommended** as primary approach.

**Example:** [.cursorrules](.cursorrules) (legacy, for reference only)

---

### 4. Aider Digest (🟠 Tier 3 - Tool-specific)

**File:** `.aidigestrc`

**Status:** Aider CLI tool specific
**Documentation:** https://aider.chat/docs/config.html
**IDE Support:** Command-line tool (any editor)
**Maturity:** ~1 year, developer tool enthusiasts

**When to use:**
- ⚠️ Only if using Aider CLI for AI-assisted coding
- ⚠️ Specialized use case

**Example:** [.aidigestrc](.aidigestrc) (legacy, for reference only)

---

## 📊 Comparison Matrix

| Configuration | Maturity | IDE Support | Official | Recommended |
|--------------|----------|-------------|----------|-------------|
| **GitHub Copilot** (.github/copilot-instructions.md) | 🟡 Tier 2 | VSCode, VS, JetBrains, Neovim | ✅ Yes (Microsoft) | ⭐ **PRIMARY** |
| **Windsurf** (.windsurfrules) | 🟠 Tier 3 | Windsurf (VSCode-based) | ✅ Yes (Codeium) | ⭐ **SECONDARY** |
| **Cursor** (.cursorrules) | 🟠 Tier 3 | Cursor only | ❌ No | ⚠️ Not recommended |
| **Aider** (.aidigestrc) | 🟠 Tier 3 | CLI tool (any editor) | ❌ No | ⚠️ Specialized only |

---

## 🎯 Recommendation for Teams

### Best Practice: GitHub Copilot + Windsurf

**Primary:** `.github/copilot-instructions.md`
- Official Microsoft standard
- Works across multiple IDEs (VSCode, JetBrains, etc.)
- Most widely adopted (~2 years mature)

**Secondary:** `.windsurfrules`
- For teams using Windsurf IDE
- VSCode-based with strong AI integration
- Growing adoption

**Avoid:** IDE-specific lock-in (Cursor)
- Limits team flexibility
- Not industry-standard

---

## 🚀 Quick Start

### For GitHub Copilot (VSCode)

1. Create `.github/copilot-instructions.md` in project root
2. Copy template from [.github/copilot-instructions.md](.github/copilot-instructions.md)
3. Customize for your project
4. Copilot automatically reads on startup

### For Windsurf

1. Create `.windsurfrules` in project root
2. Copy template from [.windsurfrules](.windsurfrules)
3. Customize for your project
4. Windsurf Cascade AI reads automatically

### For Both (Recommended)

Create both files - teams can choose their preferred IDE:
```bash
.github/copilot-instructions.md  # GitHub Copilot users
.windsurfrules                   # Windsurf users
```

Same content, different formats. Maximum team flexibility.

---

## 📝 Pattern Application

All config files demonstrate:
- **Persona Pattern:** AI role as domain specialist
- **Few-shot Pattern:** Before/after transformation examples
- **Template Pattern:** Structured quality requirements
- **Decision Documentation:** Rationale for approach choices

**Key insight:** Same patterns apply regardless of config file format. Choose format based on team's tools, not theoretical preferences.

---

## 🔗 Additional Resources

**Official Documentation:**
- GitHub Copilot: https://docs.github.com/en/copilot
- Windsurf: https://docs.windsurf.com
- VSCode: https://code.visualstudio.com/docs

**Research Backing:**
- White et al. (2023): Prompt Pattern Catalog - arXiv 2302.11382
- ADR Template: https://github.com/joelparkerhenderson/architecture-decision-record

---

**Last Updated:** November 2025
**Focus:** GitHub Copilot + Windsurf + VSCode (industry standards)
