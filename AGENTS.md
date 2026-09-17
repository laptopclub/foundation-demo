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
