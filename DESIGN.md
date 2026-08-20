# Design: witnessos-alpha

This document describes the design of the WitnessOS Alpha investment package: public HTML assets (index.html, investment package, master roadmap) used for partner outreach: the actors, the actions
they perform, and the data flow. It accompanies
[THREAT-ASSESSMENT.md](THREAT-ASSESSMENT.md) (threat model) and
[TESTING.md](TESTING.md) (test policy).

## Purpose

The witnessos alpha investment package: public html assets (index.html, investment package, master roadmap) used for partner outreach.

## Actors

| Actor | Description |
| --- | --- |
| Partner/reader | Reads the alpha HTML assets to evaluate the WitnessOS programme. |
| Content steward | Maintains the HTML assets. |

## Actions

| Action | Performed by | Implemented in |
| --- | --- | --- |
| Publish alpha assets | Steward | `*.html` |
| Validate files | CI | `docs-ci.yml` |

## Data flow

```
repository (main branch)
        │
        ▼
CI (on push / pull_request) ──► validate / test / security jobs
        │
        ▼
tagged release ──► build artifacts + CycloneDX SBOM + Sigstore signatures + SHA256SUMS
```

## Design invariants

1. **Open by construction.** The content is freely licensed and version-controlled.
2. **Minimal dependencies.** Fewer dependencies means a smaller attack surface.
3. **Tamper-evident releases.** Where releases exist, assets carry Sigstore signatures and checksums.
