# Brand Decisions - 402.cat

> Recorded: January 2026

---

## Quick Reference

| Decision | Value |
|----------|-------|
| **Primary Marks** | `▲ ▲` (ears) OR `CAT` (wordmark) |
| **THE RULE** | Never use both together |
| **Default Theme** | Dark |
| **Primary Accent** | `#00ff88` (dark) / `#006400` (light) |
| **Typography** | `ui-monospace` stack, bold |
| **Tagline** | "agents are just cats with wallets" |

---

## THE MARKS: Dual System

### The Rule
**▲ ▲** and **CAT** are interchangeable.
**NEVER use both together.** Pick one per context.

### Mark 1: Ears (`▲ ▲`)
Just the ears - minimal, sophisticated.
- Scales perfectly at any size (down to 16px)
- Works on any background
- Path-based (no font dependencies)
- Use for: favicon, icons, PFP, paired with "402.cat" text

### Mark 2: CAT Wordmark
Pixel-block "CAT" letterforms - grid-based, terminal aesthetic.
- Bold standalone presence
- Works at larger sizes (banners, hero)
- Use for: Twitter banner, hero sections, standalone brand recognition

### Usage

| Context | Mark | File |
|---------|------|------|
| Twitter Banner | CAT wordmark | `twitter-banner-cat-xl-1500x500-dark.svg` |
| Hero sections | CAT wordmark | `og-cat-1200x630-dark.svg` |
| Favicon | Ears | `favicon-32-dark.svg` |
| Twitter PFP | Ears | `pfp-ears-400-dark.svg` |
| Website footer | Ears | With "402.cat" text |
| CLI | ASCII cat | Full personality in terminal |

---

## COLORS

### Dark Mode (Default)
```css
--brand-bg: #000000;
--brand-fg: #FFFFFF;
--brand-accent: #00ff88;
```

### Light Mode
```css
--brand-bg: #FFFFFF;
--brand-fg: #000000;
--brand-accent: #006400;
```

### Full Palette
| Token | Dark | Light | Use |
|-------|------|-------|-----|
| Background | #000000 | #FFFFFF | Main bg |
| Foreground | #FFFFFF | #000000 | Text |
| Accent | #00ff88 | #006400 | CTAs, highlights |
| Success | #00ff88 | #006400 | Positive states |
| Error | #ff4444 | #cc0000 | Errors |
| Warning | #ffff00 | #cc9900 | Warnings |
| Muted | #888888 | #666666 | Secondary text |
| Surface | #111111 | #f5f5f5 | Cards, panels |
| Border | #333333 | #dddddd | Borders |

---

## TYPOGRAPHY

### Font Stack
```css
font-family: ui-monospace, SFMono-Regular, Menlo, Monaco,
             Consolas, 'Liberation Mono', 'Courier New', monospace;
```

### Weights
- **Body:** 400 (normal)
- **Headings:** 700 (bold)
- **Emphasis:** 700 (bold)

### Style Notes
- Lowercase preferred for UI
- Terminal formatting (`>`, `//`, `$`)
- No periods in headlines
- Playful but not emoji-heavy

---

## VOICE & TONE

### The Voice
Cat narrator, not corporate.

### Key Phrases
- "agents are just cats with wallets" (tagline)
- "gives agents claws" (capability)
- "playground for agents" (vision)
- "the feral economy" (thesis)

### Avoid
- Corporate speak ("leverage", "synergy")
- "X for Y" patterns
- Over-explaining
- Being too cute (on website)

---

## DO NOT USE

- `v11-pointy` (superseded by Ears Only)
- Both marks together (NEVER stack `▲ ▲` with CAT)
- `neko*` variants (exploration only)
- CAT wordmark v1/v2/v4/v5/v6 (v3 is THE wordmark)
- Old favicons with faces (just ears now)

---

```
▲ ▲  or  CAT
    never both.
```
