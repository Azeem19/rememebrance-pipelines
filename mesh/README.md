# The Remembrance Mesh

*A community-owned, off-grid network where memory lives at the edge and travels
only by consent.* Meshtastic + LoRa + NFC, built by the block's own youth.

> **Status: SPEC + PLAN.** No hardware bought, no radio code written. This folder
> is the committed record — visual, technical, and financial — so the design
> survives the Mini↔iPad move and can be cited in grant narratives.

## Non-Extraction Statement

This network receives memory; it does not extract it. The mesh carries *signals
about* stories (240-byte pointers) — never the stories themselves. Full oral
histories sync separately through the library archive rig, gated by the existing
`consent.yaml` at every step. The three tiers (Held Close / In Trust / In the
Commons) are a view over the repo's existing consent flags, not a new model.
Partner: Moorestown WestEnd Descendants Network.

## What's here

| File | What it is |
|------|-----------|
| [`ARCHITECTURE.md`](ARCHITECTURE.md) | The technical spec: layers, tiers-as-consent, precedent, and an honest "what we don't claim yet". |
| [`SOFTWARE_PLAN.md`](SOFTWARE_PLAN.md) | The software buildable *today with no hardware* — tier bridge, 240-byte codec, presence with a k-anonymity floor, bench-hours ledger, simulator — plus the hardware line. |
| [`FUNDING.md`](FUNDING.md) | The braided grant package (wages + heritage + infrastructure) and how it feeds Build 2. |
| [`storyboards.html`](storyboards.html) | The three phygital storyboards (WordPress-deployable source; a CSP-safe variant is the published Claude Artifact). |

## Reading foundations

Per repo `CLAUDE.md`, methodology is grounded in the Journal Club index. The Mesh
leans on two vetted entries: **Attribution Crisis** (*"Citation IS consent"* →
the ledger's source logging + attribution-gap metric) and **Demographic
Disparities in Medical LLMs** (→ the presence layer's stress-test grid). Cited in
`ARCHITECTURE.md` and `SOFTWARE_PLAN.md`.

## Where it sits in the bigger picture

The Mesh is **not** one of the five Build Spec Pack builds (which are revenue-path
first). It's captured here as durable architecture; its funding strands feed the
**Grant RFA Decomposer** (Build 2) in `cypher-tools/`. Build the software core in
the simulator before buying radios.
