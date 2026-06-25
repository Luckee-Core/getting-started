# Luckee — getting started

This repo is the **map** — not an app. It shows how **Luckee Core** (hosted), **open-source studios**, **Luckee Blueprints**, and the **Installer Network** fit together. To self-host studios, start with **[Luckee Dev Hub](#start-here-self-host)**; use this README as the catalog reference.

> **GitHub org for links below:** `Luckee-Core`  
> If your public repos live under a different org, change that string once and replace the `github.com/Luckee-Core/` URLs.

---

## How the pieces fit

Same story as **[luckee-marketing](https://github.com/Luckee-Core/luckee-marketing)**: your data, your workflows — with a hosted path *or* a self-host path when you want to run the stack yourself.

| # | Piece | What it is |
| --- | --- | --- |
| **01** | **Luckee Core** | Paid, hosted SaaS — we run it; you run the business. One workspace for service businesses (leads, jobs/projects, customers, AI-native workflows). Hosted on Supabase, Vercel, and Railway. Product repos: [`luckee-web`](https://github.com/Luckee-Core/luckee-web), [`luckee-central`](https://github.com/Luckee-Core/luckee-central). |
| **02** | **Open-source studios** | Same architecture and quality bar as Core, split into **repos you can self-host** — mostly **Next.js** frontends and **Express** APIs. Adopt **one studio at a time**. **This README is the map for that path.** |
| **03** | **Luckee Installer Network** | On-site **AI infrastructure** delivery (hardware through handoff). Installer verification ties to **Luckee Blueprints** certifications; Luckee routes qualified installation work. |
| — | **Luckee Blueprints** | **Train the workforce** — published tracks, certifications, DIY path alongside Core. App: [`luckee-blueprints`](https://github.com/Luckee-Core/luckee-blueprints) (+ [`luckee-blueprints-express-server`](https://github.com/Luckee-Core/luckee-blueprints-express-server) when you wire the API). |

**Short version:** on-premise AI infrastructure — **your data, your workflows** — with premium build support, the Installer Network for physical install, and a **free DIY** lane through **Blueprints + open source**.

---

## Start here (self-host)

**Luckee Dev Hub** is the recommended entry point for running open-source studios locally. Clone and start the hub first; use it to discover studios, copy `git clone` commands, wire local paths, and run dev servers.

**Canonical hub docs:** [`mentorai-server/data/how-to/central-hub/`](https://github.com/trouthouse-tech/mentorai-server/tree/main/data/how-to/central-hub) — project registry/ports, `hub.local.json`, probes, Run, local database, terminals.

| Repo | Role |
| --- | --- |
| [`luckee-hub`](https://github.com/Luckee-Core/luckee-hub) | Next.js UI (:4100) — `/projects` list + project detail |
| [`luckee-hub-express-server`](https://github.com/Luckee-Core/luckee-hub-express-server) | Local API + launcher (:4110, `127.0.0.1` only) |

```bash
git clone https://github.com/Luckee-Core/luckee-hub-express-server.git
git clone https://github.com/Luckee-Core/luckee-hub.git
cd luckee-hub-express-server && cp hub.local.json.example hub.local.json
# Edit hub.local.json → projects — see central-hub/hub-local-config.md
zsh luckee-hub/scripts/start-luckee-hub-dev.sh
```

**Workflow:**

1. Open [http://localhost:4100/projects](http://localhost:4100/projects).
2. Click a studio → project detail → **copy `git clone` commands** for Web and API repos.
3. Clone repos locally; add `webDir` / `expressDir` in `hub.local.json` (see `hub.local.json.example`).
4. **Refresh** projects in hub — status moves from Available → Configured.
5. **Run** from hub; finish setup in each studio repo (`README.md`, `.env.example`, SQL migrations).

Embedded terminal dock is on the **right**; **Run** spawns in-browser PTYs. **My Health local Postgres:** Projects → My Health → **Setup database** ([local-database-setup.md](https://github.com/trouthouse-tech/mentorai-server/blob/main/data/how-to/central-hub/local-database-setup.md)).

---

## Open-source studios (catalog)

Reference index of studios registered in **Luckee Dev Hub → Projects**. Each **studio** is typically a **Web** repo (Next.js) and an **API** repo (Express). Use `—` when that side is not a separate public repo.

Studios share the same backbone — **Next.js + Express + Supabase** — with env, SQL, and platform-token setup documented in **each repo**. The hub gets you cloned, configured, and running locally; repo docs cover production hardening.

| Studio | What it is | Web | API |
| --- | --- | --- | --- |
| **Luckee Open Source** | Lead / ops CRM-style modular dashboard (Luckee OSS surface) | [`luckee-open-source`](https://github.com/Luckee-Core/luckee-open-source) | [`luckee-open-source-express`](https://github.com/Luckee-Core/luckee-open-source-express) |
| **Luckee Blueprints** | Workforce training, certifications, delivery shell | [`luckee-blueprints`](https://github.com/Luckee-Core/luckee-blueprints) | [`luckee-blueprints-express-server`](https://github.com/Luckee-Core/luckee-blueprints-express-server) |
| **Lead Studio** | Lead CRM, research workers, email queue — reference self-hosted pair | [`lead-studio-web-open-source`](https://github.com/Luckee-Core/lead-studio-web-open-source) | [`lead-studio-express-server`](https://github.com/Luckee-Core/lead-studio-express-server) |
| **My Health** | Self-hosted appointments, care team, focus areas, and daily notes — personal health dashboard | [`my-health-open-source`](https://github.com/Luckee-Core/my-health-open-source) | [`my-health-open-source-express-server`](https://github.com/Luckee-Core/my-health-open-source-express-server) |
| **My Fundraise** | Fundraise CRM — investors pipeline, graphics studio (TSX preview + PNG export), pitch deck slide coach | [`my-fundraise-web`](https://github.com/Luckee-Core/my-fundraise-web) | [`my-fundraise-express-server`](https://github.com/Luckee-Core/my-fundraise-express-server) |
| **Personal Finances** | Self-hosted money dashboard — CSV imports, your AI prompts for categorization, recurring bills and loans | [`personal-finances`](https://github.com/Luckee-Core/personal-finances) | [`personal-finances-express-server`](https://github.com/Luckee-Core/personal-finances-express-server) |
| **Knowledge Studio** | YouTube / knowledge workflows | [`knowledge-studio-open-source`](https://github.com/Luckee-Core/knowledge-studio-open-source) | [`knowledge-studio-express-server`](https://github.com/Luckee-Core/knowledge-studio-express-server) |
| **Blog Studio** | Blog authoring and distribution | [`blog-studio-open-source-web`](https://github.com/Luckee-Core/blog-studio-open-source-web) | [`blog-studio-open-source-express-server`](https://github.com/Luckee-Core/blog-studio-open-source-express-server) |
| **Code Control** | Standalone project workspace — schema, conventions, and guided codegen into customer repos | [`code-control`](https://github.com/Luckee-Core/code-control) | [`code-control-express-server`](https://github.com/Luckee-Core/code-control-express-server) |
| **Code Your Resume** | Job-search CRM, resume graphics studio (TSX preview), skills/background/job studios | [`code-your-resume-open-source`](https://github.com/Luckee-Core/code-your-resume-open-source) | [`code-your-resume-open-source-express-server`](https://github.com/Luckee-Core/code-your-resume-open-source-express-server) |
| **Instagram Studio** | Blog → AI carousel graphics (TSX preview) and Instagram Graph publishing | [`instagram-studio-open-source`](https://github.com/Luckee-Core/instagram-studio-open-source) | [`instagram-studio-open-source-express-server`](https://github.com/Luckee-Core/instagram-studio-open-source-express-server) |
| **TikTok Studio** | Blog → AI carousel graphics (TSX preview) and TikTok content publishing | [`tiktok-studio`](https://github.com/Luckee-Core/tiktok-studio) | [`tiktok-studio-express-server`](https://github.com/Luckee-Core/tiktok-studio-express-server) |
| **QR Code Generator** | QR generation API / utilities | — | [`qr-code-generator-open-source-express-server`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server) |

Long-form docs on the marketing deploy live under **`/docs/open-source`** (e.g. **`/docs/open-source/knowledge-studio`**). Repo: [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing).

---

## Optional: clone this map

Clone this repo to browse the studio catalog offline or contribute index fixes — it is **not** required to run studios (start with **Luckee Dev Hub** above).

```bash
git clone https://github.com/Luckee-Core/getting-started.git
cd getting-started
```

### Lead Studio (web + API)

Good starting point if outbound leads still live in Maps tabs and spreadsheets. Self-host the pair for find-leads (maps), lead-detail research, and outbound email.

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/lead-studio-web-open-source](https://github.com/Luckee-Core/lead-studio-web-open-source) |
| API (Express) | [github.com/Luckee-Core/lead-studio-express-server](https://github.com/Luckee-Core/lead-studio-express-server) |

```bash
git clone https://github.com/Luckee-Core/lead-studio-express-server.git
git clone https://github.com/Luckee-Core/lead-studio-web-open-source.git
```

1. **Supabase** — run SQL in order from `lead-studio-express-server/sql/README.md`.
2. **Express** — `cp .env.example .env`, fill `SUPABASE_*` and `ANTHROPIC_API_KEY`, `npm run dev` (port **3032**).
3. **Web** — `cp .env.example .env.local`, set `NEXT_PUBLIC_SERVER_URL=http://localhost:3032`, `npm run dev`.
4. Open [http://localhost:3000/setup](http://localhost:3000/setup) for the first-run wizard, then `/dashboard`.

Full walkthrough: [`lead-studio-express-server/docs/oss-quickstart.md`](https://github.com/Luckee-Core/lead-studio-express-server/blob/main/docs/oss-quickstart.md). OSS governance (checklists, wire contract): [`mentorai-server/data/open-source/`](https://github.com/trouthouse-tech/mentorai-server/tree/main/data/open-source).

### My Health (web + API)

Self-host a dashboard for visits, doctors linked to facilities and specialties, and daily notes — without portal printouts scattered across three apps. Good if you want the same Next.js + Express + Supabase split on a **personal** data slice (not a CRM).

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/my-health-open-source](https://github.com/Luckee-Core/my-health-open-source) |
| API (Express) | [github.com/Luckee-Core/my-health-open-source-express-server](https://github.com/Luckee-Core/my-health-open-source-express-server) |

```bash
git clone https://github.com/Luckee-Core/my-health-open-source-express-server.git
git clone https://github.com/Luckee-Core/my-health-open-source.git
```

1. **Supabase** — run SQL in order from `my-health-open-source-express-server/docs/supabase/` (`001_…` then `002_…`).
2. **Express** — `cp .env.example .env`, fill `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY`, `npm run dev` (port **3009**).
3. **Web** — `cp .env.example .env.local`, set `NEXT_PUBLIC_API_URL=http://localhost:3009`, `npm run dev`.
4. Open [http://localhost:3000](http://localhost:3000) for the landing page; dashboard routes under `/appointments`, `/doctors`, `/hospitals`, `/specialties`, `/focus-areas`, `/daily-entries`.

Wire contract and env tables: [`my-health-open-source-express-server/docs/oss/wire-contract.md`](https://github.com/Luckee-Core/my-health-open-source-express-server/blob/main/docs/oss/wire-contract.md). v1 is **local/trusted-network** — no API auth until you harden for production ([`SECURITY.md`](https://github.com/Luckee-Core/my-health-open-source-express-server/blob/main/SECURITY.md)).

### My Fundraise (web + API)

Self-host a fundraise CRM when investor outreach, deck graphics, and slide copy still live in scattered docs and Figma. Track investors and contacts, run AI paste-import for firm profiles, edit carousel graphics in a TSX studio with live preview, and coach intro-deck slides with per-slide AI chat — same Next.js + Express + Supabase split as the other studios.

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/my-fundraise-web](https://github.com/Luckee-Core/my-fundraise-web) |
| API (Express) | [github.com/Luckee-Core/my-fundraise-express-server](https://github.com/Luckee-Core/my-fundraise-express-server) |

```bash
git clone https://github.com/Luckee-Core/my-fundraise-express-server.git
git clone https://github.com/Luckee-Core/my-fundraise-web.git
```

1. **Supabase** — run SQL in order from `my-fundraise-express-server/docs/sql/` (`001_…` through `004_…`).
2. **Express** — `cp .env.example .env`, fill `SUPABASE_URL`, `SUPABASE_SERVICE_ROLE_KEY`, and `ANTHROPIC_API_KEY`, `npm run dev` (port **3090** when launched from Luckee Dev Hub; repo default is **3009** if you run standalone).
3. **Web** — `cp .env.example .env.local`, set `NEXT_PUBLIC_API_URL` to your Express URL (e.g. `http://localhost:3090`), set `NEXT_PUBLIC_DEV_USER_ID` for AI endpoints, `npm run dev`.
4. Open [http://localhost:3000](http://localhost:3000) — redirects to **`/investors`**; sidebar also lists **Graphics** and **Pitch Decks**.

Optional: `CURSOR_API_KEY` + `CURSOR_TARGET_REPO` on Express for graphics TSX generation. Graphics preview pipeline: `my-fundraise-express-server/data/how-to/graphics-tsx-preview.md`.

### Personal Finances (web + API)

Self-host a money dashboard when statements still live in spreadsheets and you re-fix the same categories every month. Import bank and credit CSVs, version your own AI prompts (slug assign, category assign, recurring detect), and track recurring bills, anticipated costs, and loans — same Next.js + Express + Supabase split as the other studios.

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/personal-finances](https://github.com/Luckee-Core/personal-finances) |
| API (Express) | [github.com/Luckee-Core/personal-finances-express-server](https://github.com/Luckee-Core/personal-finances-express-server) |

```bash
git clone https://github.com/Luckee-Core/personal-finances-express-server.git
git clone https://github.com/Luckee-Core/personal-finances.git
```

1. **Supabase** — run SQL in order from [`personal-finances-express-server/docs/database-setup.md`](https://github.com/Luckee-Core/personal-finances-express-server/blob/main/docs/database-setup.md) (`001_…` through `018_…`; skip `002_…` on a fresh install).
2. **Express** — `cp .env.example .env`, fill `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` (optional `ANTHROPIC_API_KEY` for AI), `npm run dev` (port **3011**).
3. **Web** — `cp .env.example .env.local`, set `NEXT_PUBLIC_SERVER_URL=http://localhost:3011`, `npm run dev`.
4. Open [http://localhost:3000](http://localhost:3000) for the landing page; dashboard at **`/dashboard`**.

Full walkthrough and wire contract: [`personal-finances-express-server/docs/oss-quickstart.md`](https://github.com/Luckee-Core/personal-finances-express-server/blob/main/docs/oss-quickstart.md). v1 is **local/trusted-operator** — no API auth until you harden for production ([`SECURITY.md`](https://github.com/Luckee-Core/personal-finances-express-server/blob/main/SECURITY.md)). Built by Matt @ [TroutHouseTech](https://www.trouthousetech.com).

### Code Your Resume (web + API)

Self-host a job-search CRM with companies, jobs, applications, and resume studios — graphics (TSX live preview), technical skills, professional background, and per-job coach chat. Same Next.js rewrites + Express + Supabase split; web calls same-origin `/api/data/*` proxied to Express on port **3053**.

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/code-your-resume-open-source](https://github.com/Luckee-Core/code-your-resume-open-source) |
| API (Express) | [github.com/Luckee-Core/code-your-resume-open-source-express-server](https://github.com/Luckee-Core/code-your-resume-open-source-express-server) |

```bash
git clone https://github.com/Luckee-Core/code-your-resume-open-source-express-server.git
git clone https://github.com/Luckee-Core/code-your-resume-open-source.git
```

1. **Supabase** — run SQL in order from [`code-your-resume-open-source-express-server/docs/`](https://github.com/Luckee-Core/code-your-resume-open-source-express-server/tree/main/docs) (`crm-postgres-schema.sql`, then image graphics, error log, and optional studio schemas — see web [`docs/wire-contract.md`](https://github.com/Luckee-Core/code-your-resume-open-source/blob/main/docs/wire-contract.md)).
2. **Express** — `cp .env.example .env`, fill `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY`, `npm run dev` (port **3053**).
3. **Web** — `cp .env.example .env.local`, `npm run dev` (Express rewrites default to `http://127.0.0.1:3053` in dev).
4. Open [http://localhost:3000](http://localhost:3000) (marketing) or [http://localhost:3000/dashboard](http://localhost:3000/dashboard) (app).

Wire contract: [`code-your-resume-open-source/docs/wire-contract.md`](https://github.com/Luckee-Core/code-your-resume-open-source/blob/main/docs/wire-contract.md). OSS governance: [`mentorai-server/data/open-source/`](https://github.com/trouthouse-tech/mentorai-server/tree/main/data/open-source). v1 is **local/trusted-operator** — optional `CRM_API_SECRET`; see [`SECURITY.md`](https://github.com/Luckee-Core/code-your-resume-open-source/blob/main/SECURITY.md) on both repos.

### Code Control (web + API)

Standalone project workspace for TroutHouseTech — define schema, conventions, and drive guided codegen (ARD, data model, CRUD API) into customer repos. Same Next.js + Express + Supabase split as the other studios.

| Repo | URL |
| --- | --- |
| Web (Next.js) | [github.com/Luckee-Core/code-control](https://github.com/Luckee-Core/code-control) |
| API (Express) | [github.com/Luckee-Core/code-control-express-server](https://github.com/Luckee-Core/code-control-express-server) |

```bash
git clone https://github.com/Luckee-Core/code-control-express-server.git
git clone https://github.com/Luckee-Core/code-control.git
```

1. **Supabase** — run migrations from `code-control-express-server/src/db/migrations/` against a dedicated project.
2. **Express** — `cp .env.example .env`, fill `SUPABASE_*`, `CURSOR_*`, and `GITHUB_*` keys, `npm run dev` (port **3010**; hub assigns **3074** when launched from Luckee Dev Hub).
3. **Web** — `cp .env.example .env`, set `NEXT_PUBLIC_CODE_CONTROL_API_URL=http://localhost:3010` (or hub API port), `npm run dev`.
4. Open [http://localhost:3000/projects](http://localhost:3000/projects) for the project workspace.

Architecture ADRs: `.cursor/architecture/` in each repo. THT panel links here via `NEXT_PUBLIC_CODE_CONTROL_URL`.

### QR Code Generator (API only)

Stateless Express API — POST an HTTP(S) URL, get a PNG QR code. No web companion repo and no database for the OSS default.

| Repo | URL |
| --- | --- |
| API (Express) | [github.com/Luckee-Core/qr-code-generator-open-source-express-server](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server) |

```bash
git clone https://github.com/Luckee-Core/qr-code-generator-open-source-express-server.git
cd qr-code-generator-open-source-express-server
```

1. **Express** — `cp .env.example .env`, `npm install`, `npm run dev` (port **3023**).
2. Open [http://localhost:3023/docs](http://localhost:3023/docs) for the API reference, or [http://localhost:3023/api/health](http://localhost:3023/api/health) for a health check.
3. Generate a QR code: `POST http://localhost:3023/api/generate-code` with JSON body `{ "url": "https://example.com" }` → PNG bytes.

OSS governance: [`mentorai-server/data/open-source/`](https://github.com/trouthouse-tech/mentorai-server/tree/main/data/open-source). Release status: [`docs/oss-release-status.md`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server/blob/main/docs/oss-release-status.md). v1 is **local/trusted-network** — no API auth until you harden for production ([`SECURITY.md`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server/blob/main/SECURITY.md), [`docs/production-hardening.md`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server/blob/main/docs/production-hardening.md)).

---

## Add a new studio (maintainers)

Keep the **catalog table** as the single source of truth. To add a studio:

1. **Add one row** to [Open-source studios (catalog)](#open-source-studios-catalog) above.
2. **Register in Luckee Dev Hub** — add matching entries to `luckee-hub/src/config/hub-catalog.ts` and `luckee-hub-express-server/data/projects.registry.json` (unique ports), plus `hub.local.json.example`.
3. **Sort** rows alphabetically by the **Studio** column (first word), unless you intentionally group “Luckee *” first — keep Luckee-branded rows together at the top and sort the rest A–Z.
4. **Link shape:** `https://github.com/<ORG>/<repo>` with the same `<ORG>` as the callout at the top of this file.
5. **Optional docs:** add or link a page from [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing) under `/docs/open-source/…` and, if the studio has a **Data** section, under `/docs/data/…` (see `src/config/routes.ts` in marketing for path conventions).
6. **Marketing home (optional):** if the studio is flagship-level, consider a callout in `src/packages/landing/open-source/` — otherwise the table here + docs is enough.

**Copy-paste row template** (replace placeholders; delete API cell or use `—`):

```markdown
| **{Studio name}** | {One sentence: who it is for and what it does.} | [`{web-repo}`](https://github.com/Luckee-Core/{web-repo}) | [`{api-repo}`](https://github.com/Luckee-Core/{api-repo}) |
```

**API-only or web-only template:**

```markdown
| **{Studio name}** | {One sentence.} | — | [`{api-repo}`](https://github.com/Luckee-Core/{api-repo}) |
```

```markdown
| **{Studio name}** | {One sentence.} | [`{web-repo}`](https://github.com/Luckee-Core/{web-repo}) | — |
```

---

## Related repos (not a “studio” row)

| Repo | Role |
| --- | --- |
| [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing) | Public marketing + docs site |
| [`luckee-marketing-express-server`](https://github.com/Luckee-Core/luckee-marketing-express-server) | Marketing APIs (signup, analytics, public blog API, etc.) |

---

## Frequent technologies

Same backbone across most studios:

`TypeScript` `React` `Next.js` `Redux Toolkit` `Tailwind` `Express` `Supabase` `Docker` `Node`

---

## Roadmap for *this* repo

- [ ] Per-studio **one-screen** diagram (Web ↔ API ↔ DB).
- [ ] **Docker Compose** snippets for common **Web + API** pairs.
- [ ] **Version matrix** (which API tag matches which web tag) per studio.

**Issues:** use **this** repo for the index, wrong links, and cross-studio compose/docs; use each **studio** repo for product bugs and features (studio name in the title).

---

## Contact

For a given app, open issues on **that studio’s repo** (include repro, env, and web/API commit or tag). For **this map**, open an issue here in **getting-started**.
