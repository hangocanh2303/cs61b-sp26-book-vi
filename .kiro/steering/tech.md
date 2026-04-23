# Tech Stack

## Platform
- GitBook — content authoring and publishing platform
- Git — version control
- Markdown — all content is `.md` files

## Languages in Content
- Java — all code examples and exercises are Java
- No build system, package manager, or CI pipeline — this is a pure documentation/content repository

## Assets
- Images stored in `.gitbook/assets/` (PNG, SVG, JPG)
- Images referenced from markdown using GitBook-style relative paths

## Key Files
- `SUMMARY.md` — GitBook table of contents; defines chapter ordering and navigation structure
- `README.md` — Book landing page
- `disclaimer.md` — Construction notice

## Common Tasks
- Adding/editing content: Edit the relevant `.md` file directly
- Adding a new chapter: Create the folder/files and add entries to `SUMMARY.md`
- Adding images: Place in `.gitbook/assets/` and reference from markdown
