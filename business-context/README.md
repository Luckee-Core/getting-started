# Luckee Business Context

Portable schema for storing **what is** about your business — atomic facts organized in sections. Used for AI prompt injection at action time (not chat).

## Tables

See [sql/006_business_context.sql](./sql/006_business_context.sql):

- **`business_context_sections`** — organizational buckets (Identity, ICP, Product, …). You can add sections.
- **`business_facts`** — one row per atomic claim; each fact belongs to one section.

## API (my-fundraise-express-server)

| Method | Path | Purpose |
|--------|------|---------|
| GET | `/api/data/business-context-sections?userId=` | List sections |
| POST | `/api/data/business-context-sections` | Create section |
| PATCH | `/api/data/business-context-sections/:id` | Update section |
| DELETE | `/api/data/business-context-sections/:id` | Delete section (cascades facts) |
| GET | `/api/data/business-facts?userId=&sectionId=` | List facts |
| POST | `/api/data/business-facts` | Upsert fact |
| DELETE | `/api/data/business-facts/:id` | Delete fact |
| POST | `/api/business-context/seed-deck-e` | Seed Deck E sections + facts; optional `includePitchDeck: true` |

## Prompt injection

Load selected sections when running an AI action:

```ts
import { loadBusinessContextForPrompt } from './load-business-context-for-prompt';

const ctx = await loadBusinessContextForPrompt(supabase, {
  userId,
  sectionKeys: ['identity', 'product'],
});
// ctx.formatted → markdown block for system prompt
```

Section keys by action (defaults in my-fundraise-express-server):

| Action | Section keys |
|--------|--------------|
| Graphics generation | `identity`, `product` |
| Pitch copy / guidance | `identity`, `icp`, `problem`, `wedge`, `constraints` |

## Adopting in another studio

1. Run `sql/006_business_context.sql` on your Supabase project (or share one Supabase for facts across studios).
2. Copy `src/data/business-context-sections/` and `src/data/business-facts/` from my-fundraise-express-server.
3. Copy `src/utils/business-context/` for seed data and prompt loader.
4. Mount routers in your data router + optional `/api/business-context` service.

## Deck E seed

Default sections and atomic facts live in `deck-e-seed-data.ts` (express). Import via UI or `POST /api/business-context/seed-deck-e`.
