# Luckee — getting started

This repo is the **map** — not an app. It shows how **Luckee Core** (hosted), **open-source studios**, **Luckee Blueprints**, and the **Installer Network** fit together, and links you to the repos you actually clone.

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

## Clone this map (self-host path)

Start here, then clone only the studio you need:

```bash
git clone https://github.com/Luckee-Core/getting-started.git
cd getting-started
# Read the studio table below; clone the web (and API if listed) for the studio you need.
```

Long-form docs on the marketing deploy live under **`/docs/open-source`** (and nested routes such as **`/docs/open-source/knowledge-studio`**). Repo: [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing).

---

## Open-source studios (catalog)

Each **studio** is a product-shaped slice: typically a **Web** repo (Next.js) and sometimes an **API** repo (Express). Use `—` when that side is not a separate public repo for this OSS slice.

| Studio | What it is | Web | API |
| --- | --- | --- | --- |
| **Luckee Open Source** | Lead / ops CRM-style modular dashboard (Luckee OSS surface) | [`luckee-open-source`](https://github.com/Luckee-Core/luckee-open-source) | [`luckee-open-source-express`](https://github.com/Luckee-Core/luckee-open-source-express) |
| **Luckee Blueprints** | Workforce training, certifications, delivery shell | [`luckee-blueprints`](https://github.com/Luckee-Core/luckee-blueprints) | [`luckee-blueprints-express-server`](https://github.com/Luckee-Core/luckee-blueprints-express-server) |
| **Lead Studio** | Lead CRM, research workers, email queue — reference self-hosted pair | [`lead-studio-web-open-source`](https://github.com/Luckee-Core/lead-studio-web-open-source) | [`lead-studio-express-server`](https://github.com/Luckee-Core/lead-studio-express-server) |
| **My Health** | Self-hosted appointments, care team, focus areas, and daily notes — personal health dashboard | [`my-health-open-source`](https://github.com/Luckee-Core/my-health-open-source) | [`my-health-open-source-express-server`](https://github.com/Luckee-Core/my-health-open-source-express-server) |
| **Personal Finances** | Self-hosted money dashboard — CSV imports, your AI prompts for categorization, recurring bills and loans | [`personal-finances`](https://github.com/Luckee-Core/personal-finances) | [`personal-finances-express-server`](https://github.com/Luckee-Core/personal-finances-express-server) |
| **Knowledge Studio** | YouTube / knowledge workflows | [`knowledge-studio-open-source`](https://github.com/Luckee-Core/knowledge-studio-open-source) | [`knowledge-studio-express-server`](https://github.com/Luckee-Core/knowledge-studio-express-server) |
| **Blog Studio** | Blog authoring and distribution | [`blog-studio-open-source-web`](https://github.com/Luckee-Core/blog-studio-open-source-web) | [`blog-studio-open-source-express-server`](https://github.com/Luckee-Core/blog-studio-open-source-express-server) |
| **Code Your Resume** | Job-search CRM, resume graphics studio (TSX preview), skills/background/job studios | [`code-your-resume-open-source`](https://github.com/Luckee-Core/code-your-resume-open-source) | [`code-your-resume-open-source-express-server`](https://github.com/Luckee-Core/code-your-resume-open-source-express-server) |
| **QR Code Generator** | QR generation API / utilities | — | [`qr-code-generator-open-source-express-server`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server) |

**After you clone:** in each repo, follow **`README.md`** and **`.env.example`** (and any SQL migrations that repo documents). The second studio you adopt is usually faster than the first — same Express + Supabase + Next patterns throughout.

### Luckee Dev Hub (local launcher)

Run **all hooked-up studios** from one browser UI — status probes, **Run** (embedded terminals + Chrome), **Open Cursor**, **Open Chrome**. **Run** opens interactive terminals in a bottom dock panel (Express + Web tabs) via `node-pty` + WebSocket — no macOS Terminal windows by default.

| Repo | Role |
| --- | --- |
| [`luckee-hub`](https://github.com/Luckee-Core/luckee-hub) | Next.js UI (:4100) |
| [`luckee-hub-express-server`](https://github.com/Luckee-Core/luckee-hub-express-server) | Local API + macOS launcher (:4110, `127.0.0.1` only) |

```bash
git clone https://github.com/Luckee-Core/luckee-hub-express-server.git
git clone https://github.com/Luckee-Core/luckee-hub.git
cd luckee-hub-express-server && cp hub.local.json.example hub.local.json
# Edit hub.local.json — add webDir / expressDir / workspaceFile per studio you have cloned
```

```bash
zsh luckee-hub/scripts/start-luckee-hub-dev.sh
# Or: zsh luckee-hub/scripts/install-luckee-hub-dev-app.sh  → Desktop "Luckee Dev Hub.app"
```

Open [http://localhost:4100](http://localhost:4100). Studios in `data/studios.registry.json` but missing from `hub.local.json` show as **Available (not hooked up)**.

Set `"useExternalTerminal": true` in `hub.local.json` to fall back to macOS Terminal.app windows (legacy).

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
2. **Sort** rows alphabetically by the **Studio** column (first word), unless you intentionally group “Luckee *” first — keep Luckee-branded rows together at the top and sort the rest A–Z.
3. **Link shape:** `https://github.com/<ORG>/<repo>` with the same `<ORG>` as the callout at the top of this file.
4. **Optional docs:** add or link a page from [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing) under `/docs/open-source/…` and, if the studio has a **Data** section, under `/docs/data/…` (see `src/config/routes.ts` in marketing for path conventions).
5. **Marketing home (optional):** if the studio is flagship-level, consider a callout in `src/packages/landing/open-source/` — otherwise the table here + docs is enough.

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
