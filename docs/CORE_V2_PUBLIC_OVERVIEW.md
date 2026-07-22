# Core V2 Public Overview

## Purpose

Core V2 is the current reasoning engine inside the local ASA5 Security Enterprise
prototype. It analyzes ordered runtime events while preserving a visible boundary
between source evidence, derived interpretation, governance state, and operator
decision authority.

## Public Architecture

```text
Ordered external events
        |
        +--> intent and anchor structure
        +--> propositions and temporal state
        +--> delegation and commitment state
        |
        v
Evidence and constraint layer
        |
        +--> evidence / counterevidence
        +--> competing hypotheses
        +--> coverage and uncertainty
        |
        v
Bounded consequence analysis
        |
        +--> counterfactual hypotheses
        +--> causal consequence structure
        +--> clone-only scenario simulation
        +--> recovery-plan candidates
        |
        v
Operator-readable state and diagnostics
```

## Implemented Capabilities

The local prototype implements:

- structured anchor facets and propositions;
- temporal approval and governance state;
- decision-owner, delegation, commitment and violation tracking;
- formal constraint evaluation;
- competing explanations and counterevidence;
- correlation-aware evidence fusion;
- counterfactual hypotheses and causal consequence graphs;
- bounded scenario simulation on cloned state;
- bounded recovery-plan optimization;
- trajectory playback and operator diagnostics.

## Epistemic Boundary

Core V2 outputs are structured operational assessments, not statements of ground
truth. Confidence-like values are not presented as calibrated probabilities unless
an independently validated calibration profile exists. The engine must preserve
unknown, unsupported, conflicting, and incomplete states rather than silently
converting them into certainty.

## Deployment Boundary

Core V2 is a working local prototype. Production deployment would require a scoped
threat model, independent validation, domain-specific tests, calibration, access
control review, operational monitoring, and an agreed human-governance model.
