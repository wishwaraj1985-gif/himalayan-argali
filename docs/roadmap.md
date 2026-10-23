# HA Roadmap

This roadmap sequences the six initial priorities set out in [`brand-foundation.md`](brand-foundation.md). It answers *what to do in what order*, not *what HA is*.

The sequencing rests on one judgement: **coherence before expansion.** A store that clearly explains four pillars with a handful of credible products converts better and is cheaper to run than a store with a wide catalogue and no spine. Adding products to an incoherent store multiplies the incoherence.

## Phase 1 — Make the foundation legible

*Goal: a visitor understands what HA is within seconds of landing.*

- Restructure store navigation around Wear, Nourish, Equip, Explore
- Write the pillar landing pages — what each pillar is for, who it serves
- Settle the verbal identity: how HA describes itself, tone, recurring language
- Settle the visual identity essentials: logo usage, palette, typography
- Audit the existing catalogue and assign every live product to exactly one pillar
- Retire, hide, or fix products that fit nowhere

**Done when:** navigation reflects the four pillars, every live product sits in one of them, and the brand language is consistent across the homepage and pillar pages.

## Phase 2 — Build the catalogue spine

*Goal: adding a product is a routine operation, not an improvisation.*

- Adopt the taxonomy and naming conventions in [`product-architecture.md`](product-architecture.md)
- Define the metafield structure products need (provenance, claims basis, compliance status)
- Backfill existing products to the new structure
- Establish the minimum product record — no product goes live incomplete
- Set up collections that follow rules rather than manual curation where possible

**Done when:** a new product can be added end to end by following documented steps, and the catalogue structure holds without exceptions.

## Phase 3 — Launch hero products

*Goal: prove the proposition with a few products rather than diluting it across many.*

- Select a small number of hero products — the ones that best express what HA is
- Nourish is the natural starting point: honey and sea buckthorn carry the Ladakh provenance story most directly
- Build these out fully: photography, copy, provenance narrative, substantiated claims
- Get compliance right before launch, not after
- Measure honestly and learn before widening the range

**Done when:** each hero product has complete content, cleared claims, approved imagery, and real sales data to learn from.

## Phase 4 — Document provenance and trust

*Goal: the trust claims survive scrutiny.*

- Record supplier and provenance information in private storage, referenced from this repo by name only
- Document safety, testing, and certification status per product
- Establish the review step that every product claim passes through
- Build the customer-facing provenance story from what is actually documented

**Done when:** every public claim traces to something recorded, and the record lives somewhere findable.

## Phase 5 — Harden the Shopify workflow

*Goal: changes stop being risky.*

- Adopt the process in [`shopify-workflow.md`](shopify-workflow.md)
- Bring theme source under version control in `shopify/`
- Establish the duplicate-theme-then-publish habit as the default
- Define what gets checked before any customer-facing release

**Done when:** no one edits the live theme directly, and every release is reversible.

## Phase 6 — Expand deliberately

*Goal: growth that does not undo phases 1–5.*

- Widen the catalogue within proven pillars first
- Develop Equip and Explore, which need more operational depth than Wear and Nourish
- Build Nurture Boxes as a distinct proposition rather than a bundle of existing SKUs
- Revisit this roadmap as evidence arrives

## Sequencing notes

Phases 1 and 2 are genuinely sequential — structure before content. Phase 5 can run alongside 3 and 4 and arguably should, since the workflow protects the work being done. Phase 4 is not optional for Nourish; claims discipline is a launch prerequisite there, not a follow-up.

## Parked ideas

Ideas worth keeping that are not scheduled. Each names the condition for picking it up.

### Animated collage explainers for social video

Short vertical (1080×1920) explainer videos for Reels, TikTok and Shorts, built from AI-generated collage pieces (Higgsfield) animated in code by Claude with the `/motion-studio` skill and a recorded voiceover. Reported cost is about 40 Higgsfield credits per video; the animation itself is free.

- **Why it fits:** HA has stories that benefit from explanation — Ladakh provenance for honey and sea buckthorn, and the four pillars.
- **Pick up when:** the Website Master Plan is approved and at least one Phase 3 hero product is live, so videos have somewhere to send people.
- **Conditions before use:**
  - AI imagery stays clearly illustrative (paper-collage style). Real products, places, and people are shown with real photography only — AI images must never stand in for provenance evidence (see Phase 4).
  - Confirm Higgsfield's terms allow commercial use on the plan held.
  - Review the `/motion-studio` skill files before installing them.
  - Use reference pins for style only; do not reproduce other people's artwork.
- **Source:** Notion guide "Make a Collage Explainer Animated in Code with Claude".

## Decision rule

Applied to roadmap items as much as to products:

> Does this help people wear well, nourish well, equip well, or explore well?

Work that fails the test needs an explicit strategic reason, recorded here.
