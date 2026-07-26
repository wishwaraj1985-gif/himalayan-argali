# HA Product Architecture

How the HA catalogue is organised: taxonomy, naming, identifiers, and the data every product carries.

Companion to [`brand-foundation.md`](brand-foundation.md), which defines the pillars. This document defines the structure beneath them.

## Principles

1. **One product, one pillar.** A product that fits two pillars is under-defined. Decide, don't hedge.
2. **Structure before volume.** The taxonomy should be settled while the catalogue is small enough to restructure cheaply.
3. **The record is the product.** If provenance and claims are not written down, the product is not ready.
4. **Public repo, private commerce.** Structure and positioning here; costs, suppliers, and contracts elsewhere.

## Hierarchy

```
Pillar  →  Category  →  Product  →  Variant
```

- **Pillar** — Wear, Nourish, Equip, Explore. Fixed. Adding a fifth is a brand-level decision.
- **Category** — the customer-recognisable grouping within a pillar.
- **Product** — the thing bought, with its own page and story.
- **Variant** — size, colour, weight, flavour. Never a separate product.

## Categories by pillar

### Wear

| Category | Contains |
|---|---|
| Technical apparel | Performance layers, base layers, race and training wear |
| Everyday activewear | Casual-active pieces worn outside training |
| Teamwear | Club and squad kit, customisable items |
| Accessories | Caps, gloves, socks, bags, small goods |

### Nourish

| Category | Contains |
|---|---|
| Honey | Varietals and formats |
| Sea buckthorn | Juices, preserves, oils, derived products |
| Healthy foods | Ambient foods beyond honey and sea buckthorn |
| Sports nutrition | Fuelling, hydration, protein |
| Recovery | Post-activity and wellness products |
| Nurture Boxes | Curated multi-product boxes |

### Equip

| Category | Contains |
|---|---|
| Ice skating | Short-track, long-track, figure skating |
| Ice hockey | Skates, protective, sticks, accessories |
| Inline skating | Boots, frames, wheels, bearings |
| Cycling | Equipment and accessories |
| Pickleball | Paddles, balls, accessories |
| Sport accessories | Cross-sport items: bags, tools, care, spares |

### Explore

| Category | Contains |
|---|---|
| Camps | Multi-day residential or day programmes |
| Coaching | Individual and group instruction |
| Workshops | Short-format skills and education |
| Events | Competitions, meets, community gatherings |
| Memberships | Recurring access or community membership |
| Expeditions | Travel-based active experiences |

Explore products are services. They need dates, capacity, location, eligibility, cancellation terms, and — where minors participate — supervision and safeguarding requirements defined before they can be sold.

## Naming

**Pattern:** `HA <Descriptor> <Product Type>`

- `HA Ladakh Wildflower Honey`
- `HA Sea Buckthorn Juice`
- `HA Short Track Race Suit`

Rules:

- Descriptive over clever. A customer should know what it is from the name.
- Provenance in the name only when it is real and material.
- No superlatives, no invented technology words, no unearned suffixes.
- Variants are not in the product name — size and colour live in variant fields.
- Once published, a name is sticky. Changing it breaks links, reviews, and recognition. Decide carefully the first time.

## SKU structure

**Pattern:** `HA-<PILLAR>-<CAT>-<PRODUCT>-<VARIANT>`

| Segment | Format | Example |
|---|---|---|
| Prefix | `HA` | `HA` |
| Pillar | 1 letter — W, N, E, X | `N` |
| Category | 3 letters | `HON` |
| Product | 3–4 alphanumeric | `WLD` |
| Variant | 2–4 alphanumeric | `250G` |

Example: `HA-N-HON-WLD-250G` — Nourish / Honey / Wildflower / 250g.

Pillar letters: **W**ear, **N**ourish, **E**quip, e**X**plore. Explore takes X because E is already Equip; fix this convention now rather than discovering the collision later.

SKUs are internal identifiers. They should be stable, sortable, and never reused — not marketing.

## Required product data

No product goes live without all of these:

**Identity** — name, SKU, pillar, category, status
**Commerce** — price, variants, availability, shipping class
**Content** — short description, full description, key features, imagery
**Provenance** — origin, production context, why it is credible
**Substantiation** — each claim with its basis recorded
**Compliance** — regulatory status per market, restrictions, required labelling

Enforce this through Shopify metafields so an incomplete product is visible as incomplete rather than quietly shipping.

## Claims

The rule from `brand-foundation.md` applies with full force: product claims must be accurate, responsible, and compliant.

- A claim without a recorded basis does not get published.
- Describe composition, origin, and traditional use rather than implying medical effect.
- Sports nutrition and recovery claims are held to the same standard as food claims.
- Nurture Boxes for children and youth groups — Cubs, Explorers, Pathfinders, Guides — need age-appropriate formulation, clear allergen information, and conservative wording.
- Where a claim is arguable, publish the conservative version.

## Product lifecycle

```
Concept  →  In development  →  Ready  →  Active  →  Discontinued
```

- **Concept** — idea recorded, not committed
- **In development** — sourcing, formulation, or design underway
- **Ready** — all required data complete, compliance cleared, assets approved
- **Active** — live and sellable
- **Discontinued** — withdrawn; page and SEO handling decided deliberately

Only **Ready** products become **Active**. That gate is the point of the whole structure.

## Adding a product

1. Assign pillar and category
2. Reserve the SKU
3. Draft name against the naming rules
4. Complete the product record
5. Record claims with their basis
6. Confirm compliance for target markets
7. Approve imagery into `../assets/`
8. Move to Ready, then publish via the Shopify workflow

## Changing this structure

Taxonomy changes ripple through SKUs, collections, navigation, and links. Change it while the catalogue is small; after that, treat it as a migration with a written plan rather than an edit.
