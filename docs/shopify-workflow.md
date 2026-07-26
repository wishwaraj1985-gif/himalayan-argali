# HA Shopify Workflow

How changes reach the HA storefront safely.

Addresses the sixth initial priority in [`brand-foundation.md`](brand-foundation.md): *create a safe Shopify development workflow.* The working principle it serves is *make changes traceable, reviewable, and reversible.*

## The core problem

Shopify's admin makes destructive changes easy and reversal hard. Editing a live theme applies instantly to real customers with no review step and no undo. Most storefront damage comes from a small edit made directly on the live theme with good intentions.

The workflow exists to put a gap between "I changed something" and "customers see it."

## Rules

1. **Never edit the live theme.** No exceptions, including one-line fixes. Especially one-line fixes.
2. **Work on a duplicate.** Duplicate the live theme, change the copy, review it, then publish.
3. **One change set at a time.** A theme with three unrelated changes cannot be partially rolled back.
4. **Publishing is a release.** Treat it with the seriousness of a deployment, not a save.
5. **Keep a known-good theme.** Always have an untouched copy of the last working live theme to revert to.
6. **Secrets never enter the repo.** See below.

## Theme naming

`YYYY-MM-DD — <short description>`

- `2026-07-26 — pillar navigation`
- `2026-08-02 — product page metafields`

Dated names make it obvious which theme is current and which are stale. Delete old themes periodically, but never the last known-good one.

## Making a change

1. **Duplicate** the live theme
2. **Rename** the duplicate per the convention
3. **Change** one coherent thing
4. **Preview** and review against the checklist below
5. **Get approval** if the change is customer-facing or brand-affecting
6. **Publish** the reviewed theme
7. **Verify** on the live store immediately after
8. **Record** what changed and why

## Pre-publish checklist

**Function**

- Homepage, a collection page, and a product page all load
- Add to cart, cart, and checkout entry work
- Search returns results
- Navigation links resolve — no 404s

**Presentation**

- Mobile layout checked, not only desktop
- Images load at sensible sizes
- No placeholder or lorem text
- Typography and colour match the brand definitions

**Brand**

- The four pillars remain clear
- Copy matches the established voice
- Claims on any visible product are ones already cleared

**Safety**

- No credentials, tokens, or internal notes visible in source
- No test or draft products exposed
- Prices and availability correct

## Rolling back

Publish the previous known-good theme. That is the whole procedure — which is exactly why the known-good theme must always exist.

If the problem is data rather than theme (products, collections, metafields), rollback is not automatic. Note what you changed before you change it.

## Content vs. code

Not everything is a theme change:

| Change | Where | Risk |
|---|---|---|
| Theme layout, sections, styling | Duplicate theme → publish | High |
| Product content | Shopify admin, per product record | Medium |
| Collections and merchandising | Shopify admin | Medium |
| Navigation | Shopify admin | Medium — breaks links easily |
| Metafield definitions | Shopify admin | High — schema changes are hard to reverse |
| Apps | Shopify admin | High — apps inject code and can outlive their usefulness |

Metafield definitions and app installations deserve the same caution as theme publishing, even though Shopify presents them as ordinary settings.

## Apps

- Install deliberately; each app is code running on the storefront
- Record what each app does and who decided to add it
- Uninstall leaves residue — check for orphaned code after removing one
- Prefer native Shopify capability over an app where the difference is small

## What never enters this repository

This repository is **public**. Anything committed is readable by anyone, permanently, including after deletion — git history preserves it.

Never commit:

- Admin API keys, access tokens, app secrets, webhook signing keys
- Storefront password or staff account credentials
- Customer records, order data, email lists, or any personal data
- Supplier names, pricing, cost of goods, margins, or contract terms
- Payment, tax, or banking configuration
- Private URLs for unpublished themes or preview links

Credentials belong in the Shopify admin or a password manager. Commercial data belongs in private storage. This repo holds brand strategy, structure, and public-safe implementation only.

**If a secret is committed:** rotate it immediately. Removing the commit is not sufficient — assume it is compromised the moment it is pushed.

## Version control

As theme source moves into `../shopify/`:

- Commit theme changes alongside the decision that motivated them
- Keep commits scoped to one change set, matching the theme workflow
- Reference the relevant doc in the commit message where a change reflects a brand decision

## Review

Revisit this workflow after the first few releases. A process nobody follows because it is too heavy is worse than a lighter one that holds.
