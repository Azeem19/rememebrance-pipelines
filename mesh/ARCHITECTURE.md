# The Remembrance Mesh — Architecture Spec

> **Status: SPEC / PLANNING.** No hardware purchased, no code written. This
> document is the committed, citable record of the design so it survives the
> Mini↔iPad move and can be quoted in grant narratives.
>
> Storyboards (visual): published Artifact — *The Remembrance Mesh, Three
> Phygital Storyboards*. Source: `mesh/storyboards.html`.

*"Memory should live at the physical edge, under local control, and travel only
by consent."* — The Sovereign Edge Memory Principle

---

## What it is

A community-owned, off-grid mesh network across the **Moorestown–Camden–
Wilmington corridor**. Elders carry an NFC token; shops and porches host a
wooden **totem** (a Meshtastic/LoRa node with an NFC reader); light poles,
library roofs, and church steeples host silent **repeaters**. The mesh carries
*signals about* memory — never the memory itself. Full oral histories sync
separately, by consent, through the library archive rig.

No cloud. No app. No account. No telecom dependency.

## The three storyboards

1. **The Elder's Tap** — the ritual. Token → totem → tab opens → the glow
   lexicon (steady / pulse / blink / slow fade) → the hop → the ledger.
2. **The Mesh as Civic Backbone** — the corridor. Repeater anatomy, the 240-byte
   payload discipline, hop routing, and the three consent tiers.
3. **The Apprentice Pipeline** — the labor. Youth apprentices fabricate the
   totems, tokens, and repeaters with elder craft; every build is heritage
   documentation and every build is grant-fundable.

## Layers

| Layer | What it does | Owned by |
|-------|-------------|----------|
| **Token** | NFC tag in a form the elder chose at their consent session (card, wristband, sewn patch). Identifies a *tier*, not a person. | The elder |
| **Totem** | Wooden housing + Meshtastic node + NFC reader + solar trickle. Reads taps, emits the glow lexicon, originates packets. | The host site |
| **Repeater** | LoRa radio + MCU + antenna + 5W panel. Publishes nothing of its own — relays only. | The community |
| **Archive rig** | The Mini at the library. Holds the actual oral histories, gated by `consent.yaml`. Syncs nightly. | The community, via Cypher stewardship |
| **Ledger** | Community-owned tally of elder bench hours → dashboards, grant reports, coffee perks. | The community |

## The consent tiers ARE the existing consent schema

This is the load-bearing connection. The three tier locks map directly onto
`data/consent.schema.yaml` and `pipeline/consent_gate.py` — the mesh is that
gate applied at the radio edge, not a new consent model.

| Mesh tier | Existing schema equivalent | At the radio edge |
|-----------|---------------------------|-------------------|
| **Held Close** | `consent_for: [transcription, thematic_tagging]`, no release flags | Category matching only. The mesh may emit "a fragment exists"; never content. |
| **In Trust** | `+ archival_storage`, `community_review_required: true`, embargo respected | Cypher stewards under agreement. Encrypted in transit; sync gated by review. |
| **In the Commons** | `+ educational_use / public_exhibition / community_sharing` | The *outcome* joins the ledger every node can see and every grant can cite. |

**The story never travels. Only the pointer travels.** A dead-drop packet says
*"a fragment waits at CIVIC on Eighth"* — retrieval happens at the rig, through
the consent gate, exactly as it does today.

## Reading Index grounding

Per `CLAUDE.md`, methodology is drawn from the vetted Journal Club index before
inventing new approaches. Applicable entries:

- **Attribution Crisis in LLM Search Results** (Data & Policy 2026, 8:e15) —
  *"Citation IS consent. RAG without attribution = extraction."* The mesh is the
  transport-layer expression of the same principle: every packet carries its
  provenance, and every relay carries what it cannot read. The paper's required
  telemetry (source IDs logged alongside output) becomes **every dead-drop
  pointer logs its origin node and consent tier**. The hurdle model gives the
  ledger an attribution-gap metric: (1) is there a gap between stories consumed
  and stories credited? (2) how large?
- **Demographic Disparities in Medical LLMs** (IJEH 2025) — the demographic
  stress-test grid applies to presence beacons. A tier beacon that correlates
  with a single identifiable person is not anonymity. See the k-anonymity floor
  in `SOFTWARE_PLAN.md` § Presence.

## Precedent

- **NYC Mesh** — 2,000+ member-owned nodes, community-governed.
- **Detroit Digital Stewards** — 300+ builders trained, ages 21–80, 500+
  households reached. The apprentice model is theirs; the RNN adapts it.

## Hardware sketch (indicative, not procured)

| Item | Indicative cost | Notes |
|------|----------------|-------|
| Token (NFC tag) | $0.80–$3 | See `SOFTWARE_PLAN.md` § Tokens — static-UID tags are clonable; budget the upper end. |
| Totem (node + housing) | $90–$150 | Fabricated by apprentices; electronics are the minority of cost. |
| Repeater | $40–$130 | Ruggedized public-mount units run toward the high end. |

## What this spec does NOT yet commit to

Named honestly so a funder is never over-promised:

- No hardware has been bought or bench-tested.
- Radio coverage across the corridor is **unmodeled** — LoRa range claims depend
  entirely on antenna height and terrain; a link budget and a site survey come
  before any coverage claim.
- "Presence by tier, not name" is a **design intent with a real deanonymization
  risk**, not a solved anonymity guarantee (see `SOFTWARE_PLAN.md`).
- FCC Part 15 / ISM-band duty and dwell constraints have not been reviewed.
- No agreement yet exists with pole/steeple/roof owners for repeater siting.

## Files

- `ARCHITECTURE.md` — this file.
- `SOFTWARE_PLAN.md` — the buildable software layer and its open risks.
- `FUNDING.md` — the braided grant stack.
- `storyboards.html` — the published visual storyboards (source of the Artifact).
