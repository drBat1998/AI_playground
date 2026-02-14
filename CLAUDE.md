# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

This is a personal knowledge management (PKM) vault used with Obsidian and Logseq. It follows the Zettelkasten (atomic notes) methodology for a neuroscience research context. There is no software build system, test suite, or linting — all content is Markdown.

## Vault Structure

- `0 - Intro/` — Introductory notes and research materials
- `1-Fleeting_notes/` — Quick capture notes (tagged `#fleeting_note`)
- `2-Reading_notes/` — Notes extracted from papers, books, videos
- `3-Atomic_notes/` — Permanent one-concept-per-note entries (tagged `#atomic_note`)
- `5-Output/` — Written outputs: articles, IELTS practice, mini essays
- `6-Primary_Sources/` — Source materials (YouTube notes, Zotero imports)
- `7-Canvas/` — Obsidian Canvas files for visual knowledge mapping
- `Figure/` — Research figures/images organized by citation
- `LAB/` — Lab protocols, journals, and research data
- `Template/` — Reusable note templates

## Knowledge Flow

Information moves through a pipeline: **Fleeting notes** (quick capture) → **Reading notes** (extracted from sources) → **Atomic notes** (permanent, single-concept) → **Canvas** (visual relationships) → **Output** (essays, articles).

## Note Conventions

All notes use YAML frontmatter with `adding data` and `retrieval data` date fields.

**Atomic notes** (`Template/Atomic note.md`): Title, `#atomic_note` tag, `# Notes` section, `# Links` section.

**Reading notes** (`Template/Reading_notes.md`): Title, tags, `# Notes`, `# Summary`, `# Links` sections.

**Question/fleeting notes** (`Template/Question.md`): Title, `#fleeting_note` tag, callout blocks for questions and ideas.

**YouTube notes** (`Template/YouTube.md`): Title, Author (as wiki-link), tags, `# Notes`, `# Links`.

**Zotero imports** (`Template/zotero.md`): Auto-populated from Zotero with bibliography, abstract, and highlighted annotations using Jinja2 templating.

**Essay training** (`Template/Essay training.md`): Structured outline (hook → thesis → 3 body paragraphs → conclusion), with sections for new words, spelling, essay text, and GPT correction.

## Cross-Linking

Notes are connected via Obsidian `[[wiki-links]]`. The graph view and backlinks panel are used to discover relationships. When creating or editing notes, maintain cross-links in the `# Links` section.

## Research Domain

The vault centers on neuroscience research: neuroprotective effects of microbiome metabolites during oxygen-glucose deprivation (OGD), necroptosis, apoptosis, pyroptosis, cell death mechanisms, and the microbiome-brain axis. Lab methods include cell culture, LDH/MTT assays, immunohistochemistry, Western blotting, and qPCR.

## Writing Style

Essays follow these rules: one point per essay, 300 words minimum, explain complex topics simply, nonfiction style preferred.
