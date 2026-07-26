# Products

Product information and catalogue structure for Himalayan Argali.

This folder is the source of truth for **what a product is** — its identity, claims, provenance, and place in the brand. Shopify is where that information gets published; it is not where it gets decided.

## What belongs here

- Product definitions: name, pillar, category, variants, positioning
- Approved copy: descriptions, benefit statements, usage guidance
- Provenance: origin region, harvest or production context, what makes it credible
- Substantiation: what a claim rests on, and where the evidence lives
- Compliance notes: labelling requirements, regulated wording, restrictions by market
- Product status: concept, in development, active, discontinued

## What must never be committed here

- Supplier names, contacts, pricing, or contract terms
- Cost of goods, margins, or landed cost calculations
- Manufacturer-confidential specifications or formulations shared under NDA
- Customer data of any kind
- Certificates or test reports containing commercially sensitive detail

This repository is public. Record *that* a claim is substantiated and *what kind* of evidence supports it. Keep the underlying commercial and supplier documents in private storage and reference them by name only.

## Pillars

Every product belongs to exactly one pillar. If it plausibly fits two, that is a signal the product or the pillar boundary needs sharpening.

- **Wear** — apparel, technical clothing, teamwear, accessories
- **Nourish** — honey, sea buckthorn, healthy foods, sports nutrition, recovery, Nurture Boxes
- **Equip** — skating, hockey, cycling, pickleball, and related sports equipment
- **Explore** — camps, coaching, workshops, events, memberships, experiences

## Product record — minimum fields

Before a product goes live it should have all of these settled:

| Field | Notes |
|---|---|
| Product name | Customer-facing, consistent with naming conventions |
| Pillar | One of Wear, Nourish, Equip, Explore |
| Category | Per the taxonomy in `../docs/product-architecture.md` |
| Short description | One or two sentences |
| Full description | Benefit-led, accurate, no unsupported claims |
| Variants | Size, colour, weight, or flavour as applicable |
| Provenance | Where it comes from and why that matters |
| Claims + basis | Each claim paired with what supports it |
| Compliance status | Cleared, pending, or restricted — and for which markets |
| Imagery status | Approved assets exist in `../assets/` |
| Status | Concept / in development / active / discontinued |

## Claims discipline

Nourish products carry the most regulatory risk. Treat every health, nutritional, or performance statement as something that must be defensible.

- No claim without a basis recorded alongside it.
- Prefer describing composition and traditional use over implying medical benefit.
- Nurture Boxes aimed at children and youth groups (Cubs, Explorers, Pathfinders, Guides) need extra care on age-appropriateness, allergens, and wording.
- When unsure, write the conservative version and flag it for review.

## Naming

Naming conventions and SKU structure are defined in [`../docs/product-architecture.md`](../docs/product-architecture.md). Follow them from the first product rather than retrofitting later.
