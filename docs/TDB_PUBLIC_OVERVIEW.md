# Trajectory Distillation Buffer — Public Overview

## Purpose

The Trajectory Distillation Buffer (TDB) is an evidence-processing boundary between
provider-specific public records and Core V2. Its purpose is to make provenance and
transformation visible before an external conversation is interpreted as a
trajectory.

## Public Flow

```text
Public provider records
        |
        v
Immutable evidence records and provenance
        |
        v
Deterministic deduplication and reply reconstruction
        |
        v
Completeness and relevance qualification
        |
        v
Provider-neutral trajectory points
        |
        v
Core V2 evidence-only shadow analysis
```

## Safety Properties

- private-source use must be explicitly rejected for the public-data path;
- raw evidence and distilled trajectory points remain separate;
- duplicate records cannot gain additional influence;
- incomplete branches and missing parents remain visible;
- excluded noise remains auditable;
- provider annotations are not treated as ASA-derived facts;
- unanchored public trajectories are not governance-eligible;
- source provenance is retained through the transformation path.

## Connector Boundary

Provider-specific connectors are experimental and are not presented as validation
evidence. Public claims about TDB are limited to its provider-neutral evidence
contract and controlled evaluation inputs. Connector credentials, cached provider
responses, cost records, and imported conversations are outside this repository.

TDB is not a semantic truth compressor and does not claim to remove all irrelevant
meaning. Its current public claim is narrower: deterministic structural
distillation with auditable provenance and explicit incompleteness.
