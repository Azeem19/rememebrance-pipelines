# Ancestor Search RAG — Build 5 (STUB · architecture only)

> ## 🔒 DO NOT BUILD THIS WEEKEND — OR UNTIL BUILDS 1–2 ARE LIVE AND GENERATING REVENUE.
> This is the soul of the Remembrance Intelligence Layer, but it is a **product
> capability, not a bottleneck-breaker.** By the Vision 2031 filter it sits in the
> 2029 column: it makes the archive queryable, but it doesn't close a deal or win
> a grant faster. Architecture is captured so it's ready when its time comes. The
> hours belong to Builds 1 & 2, which remove Rob from the revenue path.

*Query the consented elder archive privately, on community-owned hardware.*

## Principle

**Data sovereignty is architectural, not philosophical.** Elder interviews never
leave community-owned hardware. Local vector DB, never AWS/Google.

## The rig

- **Mac Mini M4** runs the pipeline.
- **Ollama** serves a local model.
- **iPad** is the window, over **Tailscale**. Nothing leaves the Mini.

## Pipeline

```
consent-first intake → local transcription (Whisper) → chunk + embed
   → local vector store (Chroma / LanceDB) → retrieval-augmented query
   → local LLM (Ollama), with provenance + consent shown on every answer
```

## Consent

Every chunk carries its consent record. **A story with no documented consent is
never indexed.** This reuses the existing gate — see
[`../pipeline/consent_gate.py`](../pipeline/consent_gate.py) and
[`../data/consent.schema.yaml`](../data/consent.schema.yaml).

## Query surface

"Ask the archive" — a community can search its own collective memory; provenance
and consent are shown with every answer.

## Stub Lego (high-level only — do not build)

| Block | What it is | Done when |
|-------|-----------|-----------|
| 01 · Consent-gated intake | Ingest only stories with a documented consent record. | Nothing enters the index without consent metadata. |
| 02 · Local transcription | Whisper (or equiv) on the Mini; audio never leaves the machine. Reuses [`../pipeline/transcribe.py`](../pipeline/transcribe.py). | A 2-hour interview transcribes locally, overnight, free. |
| 03 · Embed + store | Chunk, embed, write to a local vector DB (Chroma/LanceDB). | Transcripts queryable by meaning, on-machine. |
| 04 · RAG query | Ollama-served model answers questions grounded in retrieved chunks, with provenance + consent shown. | "Ask the archive" returns sourced answers; nothing leaves the Mini. |

## Reuse hooks (when the time comes)

- `pipeline/consent_gate.py` — the consent enforcement gate (Block 01).
- `pipeline/transcribe.py` — local transcription entry point (Block 02).

**Revisit after Builds 1–2 are live and generating revenue. Not before.**
