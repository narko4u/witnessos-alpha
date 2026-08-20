# Security Assessment

Status: assessment performed for the current release. This document records
the most likely and impactful potential security problems for this project and
the mitigations in place. It is reviewed before each release.

## What this project is

The witnessos alpha investment package: public html assets (index.html, investment package, master roadmap) used for partner outreach.

## Assets

1. **Content/specification integrity** - the published content must not silently change.
2. **Tool correctness** - any shipped tooling must not be tricked into wrong output.
3. **No foothold from use** - consuming the content or running the tooling must not compromise the user's host.

## Likely and impactful problems

| # | Problem | Likelihood | Impact | Mitigation |
|---|---------|------------|--------|------------|
| Stale/misleading partner content | Medium | Medium | Content is version-controlled; CI validates structure |
| Credentials committed accidentally | Low | High | CI secrets scan policy in SECURITY.md |

## Threat model scope

- **In scope:** content integrity, tooling input handling, release integrity.
- **Explicitly out of scope:** transport security of external endpoints the user chooses to reach.

## Attack surface analysis

- Components: HTML assets (index/investment/roadmap), witnessos-logo.png.
- CI workflows: least-privilege `contents: read` permissions (plus scoped `security-events: write` for SAST).
