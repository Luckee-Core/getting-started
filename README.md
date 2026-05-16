# Luckee — getting started

This repo is the **entry map** for the Luckee system: how **hosted Luckee Core**, **open-source studios**, **Luckee Blueprints**, and the **Luckee Installer Network** fit together, plus links into each public codebase. There is **no application code here**—only the index and onboarding copy.

> **GitHub org for links in this README:** `Luckee-Core`  
> If your public repos live under a different org, change that string once and replace all `github.com/Luckee-Core/` URLs below.

---

## The Luckee system (how the pieces fit)

These line up with the story on **[Luckee marketing](https://github.com/Luckee-Core/luckee-marketing)** (home: vision → software → open source → on-site delivery).

| # | Piece | What it is |
| --- | --- | --- |
| **01** | **Luckee Core** | Paid, hosted SaaS—**we run it; you run the business.** One workspace for service businesses (leads, jobs/projects, customers, AI-native workflows). Hosted on Supabase, Vercel, and Railway. Product repos: [`luckee-web`](https://github.com/Luckee-Core/luckee-web), [`luckee-central`](https://github.com/Luckee-Core/luckee-central). |
| **02** | **Open-source studios** | **5+ apps:** same architecture and quality bar as Core, split into **repos you can self-host**—mostly **Next.js** frontends and **Express** APIs. Adopt **one studio at a time** on your stack. **This README is the map for that path.** |
| **03** | **Luckee Installer Network** | On-site **AI infrastructure** delivery (hardware through handoff). Installer verification ties to **Luckee Blueprints** certifications; Luckee routes qualified installation work. |
| — | **Luckee Blueprints** | **Train the workforce**—published tracks, certifications, DIY path alongside Core. App: [`luckee-blueprints`](https://github.com/Luckee-Core/luckee-blueprints) (+ [`luckee-blueprints-express-server`](https://github.com/Luckee-Core/luckee-blueprints-express-server) when you wire the API). |

**Hero framing (from marketing):** on-premise AI infrastructure—**your data, your workflows**—with premium build support, the Installer Network for physical install, and a **free DIY** lane through **Blueprints + open source**.

---

## Clone this map (self-host path)

The marketing site tells operators to start from this repo, then jump into individual studios:

```bash
git clone https://github.com/Luckee-Core/getting-started.git
cd getting-started
# Read the studio table below; clone only the web (and API if listed) for the studio you need.
```

Long-form docs on the marketing deploy live under **`/docs/open-source`** (and nested routes such as **`/docs/open-source/knowledge-studio`**). Repo: [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing).

---

## Open-source studios (catalog)

Each **studio** is a product-shaped slice: typically a **Web** repo (Next.js) and sometimes an **API** repo (Express). Use `—` when that side is not a separate public repo for this OSS slice.

| Studio | What it is | Web | API |
| --- | --- | --- | --- |
| **Luckee Open Source** | Lead / ops CRM-style modular dashboard (Luckee OSS surface) | [`luckee-open-source`](https://github.com/Luckee-Core/luckee-open-source) | [`luckee-open-source-express`](https://github.com/Luckee-Core/luckee-open-source-express) |
| **Luckee Blueprints** | Workforce training / certifications / delivery shell | [`luckee-blueprints`](https://github.com/Luckee-Core/luckee-blueprints) | [`luckee-blueprints-express-server`](https://github.com/Luckee-Core/luckee-blueprints-express-server) |
| **Lead Studio** | Lead pipeline and studio workflows (open web edition) | [`lead-studio-web-open-source`](https://github.com/Luckee-Core/lead-studio-web-open-source) | — |
| **Knowledge Studio** | YouTube / knowledge workflows | [`knowledge-studio-open-source`](https://github.com/Luckee-Core/knowledge-studio-open-source) | [`knowledge-studio-express-server`](https://github.com/Luckee-Core/knowledge-studio-express-server) |
| **Blog Studio** | Blog authoring and distribution | [`blog-studio-open-source-web`](https://github.com/Luckee-Core/blog-studio-open-source-web) | [`blog-studio-open-source-express-server`](https://github.com/Luckee-Core/blog-studio-open-source-express-server) |
| **Code Your Resume** | Resume builder / job-search CRM patterns | [`code-your-resume-open-source`](https://github.com/Luckee-Core/code-your-resume-open-source) | — |
| **QR Code Generator** | QR generation API / utilities | — | [`qr-code-generator-open-source-express-server`](https://github.com/Luckee-Core/qr-code-generator-open-source-express-server) |

**After you clone:** in each repo, follow **`README.md`** and **`.env.example`** (and any SQL migrations that repo documents).

---

## Add a new studio (maintainers)

Keep the **catalog table** as the single source of truth. To add a studio:

1. **Add one row** to [Open-source studios (catalog)](#open-source-studios-catalog) above.
2. **Sort** rows alphabetically by the **Studio** column (first word), unless you intentionally group “Luckee *” first—in that case keep Luckee-branded rows together at the top and sort the rest A–Z.
3. **Link shape:** `https://github.com/<ORG>/<repo>` with the same `<ORG>` as the callout at the top of this file.
4. **Optional docs:** add or link a page from [`luckee-marketing`](https://github.com/Luckee-Core/luckee-marketing) under `/docs/open-source/…` and, if the studio has a **Data** section, under `/docs/data/…` (see `src/config/routes.ts` in marketing for path conventions).
5. **Marketing home (optional):** if the studio is flagship-level, consider a callout in `src/packages/landing/open-source/`—otherwise the table here + docs is enough.

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

Same backbone across most studios (so the **second** studio you adopt is faster than the first):

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
