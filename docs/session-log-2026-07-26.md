# Himalayan Argali — Cowork Session Log
*Recorded 26 July 2026. Read-only summary of everything done in this session, in order, with open items and honest notes.*

---

## 0. Ground truth (unchanged throughout)

- **The live storefront was never touched.** himalayanargali.shop still runs the original SkateBang-derived theme. Every design change described below lives on an **unpublished copy**.
- **Publishing is blocked** through the Shopify connector by design. Going live must be done by you in Shopify admin.
- Store: *Himalayan Argali The Sports Store* · himalayanargali.shop · INR · IST · **Pause and Build** plan (admin editable, checkout disabled until upgraded).
- The connector lacks the app-listing scope, so installed apps could not be inspected.

---

## 1. Orientation

Started from the Cowork bridge file. Governing rule confirmed: **migration, not redesign** — the locked v9 system is fine; the job is deploying it. Two-tier architecture (Tier 1 = HA-made cult line with full liturgy; Tier 2 = pro shop, look-not-liturgy). Kill all discount machinery day one.

---

## 2. Store + theme audit

- **Live theme:** "Himalyan Argali 14-08-2025" (role MAIN), a SkateBang demo template. Nine themes total, including a "Himalyan Argali Backup" from August.
- **Deployed look:** Futura headings; demo colour schemes `#ff6363` coral, `#2bbea1` teal, `#334fb4` blue, `#24104e` purple, `#121212` near-black. **Zero v9 tokens present** — confirming the audit that none of the brand system is live.

---

## 3. Discount machinery — located

| Item | Source | Status |
|---|---|---|
| Black Friday countdown | `templates/index.json` section `banner_countdown_v2_tdUpKd`, counting down to **25 Dec 2025** (long expired) | Removed on working theme |
| Free-shipping nag | `config/settings_data.json` → `show_cart_free_shipping: true`, ₹600 threshold | Turned off on working theme |
| 20%-off popup | **Not in theme.** Likely an installed app — could not confirm (no app scope) | **Unresolved — check Shopify admin → Apps** |

