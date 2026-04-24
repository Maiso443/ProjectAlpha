# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev        # Start dev server at localhost:4321
npm run build      # Type-check and build to ./dist/
npm run preview    # Preview production build locally
npx astro check    # Run Astro type-checking
```

No test suite is configured.

## Architecture

This is an **Astro 6** blog site using the default blog starter template.

**Content layer**: Blog posts live in `src/content/blog/` as `.md` or `.mdx` files. The collection is defined in `src/content.config.ts` using Astro's glob loader. Required frontmatter fields: `title`, `description`, `pubDate`. Optional: `updatedDate`, `heroImage`.

**Routing**: `src/pages/blog/[...slug].astro` generates static pages from the blog collection — `post.id` maps directly to the URL slug. The index page at `src/pages/index.astro` and `src/pages/blog/index.astro` list posts.

**Layouts and components**: `BlogPost.astro` is the single layout for all blog posts — it assembles `BaseHead`, `Header`, `Footer`, and `FormattedDate`. Components are flat in `src/components/`; there is no component hierarchy.

**Global constants**: `src/consts.ts` exports `SITE_TITLE` and `SITE_DESCRIPTION`, used in `BaseHead` and the RSS feed.

**Integrations**: MDX (`@astrojs/mdx`) for `.mdx` posts, sitemap auto-generation (`@astrojs/sitemap`), and RSS feed at `/rss.xml`. The `site` URL in `astro.config.mjs` must be updated from `https://example.com` before deploying.

**Fonts**: Atkinson Hyperlegible served locally from `src/assets/fonts/`, exposed via CSS variable `--font-atkinson`.

**Styles**: Global styles in `src/styles/global.css`. Component-scoped styles are written inline within each `.astro` file's `<style>` block.
