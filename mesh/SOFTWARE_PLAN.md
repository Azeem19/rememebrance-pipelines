# The Remembrance Mesh — Software Layer Plan

> **Status: PLAN.** This scopes the software that can be written *today, without
> any radio hardware*, and draws a hard line at what genuinely needs a LoRa
> bench. The goal: have a working, tested consent+payload+ledger core running in
> a simulator before a single node is bought — so the hardware, when it arrives,
> plugs into proven logic.

Grounded in the existing repo. The mesh does not invent a new consent model; it
applies `pipeline/consent_gate.py` at the radio edge.

---

## What's buildable today (no hardware)

Four pure-Python modules + a simulator. All testable on the Mini or over the
iPad terminal, same portability discipline as the Node-Readiness Scorer.

### 1. `mesh/tier.py` — tier ⇄ consent bridge

The three storyboard tiers are a *view* over the existing `consent_for` flags in
`consent_gate.py` (`transcription`, `diarization`, `thematic_tagging`,
`internal_archive`, `public_release`, `curriculum_use`, `research_use`). One
function derives the tier from a validated `ConsentDocument`; the mesh never
reads consent independently of the gate.

```
Held Close     → internal_archive False AND public_release False
                 (matching/thematic only; nothing leaves the rig)
In Trust       → internal_archive True, public_release False,
                 community_review gated
In the Commons → public_release True OR curriculum_use True OR research_use True
```

`derive_tier(doc) -> Tier` calls the *same* `validate()` the pipeline already
uses. A revoked/expired/embargoed record raises `ConsentError` before any tier
is emitted — the gate stays the single choke point.

### 2. `mesh/payload.py` — the 240-byte codec

Encode/decode the six storyboard payload types into a ≤240-byte frame (LoRa's
hard limit). **Pointers only — never content.** A dead-drop carries an opaque
story ID + tier + origin-node ID; retrieval happens later at the rig through the
gate.

Frame: `ver(1) · type(1) · tier(1) · origin_node(2) · ref(≤16) · ts(4) · body(≤N)`.
A `assert len(frame) <= 240` is the codec's core invariant (unit-tested). The
six types map 1:1 to the storyboard cards (dead-drop, match signal, co-op
availability, grant alert, presence beacon, audit ping).

### 3. `mesh/presence.py` — presence-by-tier, with a real anonymity floor

Emits `"an elder of the Held Close tier is here"` — tier, never name. **This is
the piece with a genuine privacy risk, so it does not ship on trust:**

- **k-anonymity floor:** a presence beacon is suppressed unless at least *k*
  members share that (tier, site, time-bucket). Below k, a "tier" beacon is a
  person. Default k configurable; start conservative.
- **Time-bucketing + jitter** so beacon timing can't fingerprint a routine.
- **Rotating per-epoch pseudonyms**, not stable IDs, so two beacons can't be
  linked across days.
- Grounded in the Reading Index **Demographic Disparities** entry: run a
  stress-test grid (tier × site × time) and write a PRISMA-style table showing
  no single beacon resolves to an individual. Presence ships only after that
  table passes.

### 4. `mesh/ledger.py` — the community bench-hours ledger

Append-only local log of elder bench hours → the number that feeds dashboards,
grant reports, and coffee perks. Per the Reading Index **Attribution Crisis**
entry (*"Citation IS consent"*), every ledger entry logs its source node + tier,
and the ledger exposes an **attribution-gap metric** (hurdle model: is there a
gap between stories surfaced and stories credited, and how large). Signed
entries so an audit ping can verify a month's hours without a central server.

### 5. `mesh/sim.py` — the mesh simulator

A pure-software fake of totems/repeaters/rig so 1–4 can be tested end to end with
zero radios: enqueue taps → derive tier → encode payload → hop through N virtual
relays (assert sealed: relays touch bytes they can't decode) → arrive at a mock
rig → ledger updates. This is how we validate the whole logic path *before*
Meshtastic is on the bench.

---

## The hardware line (NOT today)

Needs a physical bench and is explicitly out of scope for a no-hardware session:

- Meshtastic firmware config, channel/PSK setup, actual LoRa TX/RX.
- NFC reader integration + the glow-lexicon LED driver on the totem MCU.
- Range/link-budget modeling and a corridor site survey.
- FCC Part 15 / ISM duty-cycle review.
- Repeater siting agreements (poles, steeples, library roof).

The simulator is designed so the real radio layer swaps in behind the same
`payload`/`presence` interfaces — hardware becomes a transport, not a rewrite.

---

## Reading Index citations (per CLAUDE.md protocol)

- **Attribution Crisis in LLM Search Results** (Data & Policy 2026, 8:e15) →
  `ledger.py` logs source+tier on every entry and computes the attribution gap.
  *Citation IS consent.*
- **Demographic Disparities in Medical LLMs** (IJEH 2025) → `presence.py` runs a
  demographic stress-test grid and ships only behind a passing k-anonymity table.
- **Prompt Engineering / Document Extraction** (Electronics 2025) → if a
  match-signal ever classifies free-text into a category, use APE + a confidence
  score, human-in-the-loop — do not hardcode.

## Suggested build order (a real half-day of work, no hardware)

1. `tier.py` + tests (map onto `consent_gate.py`, reuse `validate()`).
2. `payload.py` + tests (the 240-byte invariant).
3. `ledger.py` + tests (append-only, signed, attribution-gap metric).
4. `sim.py` wiring 1–3 into an end-to-end run.
5. `presence.py` **last**, with the k-anonymity gate and the stress-test table.

Every module stdlib-first; `consent_gate.py` already uses `pyyaml`/`pydantic`,
so tier.py inherits those and nothing new is required for the core.
