# Architecture Overview

ASA5 / ASC is structured as an external security and governance-observability architecture for long-horizon AI systems and agentic runtimes.

## Core Flow

```text
AI system / agentic runtime
        |
        v
External telemetry events
        |
        v
ASA5 Core V2 - trajectory and governance observability
        |
        v
Classified trajectory state
        |
        v
ASC - bounded response recommendation
        |
        v
Operator / security / policy / audit layer
```

## ASA5

ASA5 observes runtime trajectory behavior.

It is concerned with conditions such as:

- trajectory drift
- coherence loss
- integrity degradation
- governance relevance
- pre-incident instability
- recovery loss
- pressure across long-running workflows

ASA5 does not modify the observed model. It reads external telemetry and produces operator-facing security state.

The current Core V2 prototype also represents structured anchors, temporal governance state, evidence and counterevidence, competing hypotheses, bounded counterfactuals, causal consequences, clone-only scenarios, and recovery-plan candidates. These are inspectable operational assessments, not calibrated predictions of real-world failure.

Provider-specific public evidence may enter Core V2 through the Trajectory Distillation Buffer (TDB). TDB preserves provenance, reconstruction boundaries, duplicates, noise, and incompleteness before emitting provider-neutral trajectory points. Unanchored public evidence is not governance-eligible.

## ASC

ASC is the bounded response and stabilization layer.

In the current public version, ASC operates in shadow mode:

- it recommends what response path would be selected
- it does not execute the response
- it records advisory decisions for review
- it keeps human governance explicit

ASC must never be the first observer of instability.

It responds only to already classified ASA5 trajectory state.

## Externality

The observed AI system should not be able to:

- access ASA5 private scoring
- modify ASA5 telemetry interpretation
- suppress ASA5 security state
- alter ASC response recommendations
- bypass audit visibility

This separation is the core ASA principle.

## Current Maturity

The architecture is implemented as a working local prototype and partner-evaluation system. It is not independently validated, statistically calibrated for production risk prediction, or certified for safety-critical deployment.
