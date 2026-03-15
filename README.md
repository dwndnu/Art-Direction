# Art Direction — Creative Director Skill Suite

End-to-end visual content workflow automation for Claude Code. From research to Canva design to email delivery — in one session.

Built for the **Creative Director / Art Director / Graphic Designer** workflow.

---

## Overview

Four skills that work as a connected pipeline:

```
/creative brief  →  /creative design  →  /creative deliver
     ↓                    ↓                     ↓
CREATIVE-BRIEF.md    CREATIVE-STATE.md      CREATIVE-LOG.md
 (art direction)      (canva design ID)     (delivery record)
```

---

## Skills

### `creative` — Orchestrator
Routes commands, manages workflow gates, maintains format reference, and enforces Creative Direction Principles across all phases.

**Flagship command:**
```
/creative campaign <topic>
```
Runs all phases sequentially with confirmation gates between each phase. Will not proceed to design without brief approval. Will not send email without design approval.

---

### `creative-brief` — Research & Art Direction Brief

Researches the visual landscape, defines creative strategy, and produces a production-ready brief.

```
/creative brief <topic/brand/url>
```

**Output:** `CREATIVE-BRIEF-[ProjectName].md`

What it produces:
- **Creative Challenge** — the specific problem the design must solve
- **Single-Minded Proposition (SMP)** — one sentence, no conjunctions, one idea
- **Creative Territory** — the brand's strategic aesthetic space
- **Color Palette** — with hex codes, usage rules, and rationale
- **Typography** — Canva-available fonts, scale ratios, personality
- **Imagery Direction** — specific style, DON'Ts, and composition rules
- **Format Specifications** — per-platform dimensions and constraints
- **Copy Framework** — headline/body/CTA direction
- **Success Criteria** — measurable metrics, not just vibes
- **Visual References** — direct + lateral + anti-references

---

### `creative-design` — Canva Art Direction

Executes the brief in Canva. Template-first approach. Visual evaluation via thumbnail. FLUX image generation for custom assets.

```
/creative design [brief-file]
```

**Output:** Canva design link + `CREATIVE-STATE.md`

Key behaviors:
- Reads brief parameters before touching Canva
- Searches for templates before AI generation from scratch
- Evaluates generated designs **visually via thumbnail** — not just structural data
- Uses FLUX (`gr1_flux_1_kontext_dev_infer`) to generate custom imagery → uploads to Canva
- Documents every creative decision not in the brief
- Honest about Canva AI limitations — iterates instead of assuming compliance

---

### `creative-deliver` — Export & Email

Sets sharing permissions, exports the design, composes a professional delivery email, and maintains the project log.

```
/creative deliver <recipient@email.com>
```

**Output:** Shared Canva link + Gmail delivery + `CREATIVE-LOG.md`

Key behaviors:
- **Always sets Canva sharing permissions before sending** — private links = Access Denied for recipient
- Honest about Gmail MCP limitations: delivers Canva link, not binary email attachments
- Always previews the full email before sending — no "just send it" bypass
- Classifies revision feedback: execution-level (edit in Canva) vs concept-level (rebrief)
- Maintains `CREATIVE-LOG.md` as separate project history

---

## All Commands

| Command | Description |
|---------|-------------|
| `/creative campaign <topic>` | Full end-to-end workflow |
| `/creative brief <topic/brand/url>` | Research + creative brief only |
| `/creative design [brief-file]` | Canva design execution only |
| `/creative deliver <email>` | Export + email delivery only |
| `/creative inspect <canva-url>` | Art direction review of existing design |
| `/creative resize <canva-url> <format>` | Adapt design to new format |
| `/creative image <prompt>` | Generate image via FLUX + optional Canva upload |

---

## File System

| File | Created by | Purpose |
|------|-----------|---------|
| `CREATIVE-BRIEF-[Name].md` | `creative-brief` | Art direction source of truth |
| `CREATIVE-STATE.md` | `creative-design` | Canva design ID + version state |
| `CREATIVE-LOG.md` | `creative-deliver` | Delivery history + revision log |
| `AD-NOTES-[Name].md` | `/creative inspect` | Art direction notes on existing design |

---

## Integrations

| Tool | Used for |
|------|---------|
| **Canva MCP** | Design creation, editing, export, asset upload |
| **FLUX (HuggingFace MCP)** | Custom image generation for campaign assets |
| **Gmail MCP** | Email composition and delivery |
| **WebSearch / WebFetch** | Visual landscape research, competitor analysis |
| **BRAND-VOICE.md** (from `/market brand`) | Tone alignment in copy elements |
| **SOCIAL-CALENDAR.md** (from `/market social`) | Visual direction aligned to campaign calendar |

---

## Installation

Copy the skill folders into your Claude Code skills directory:

```
~/.claude/skills/
├── creative/
│   └── SKILL.md
├── creative-brief/
│   └── SKILL.md
├── creative-design/
│   └── SKILL.md
└── creative-deliver/
    └── SKILL.md
```

Skills are auto-discovered by Claude Code on next session start.

**Prerequisites:**
- Claude Code with Canva MCP configured
- Claude Code with HuggingFace MCP configured (for FLUX image generation)
- Claude Code with Gmail MCP configured (for email delivery)

---

## Design Principles

The orchestrator enforces these across all phases:

1. **Concept First** — One organising idea, expressible in one sentence
2. **Hierarchy is Clarity** — First read → second read → detail. Never compete
3. **Color with Intent** — Every palette choice earns its place
4. **Typography as Voice** — Font selection is tone of voice made visible
5. **White Space is Power** — Negative space is active design
6. **Consistency Builds Trust** — The system must hold across formats
7. **Context is Everything** — Design for where it will be seen, at what size, by whom

---

## Format Reference

| Format | Dimensions | Platform |
|--------|-----------|----------|
| Instagram Feed | 1080 × 1080 | Instagram |
| Instagram Portrait | 1080 × 1350 | Instagram |
| Instagram Stories | 1080 × 1920 | Instagram |
| Facebook Post | 1200 × 630 | Facebook |
| LinkedIn Post | 1200 × 628 | LinkedIn |
| Twitter/X Post | 1200 × 675 | X |
| Pinterest | 1000 × 1500 | Pinterest |
| YouTube Thumbnail | 1280 × 720 | YouTube |
| Presentation | 1920 × 1080 | Slides |
| A4 Portrait | 2480 × 3508 | Print |

---

*Built for [Claude Code](https://claude.ai/claude-code) — AI-powered CLI for software and creative workflows.*
