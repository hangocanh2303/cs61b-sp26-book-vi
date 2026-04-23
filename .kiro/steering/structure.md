# Project Structure

## Layout

```
/                           # Root — contains single-page chapters and top-level files
├── SUMMARY.md              # GitBook TOC — defines all navigation (MUST be updated for new chapters)
├── README.md               # Book landing page
├── disclaimer.md           # Construction disclaimer
├── {N}.-{topic}.md         # Single-page chapters (English), e.g. 2.-defining-and-using-classes.md
├── {N}.-{topic}_vi.md      # Single-page chapters (Vietnamese), e.g. 2.-defining-and-using-classes_vi.md
├── {N}.-{topic}/           # Multi-page chapter folders
│   ├── README.md           # Chapter intro/landing page (English)
│   ├── {N}.{M}-{section}.md  # Section files (English)
│   └── vi/                 # Vietnamese translations subfolder
│       ├── README.md       # Chapter intro (Vietnamese)
│       └── {N}.{M}-{section}.md  # Section files (Vietnamese)
├── .gitbook/
│   └── assets/             # All images (PNG, SVG, JPG)
└── .kiro/
    └── steering/           # AI assistant steering rules
```

## Conventions

- Chapter folders use the pattern `{number}.-{kebab-case-topic}/` (e.g. `15.-bsts/`)
- Section files use `{chapter}.{section}-{kebab-case-title}.md` (e.g. `15.3-bst-operations.md`)
- Single-page chapters live at root level as `{N}.-{topic}.md`
- Vietnamese translations: for single-page chapters use `_vi` suffix; for multi-page chapters use a `vi/` subfolder mirroring the English structure
- English is the primary language; Vietnamese files mirror the English content structure exactly
- The folder `9999.-...-OLD-DO-NOT-USE/` is deprecated — do not reference or modify it
- Chapters 30–40 exist on disk but are commented out in `SUMMARY.md` (not yet published)
- Each chapter folder has a `README.md` that serves as the chapter landing page
