# Foundation Demo

Persistent live demo and canary consumer for the Laptop Club Foundation framework.

- Framework: https://github.com/laptopclub/foundation
- Production site: https://foundation-gold.vercel.app
- Hosted Studio: https://foundation-demo.sanity.studio

## Setup

A GitHub token with `read:packages` access is required. Authenticate once through npm without committing the token:

```bash
npm login --scope=@laptopclub --auth-type=legacy --registry=https://npm.pkg.github.com
pnpm install
cp .env.example .env.local
pnpm dev
```

Use your GitHub username and package token when prompted. Vercel stores the token as `NPM_TOKEN` and runs `scripts/vercel-install.mjs` during installation.

Open:

- Site: http://localhost:3333
- Embedded Studio: http://localhost:3333/studio

Sanity Presentation requires `SANITY_API_READ_TOKEN` in `.env.local`. Without it, `/api/draft-mode/enable` cannot validate the Presentation secret and the preview iframe will report that `@sanity/visual-editing` is not set up.

## Validation

```bash
pnpm check
pnpm build
```

## Framework upgrades

Foundation packages are installed from GitHub Packages under the `@laptopclub` scope. Upgrade them together so CMS schemas and frontend renderers remain compatible. Validate upgrades through a Vercel preview before merging to `main`.

Site-specific schemas are composed in `sanity/schema-types.ts`. Site-specific renderers are composed in `lib/blocks.ts`. Reusable changes belong in `laptopclub/foundation` rather than this repository.

Dependabot checks for Foundation package updates every Monday. Compatible package updates are grouped into one pull request, which must pass CI and receive a Vercel preview review before merging. Major updates remain separate and require explicit migration review.