Homepage typos found and corrected on the working theme: `SALALOM SKATE` → `SLALOM SKATE`, `INTRODUCING SALALOM` → `INTRODUCING SLALOM`, `| Most Popular| Scates` → `| Most Popular| Skates`. (The product's real name is "Himalayan Argali Slalom Shoes"; its URL handle `salalom-himalayan-argali` was left alone to avoid breaking links.)

---

## 4. Backup + working theme

- Live theme could not be edited or published through the connector (blocked by design), so the safe path was forced and taken: **duplicated the live theme** → **"HA Working 2026-07-13"** (unpublished; id in private notes). The live theme remains the rollback.

**Preview URLs** (require being logged into Shopify admin in the same browser):
- Homepage: `[unpublished preview URL — withheld from public repo; in private notes]`
- Tier-1 page: `[unpublished preview URL — withheld from public repo; in private notes]`

---

## 5. Edits made on the working theme (unpublished)

1. Deleted the Black Friday countdown section and its `order` entry.
2. Fixed the SALALOM / Scates typos.
3. Set `show_cart_free_shipping` to `false`.
4. Stripped remaining sale language ("DAILY OFFER / WEEKLY OFFER / SHOES SALE" banner, "Special offer" tag).
5. Built the Tier-1 hero (see §7).
6. Built the modern homepage section (see §9) — later rejected, still on the theme.

**Two mistakes I made and own:**
- While re-serialising `settings_data.json` I dropped the `presets` block without asking. Flagged it, then **restored it verbatim** — the file now differs from live by exactly the one intended byte (`true`→`false`).
- While re-serialising `index.json` I dropped a long inline SVG icon from the **disabled** Instagram section. It renders nothing (section is off), but I offered to restore it verbatim and can if you want.

---

## 6. Shopify discount codes (data, not theme)

Listed, **none deleted** (money-touching = your call):
- `HELMET25` — **ACTIVE, no end date** ← still live
- `NAT2025`, `NATDED`, `ANUBHAV` — expired
- `TEST` (automatic) — expired

---

## 7. Tier-1 hero (built)

Files on the working theme:
- `sections/ha-tier1-hero.liquid`
- `templates/product.tier-1.json`

Editorial treatment in v9 tokens: Argali Register serial, copper guilloché seal, made-to-order framing, and a **"Join the Register" waitlist form replacing Add to Cart**. Flagship set to **Skate Package BLW (₹48,000)** because the brief's "RED skate ₹41k" does not exist in the live catalogue. Template is reusable — repointing to another SKU is a one-line change.

Note on the "set everything to out-of-stock / join the list" idea: correct order is build waitlist UI → publish → then flip inventory (flipping first, unpublished, would show "sold out" with no waitlist). Also moot today — Pause and Build already disables checkout.

---

## 8. Catalogue clean-up (live product data — permanent changes)

**Audit findings:** a draft product **"Do Not Delete"** carried ~110 tags, and every collection is an automatic tag-based collection — so that one ghost product was inflating ~40 phantom single-item departments. Also: `productType` empty on every product; `vendor` = "My Store" almost everywhere (including third-party StayBent/EHS); the two ice skates mistagged `Summer Sports`/`Roller Sports`; `Bearings` live at **₹0.00**; placeholder inventory (1000s).

**Actions taken (permanent, approved):**
- **Deleted** the "Do Not Delete" ghost product (no images, no sales — low risk). This collapsed ~32 collections to zero products, confirming the diagnosis.
- **Deleted 32 empty collections** (the phantom set: Boxing Boots, Taekwondo Mat, Volleyball Shoes, Long Track Speed Skating, Bearings, Bags, etc.).

**NOT done (still open):**
- A **second batch of empty collections** was found past the first page (apparel/teamwear tree — EZ Fit, Glasses, Offers & Sale, Winter/Summer Apparel, Suits, Jerseys, plus Badminton, Lawn Tennis, Volleyball, Basketball, Football, Gymnastics, Handball, Field Hockey, Squash, Cricket, Chess, "Testing Himalya"). You approved deleting all empties, but the conversation pivoted before these were removed. **These still exist.**
- No product-level fixes yet: vendor, productType, ice/roller retagging, and the ₹0.00 Bearings price are **unchanged**.

**Real catalogue that remains** (populated): Winter Sports (21), Accessories (19), Roller Sports (16), Blade Sharpening (8), Honey (7), Inline Skate (6), Short Track (5), Services (5), Ice Skate Shoes / Ice Skate Blades / Protective Helmet (4 each), plus smaller. Best Selling (52), Honey Type 1/2 (7 each). ~48 real products intact — nothing else deleted.

---

## 9. Design exploration

- Built a modern homepage **concept** (visual) → rejected.
- Built the real homepage section `ha-home.liquid` + `index.json` on the working theme (v9 tokens, "Carry the mountain with you", four worlds, flagship, Nurture honey, Experience/OTI bridge, founder story) → **rejected** ("look/feel wrong, too much cult stuff"). Still sits on the working theme.
- Retrieved the canonical **brand master** for correct voice/tagline. Flagged a palette discrepancy: the mounted `HA-brand-master-2026.md` is the older v1 (ochre palette); the **v9 tokens (ink/copper/amber/cream) are canonical** per your memory note. Colour work used v9.
- Showed **4 popular current Shopify themes** (Horizon, Craft, Symmetry, Impulse) → "they all look alike."
- Named the real cause: nearly all modern commerce sites share one skeleton (thin nav → big hero → grid). Differentiation comes from **photography, typography, colour, and one signature interaction** — not layout.
- Pulled **live reference storefronts** via browser: Satisfy (video hero, didn't capture), **District Vision** (minimal-luxury athleisure), **Snow Peak** (warm heritage adventure). Still read as "alike."
- You chose the levers: **signature typography + art direction/photography**, and the fusion brief: *postmodern × adventure travel × winter sports × streetwear × athleisure*.
- Built **4 distinct typographic voices** for the same words: A editorial serif (Cormorant), B impact grotesque (Anton, streetwear), C condensed technical (Bebas Neue, sport), D characterful serif + Devanagari पर्वत (Fraunces, postmodern). **Well received.** Voice not yet finalised.

---

## 10. Project हस्ताक्षर (Manufacturing Provenance System)

You delivered a full spec; I captured it as a Brand Master module: **`HA-project-hastakshar-provenance-system.md`** (in the outputs folder). Documentary tone, all 12 refinements folded in, "Heroism you wear" cut. हस्ताक्षर = manufacturing provenance (garments/crafted goods), the twin of Adopt-a-Queen's living provenance (honey), both feeding **The Argali Register**.

Key locked decisions: separate register from honey (`HA-G000001`, Devanagari numerals); "crafted by" not "stitched by"; woven neck label + embroidered crests, no printed logos; per-garment passport page `/hastakshar/000128`; life-history ledger (Registered → Purchased → Repaired → Inherited → Still Active); quiet internal QR; expedition-journal drop names; "scarcity is evidenced, not announced."

Built a **passport page mockup** for register `000128` (Alpine Force Polo, Drop 02) — **maker name only, no city**, per your decision on the Ladakh/Tiruppur tension.

**Open हस्ताक्षर decisions (build-time):** public-vs-private register pages + maker consent policy (sequential IDs are enumerable); repair/inheritance **write-path** (admin flow to update entries years later); claims must be **verifiable-only** (ASCI); woven QR rarely scans — prefer a laminated care-label QR.

---

## 11. GitHub + repo

- GitHub connector was connected but **not authorized** for tool access in-session; provided authorization steps. Account: wishwaraj1985@gmail.com (personal).
- Instead, connected the repo **folder** directly and inspected it read-only:
  - Path: `C:\Users\wishw\Documents\Codex\2026-07-25\check-this-computer-for-all-files\work\himalayan-argali`
  - Branch **`main`**, in sync with `origin/main`
  - Commit **`803da5c`** — "Add HA workspace structure and operating docs"
  - Working tree **DIRTY** — 6 tracked files modified, unstaged (likely Codex's in-progress work): `assets/README.md`, `docs/product-architecture.md`, `docs/roadmap.md`, `docs/shopify-workflow.md`, `products/README.md`, `shopify/README.md`
  - 8 files total; `README.md` and `docs/brand-foundation.md` clean.

---

## 12. Deliverables produced this session

- Working Shopify theme **HA Working 2026-07-13** (unpublished): cleaned `index.json`, `settings_data.json` (free shipping off, presets restored), `ha-tier1-hero.liquid`, `templates/product.tier-1.json`, `ha-home.liquid`.
- `HA-project-hastakshar-provenance-system.md` (outputs)
- Theme screenshots: Horizon, Craft, Symmetry, Impulse (outputs)
- Reference screenshots: Snow Peak, District Vision (outputs)
- Visual concepts (ephemeral, in-chat): homepage concept, 4 typography voices, passport page 000128
- This session log.

---

## 13. Open items / decisions pending

1. **Publish nothing yet** — live site is still SkateBang. Working theme awaits your review + publish in admin.
2. **HELMET25** discount still active — deactivate or keep?
3. **20%-off popup** source unconfirmed — check Apps.
4. **Second batch of empty collections** not yet deleted.
5. **Product data fixes** not done: vendor, productType, ice/roller tags, Bearings ₹0.00.
6. **Design not finalised**: pick a typographic voice (A/B/C/D or mix); define photography direction.
7. **हस्ताक्षर build decisions**: register privacy + maker consent, repair write-path, verifiable claims, QR medium.
8. **Homepage `ha-home.liquid`** (rejected) still on the working theme — remove or replace once the new type/photo direction is set.
9. Restore the disabled Instagram section's SVG icon if you want it back.

---

*End of log. Nothing on the live storefront was changed. The catalogue changes in §8 (one product + 32 collections deleted) are the only permanent actions taken, and were approved.*
