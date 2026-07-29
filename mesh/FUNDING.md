# The Remembrance Mesh — Grant Package (The Braid)

> **Status: PLAN.** The fundable framing of the Mesh. The core move: the network
> is **not one grant** — it's three braided streams (wages, heritage,
> infrastructure) that together pay for a workforce product that builds and owns
> its own connectivity. This is the model that lets the network pay for itself.

Cost figures are indicative (community-reported builds; ruggedized public units
run to the high end). No funder is promised a modeled coverage map — see the
"What we don't claim yet" section in `ARCHITECTURE.md`.

---

## The three strands

| Strand | What it pays for | Candidate sources |
|--------|-----------------|-------------------|
| **Youth Wages** | Apprentice hours: the youth who fabricate totems, tokens, repeaters. | SYEP (summer youth employment), WIOA youth workforce funds, YouthBuild |
| **Heritage & Craft** | Documentation of elder craft — surveys, oral histories, the record itself. | NPS Underrepresented Community Grants (URC), African American Civil Rights (AACR) History grants |
| **Infrastructure** | The nodes, repeaters, and the mesh itself — hardware + siting. | State digital-equity / broadband-equity funds, Internet Society (ISOC) community-network grants |

**The braid:** one apprentice building one totem simultaneously earns a *wage*
(strand 1), produces *heritage documentation* of the elder technique captured in
the build (strand 2), and yields a *piece of infrastructure* the community owns
(strand 3). Three funders, one unit of work — that's the efficiency the package
sells.

## Precedent that de-risks the ask

- **Detroit Digital Stewards** — 300+ builders trained, ages 21–80, 500+
  households reached. The apprentice-builds-infrastructure model is proven.
- **NYC Mesh** — 2,000+ member-owned nodes; community governance at scale.

The Mesh adapts a validated playbook rather than inventing one — a fundable
posture, not a moonshot.

## How this connects to the rest of Cypher

- **Feeds Build 2 (Grant RFA Decomposer)** in `cypher-tools/grant_decomposer/`.
  Each strand's RFAs become inputs to the decomposer: parse → role-split
  (Applicant / Cypher / Joint) → gate-check → work plan. The Mesh is a live test
  case for the generator once its source docs land.
- **Sits in the 38-grant playbook** as a multi-strand entry rather than a single
  line — the decomposer's "international / multi-tier" edge case applies to the
  corridor's Moorestown–Camden–Wilmington multi-jurisdiction reality.
- **Runs one** should be the strand with the nearest deadline and the cleanest
  eligibility gate; the decomposer's gate-check block decides which.

## The pitch line (for LOIs and the deck)

> The Remembrance Mesh is a community-owned, off-grid memory network whose
> hardware is built by the block's own youth. It braids three funding streams —
> workforce wages, heritage preservation, and digital-equity infrastructure —
> into a single workforce product, so the network trains its builders, preserves
> its elders' craft, and owns its own connectivity in one motion. Memory lives at
> the physical edge, under local control, and travels only by consent.

## Open items before submission

- Confirm current cycle + exact eligibility for each candidate source (deadlines
  drift; verify at RFA time — never state a date the funder hasn't published).
- Identify the applicant-of-record per strand (some workforce funds require a
  fiscal sponsor or LEA partner — ties to the "pending School Partner" in
  `CLAUDE.md`).
- Feed each RFA through Build 2 once its parser is live.
