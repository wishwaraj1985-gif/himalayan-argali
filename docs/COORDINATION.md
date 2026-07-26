# Agent Coordination — Cowork · Claude Code · Codex

How three AI tools work the same Himalayan Argali repo without colliding. Read this first.

*Added by Claude Cowork, 26 July 2026. This repo is **public** — see the secrets rule in [`shopify-workflow.md`](shopify-workflow.md).*

---

## The three tools and their lanes

| Tool | Runs where | Best at | Owns |
|---|---|---|---|
| **Codex** | This computer, in the repo | Repo code, structure, docs, commits | The repo working tree |
| **Claude Code** | This computer, in the repo | Repo code, git, terminal, running things | Shares the repo working tree |
| **Claude Cowork** | Desktop app + connectors | Shopify admin/theme, catalogue, brand docs, visuals | The Shopify store + brand canon |

The dividing line: **Cowork touches Shopify (the live commerce system); Codex and Claude Code touch the repo (the code and docs).** They meet in this repo, which is the shared source of truth.

---

## The one rule that prevents collisions

**Commit or stash before handing off.** Only one tool should have uncommitted changes at a time.

At the time this doc was written the tree was **dirty** — six files modified, uncommitted (Codex's in-progress work). If Cowork or Claude Code had started editing those same files, the work would have collided with no clean way to separate it.

Protocol:
1. Finish a change set.
2. Commit it (or stash) — the tree is clean.
3. *Then* the next tool starts.
4. Never leave the repo dirty when switching tools.

Claude Cowork will **not** commit or push. It creates/edits files when asked and leaves git operations to you, Codex, or Claude Code — because Cowork can't see whether a commit would clobber another tool's uncommitted work.

---

## Source of truth — where each thing lives

| Thing | Lives in | Not in |
|---|---|---|
| Brand strategy, pillars, voice | `docs/` (this repo) | — |
| Product taxonomy, SKUs | [`product-architecture.md`](product-architecture.md) | — |
| Shopify safe-change process | [`shopify-workflow.md`](shopify-workflow.md) | — |
| Manufacturing provenance system | [`hastakshar-provenance-system.md`](hastakshar-provenance-system.md) | — |
| Full session history | [`session-log-2026-07-26.md`](session-log-2026-07-26.md) | — |
| **Live Shopify theme** | **Shopify only — not yet in this repo** | `shopify/` (empty) |
| Theme preview URLs, unpublished theme IDs, discount codes, credentials | Private notes / password manager | **Never this public repo** |

---

## The gap blocking "code + Cowork + Codex together"

**The Shopify theme source is not in the repo.** `shopify/` is a placeholder. Right now the only working copy of the migrated theme is an unpublished theme inside Shopify (built by Cowork). Codex and Claude Code cannot touch theme code that isn't on disk.

**Top enabling action:** pull the theme into `shopify/` so all three tools share it.

```
# in shopify/ , using Shopify CLI (Claude Code or Codex can run this)
shopify theme pull --theme <theme-id>
```

Once the theme is version-controlled in `shopify/`:
- Codex / Claude Code edit theme code as normal repo files, commit per `shopify-workflow.md`.
- Cowork pushes reviewed changes back to Shopify and handles preview/publish (publishing is a Shopify-admin step a human does).
- Round trip: edit in repo → `shopify theme push` to an unpublished theme → Cowork/human previews → publish.

Ask Cowork for the unpublished theme ID when you're ready to pull it — it's withheld from this public repo on purpose.

---

## Open reconciliations (decide together before building on them)

1. **Two taxonomies exist.** This repo defines four **pillars** — Wear / Nourish / Equip / Explore (`product-architecture.md`). The brand master defines four **worlds** — On Ice / On Wheels / Nurture / Experience. They are not the same axis (product-type vs discipline). Pick one as canonical for navigation, or define an explicit mapping, before either drives Shopify collections.
2. **Identifier overlap.** SKUs use pillar letters `HA-W/N/E/X-…`. The हस्ताक्षर register uses `HA-G` (garment) / `HA-L` (leather) / `HA-T` (tools). Register IDs are provenance serials, not SKUs — different purpose, but confirm the letter spaces don't confuse. Keep them clearly separate in any schema.
3. **Catalogue state.** Cowork made permanent Shopify changes (deleted one ghost product + 32 empty collections); ~41 empty collections still exist; product `vendor`/`productType`/tags and a ₹0 `Bearings` price are unfixed. See the session log §8.

---

## Current live-store state (as of 26 Jul 2026)

- Live storefront **unchanged** — still the original SkateBang-derived theme.
- A migrated theme exists **unpublished** in Shopify (nav/discount cleanup, Tier-1 hero, a homepage draft). Not published.
- Store is on **Pause and Build** — checkout disabled until upgraded.
- One discount code (`HELMET25`) still active; a possible popup app unconfirmed.

---

## Quick protocol summary

- Cowork = Shopify + brand canon. Codex / Claude Code = repo + git.
- Clean tree before switching tools. Cowork never commits.
- Theme belongs in `shopify/` — pull it there to unblock code work.
- Nothing private in this public repo — no preview URLs, theme IDs, codes, or credentials.
- Record decisions as docs; reconcile the two taxonomies before building on either.
