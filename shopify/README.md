# Shopify

Shopify theme and commerce implementation for Himalayan Argali.

## What belongs here

- Theme source: templates, sections, snippets, layout, locales
- Theme settings schema and structured content definitions
- Metafield and metaobject definitions (structure, not values)
- Navigation, collection logic, and merchandising rules expressed as code or documented decisions
- Notes on apps in use and what each one is responsible for

## What must never be committed here

- API keys, access tokens, Admin API credentials, or app secrets
- Storefront passwords or staff account details
- Customer records, order exports, or anything containing personal data
- Supplier pricing, cost data, margins, or contract terms
- Payment, tax, or banking configuration

This repository is public. Assume anything committed is readable by anyone, permanently. Secrets belong in the Shopify admin or a password manager, never in git.

## Structure

As implementation begins, expect roughly:

```
shopify/
  theme/          Theme source under version control
  metafields/     Metafield and metaobject definitions
  collections/    Collection rules and merchandising logic
  docs/           Implementation notes and app decisions
```

Create folders when there is real content for them. Empty scaffolding ages badly.

## Working rules

1. **Never edit the live theme directly.** Work on a duplicate, review, then publish.
2. **One change set at a time.** Small, reviewable, reversible.
3. **Publish deliberately.** Theme publishing is a customer-facing release, not a save.
4. **Record why.** A theme change that reflects a brand or merchandising decision should reference the decision doc.
5. **Check the four pillars.** Every template, collection, and navigation choice should make Wear, Nourish, Equip, or Explore clearer — not blur them.

See [`../docs/shopify-workflow.md`](../docs/shopify-workflow.md) for the full workflow.
