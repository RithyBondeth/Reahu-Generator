<div align="center">

<img src="./public/og-templates.png" alt="Reahu Generator — complete GitHub profile README templates" width="100%">

# Reahu Generator

**Build your GitHub profile README with drag-and-drop blocks, live preview, and shareable links. No backend and no account required.**

[![Live Demo](https://img.shields.io/badge/Live_demo-C5F74F?style=for-the-badge&labelColor=111111&color=C5F74F)](https://reahu-generator.vercel.app)
[![Open Builder](https://img.shields.io/badge/Open_builder-ffffff?style=for-the-badge&labelColor=111111&color=ffffff)](https://reahu-generator.vercel.app/build)

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Nuxt](https://img.shields.io/badge/Nuxt-00DC82?style=for-the-badge&logo=nuxtdotjs&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vitest](https://img.shields.io/badge/Vitest-6E9F18?style=for-the-badge&logo=vitest&logoColor=white)

</div>

---

![Reahu Generator landing page showing the block-based profile builder](./public/screenshots/reahu-landing.jpg)

## Overview

Great profile READMEs are memorable, but building one usually means copying snippets, fixing broken image URLs, and repeatedly checking GitHub to see how everything renders. Reahu Generator turns that into a visual workflow:

1. Pick a template, or start from a sensible default.
2. Add and arrange the blocks that tell your story.
3. Edit on the left while the GitHub-style preview updates on the right.
4. Copy, share, or download the finished Markdown.

Everything runs in your browser. There is no account, database, or backend, and your draft stays on your device.

## Features

- **17 focused blocks:** headers, animated banners, typing text, about, quote, table, divider, custom Markdown, tech stacks, stats, activity graphs, trophies, pinned repositories, socials, sponsors, and more.
- **12 complete templates** for different developer profiles and specialties.
- **Live GitHub-style preview** in light and dark themes.
- **Drag-and-drop composition:** reorder, duplicate, edit, or remove any section.
- **Undo, redo, and autosave.**
- **Shareable links:** the document is compressed into the URL, so nothing is stored on a server.
- **Markdown export:** copy the source or download a ready-to-commit `README.md`.
- **Large libraries:** about 200 tech icons, 50 social platforms, and around 70 themes for compatible GitHub cards.

![Reahu Generator builder with editable blocks and a live GitHub-style preview](./public/screenshots/reahu-builder.jpg)

## Tech Stack

| Area | Technology |
| --- | --- |
| Framework | Nuxt 4, Vue 3 |
| Language | TypeScript |
| UI | Nuxt UI, Tailwind CSS 4, Iconify (Lucide, Simple Icons) |
| Editing | vue-draggable-plus, VueUse |
| Rendering | markdown-it, DOMPurify, lz-string |
| Quality | Vitest, ESLint, vue-tsc, GitHub Actions, Renovate |

## Getting Started

### Prerequisites

- Node.js 20 or newer
- npm

### Installation

```bash
git clone https://github.com/RithyBondeth/Reahu-Generator.git
cd Reahu-Generator
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000). The builder is at [http://localhost:3000/build](http://localhost:3000/build).

### Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the development server |
| `npm run build` | Create a production build in `.output/` |
| `npm run preview` | Preview the production build |
| `npm run lint` | Run ESLint |
| `npm run typecheck` | Run Nuxt and Vue type checks |
| `npm test` | Run the document and renderer regression tests |

## How It Works

A Reahu document is an ordered array of typed blocks. A small, framework-independent pipeline renders that array into Markdown. The core renderers and configuration never import Vue, so the Markdown output can be tested on its own.

### Adding a New Block

1. Add the block's props to `app/types/block.ts`.
2. Create and register a renderer in `app/core/render/`.
3. Add its label, category, icon, and defaults in `app/core/blocks/definitions.ts`.
4. Build the matching editor in `app/components/blocks/editors/`.

Type-checking fails if a block is missing from the renderer registry or the block palette.

## Project Structure

```text
Reahu-Generator/
├── app/
│   ├── components/     # Block list and editors, landing sections, README preview
│   ├── composables/    # Document state, persistence, undo and redo
│   ├── config/         # Icons, services, themes, platforms, UI options
│   ├── core/
│   │   ├── blocks/     # Definitions, defaults, factories
│   │   ├── document/   # Local storage, sharing, download helpers
│   │   ├── render/     # Pure block-to-Markdown renderers
│   │   └── templates/  # Ready-made profile documents
│   ├── pages/          # Landing page, templates, builder
│   └── types/          # Shared TypeScript types
├── server/             # Sitemap, robots, social-proof endpoint
└── test/               # Vitest regression tests
```

## Deployment

Reahu works on Vercel, Netlify, Cloudflare Pages, and other Nuxt-compatible hosts. Run `npm run build` and deploy the `.output/` directory. Public pages and the template gallery are prerendered, while `/build` stays client-side.

## Privacy

Drafts are never sent to a backend. Local drafts live in `localStorage`, and shared documents are compressed into the URL fragment. Some blocks load public images from third-party services such as Shields.io, Skill Icons, and GitHub Readme Stats. Those hosts are centralized in `app/config/services.ts`, so they are easy to replace or self-host.

## Author

**Rithy Bondeth** — Full Stack Developer & AI Engineer

[![Portfolio](https://img.shields.io/badge/Portfolio-0A0A0A?style=for-the-badge&logo=vercel&logoColor=white)](https://bondeth.dev)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/RithyBondeth)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rithy-bondeth-484073282/)

## License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.
