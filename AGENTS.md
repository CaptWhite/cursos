## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Architecture

This is an Astro static site that renders course documentation from Markdown.

**Key files:**
- `src/docMapping.ts` — **Must be updated** when adding new docs. Maps filenames to slugs, menu tabs, chapter numbers, and descriptions. Controls both navigation and URL routing.
- `src/content.config.ts` — Glob pattern loads all `*.md` from `src/content/docs/`
- `src/pages/[...slug].astro` — Dynamic route that renders docs via `docMapping`
- `src/layouts/DocsLayout.astro` — Single layout with sidebar, tabs, and global styles

**Content structure:**
- Docs live in `src/content/docs/{Cursos,IA,Tab3,Tab4,Tab5,Tab6}/` subdirectories
- Frontmatter (`title`, `description`) is optional
- Site language is Spanish (`lang="es"`)

## Adding a new document

1. Create the `.md` file in the appropriate subdirectory under `src/content/docs/`
2. Add an entry to `src/docMapping.ts` with: `filename`, `menutab`, `id`, `slug`, `description`, `chapter`
3. The `id` must match the filename without extension; the `slug` becomes the URL path

## Math and diagrams

- Math uses `$$` syntax via `remark-math` + `rehype-katex` (configured in `astro.config.mjs`)
- KaTeX CSS is loaded from CDN in `DocsLayout.astro`
- Mermaid diagrams render client-side — use fenced code blocks with ` ```mermaid `

## Preprocessing

Run `node scripts/preprocess-docs.js` to normalize math formulas in the `Apéndices` folder (converts single-line `$$` to multi-line blocks).

## Deployment

- **Docker**: Multi-stage build (`node:22-alpine` → `serve dist -l 4321`)
- **CI/CD**: GitHub Actions pushes `captwhite/cursos:latest` to Docker Hub on push to `main`
- **Production**: Deploys to VPS via SSH, served behind Traefik reverse proxy at `cursos.captwhite.com`
- **Node requirement**: `>=22.12.0`

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
