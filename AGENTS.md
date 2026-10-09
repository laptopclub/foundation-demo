# Foundation Demo agent guide

Foundation Demo is the persistent demonstration and canary consumer of `laptopclub/foundation`.

## Read first

- `README.md`: setup and framework upgrade workflow
- `docs/sanity-revalidation.md`: production webhook behavior
- Framework guidance: https://github.com/laptopclub/foundation/blob/main/AGENTS.md

## Boundaries

- Keep demonstration content, branding and site-specific extensions in this repository.
- Put reusable schemas, blocks, components and fixes in `laptopclub/foundation`.
- Do not copy or edit code inside installed Foundation packages.
- Add site-specific schemas in `sanity/schema-types.ts`.
- Add site-specific renderers in `lib/blocks.ts`.
- Upgrade all `@laptopclub/foundation-*` packages together unless compatibility is documented.
- Do not mutate production Sanity content unless explicitly requested.
- Never commit `.env` files, package tokens, Sanity tokens or webhook secrets.
- Do not hand-edit `sanity.types.ts` or `schema.json`.
- Do not add dependencies without explicit approval.

## Required checks

```bash
pnpm check
pnpm build
```

For schema or GROQ query changes:

```bash
pnpm sanity:schema
pnpm sanity:typegen
```

## Definition of done

- Framework changes are made upstream when reusable.
- Package installation, checks and production build pass.
- A Vercel preview is reviewed for package upgrades.
- No secrets or temporary generated files are committed.

<!-- BEGIN:nextjs-agent-rules -->

# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->
