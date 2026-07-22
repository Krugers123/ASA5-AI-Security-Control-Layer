# ASA5 Security Enterprise

**External runtime security and governance observability for long-horizon AI systems.**

ASA5 monitors how an AI workflow evolves over time. It is designed to make
trajectory drift, weakening intent alignment, governance ambiguity, narrowing
option space, and recovery pressure visible before they become obvious surface
failures.

ASA5 remains outside the observed model. It does not modify model weights,
request hidden reasoning, or replace the authority of a human operator.

## Current Public Surface

- Product: `ASA5 Security Enterprise`
- Reasoning engine: `Core V2 v1.3`
- Public integration contract: `External Interface v0.3`
- Response layer: `ASC shadow mode`
- Status: working local prototype and partner-evaluation system

The current implementation is not independently validated, statistically
calibrated for production risk prediction, or certified for safety-critical use.

## The Operating Problem

A long-running agent or AI workflow can remain locally fluent and apparently
correct while its full trajectory moves away from the original human intent,
policy boundary, or approved operating frame.

ASA5 adds an independent observation path:

```text
AI system or agentic runtime
        |
        v
External telemetry and ordered events
        |
        v
ASA5 Core V2
  trajectory + governance reasoning
        |
        +--> evidence and uncertainty
        +--> risk and state transition
        +--> counterfactual and recovery analysis
        |
        v
ASC bounded response recommendation (shadow mode)
        |
        v
Operator / security / policy / audit
```

## What Core V2 Adds

Core V2 moves ASA5 beyond a flat risk score into a typed, inspectable reasoning
pipeline. The implemented local prototype includes:

- structured intent and anchor facets;
- ordered propositions and temporal governance state;
- decision ownership, approval mode, delegation and commitment memory;
- explicit evidence, counterevidence and uncertainty;
- competing hypotheses rather than a single forced explanation;
- bounded counterfactual analysis;
- causal consequence structure;
- clone-only scenario simulation;
- bounded recovery-plan search;
- operator-readable diagnostics and trajectory playback.

These capabilities are implemented and tested locally. They remain subject to
independent validation and domain-specific evaluation.

Read: [Core V2 Public Overview](docs/CORE_V2_PUBLIC_OVERVIEW.md)

## Trajectory Distillation Buffer

The Trajectory Distillation Buffer (TDB) is the evidence boundary between
provider-specific public data and Core V2. It preserves raw source provenance,
reconstructs reply order, removes duplicate influence, marks incomplete branches,
keeps noise auditable, and emits a provider-neutral trajectory.

TDB does not turn public conversations into ground truth. Unanchored public
trajectories remain evidence-only and are not governance-eligible.

Read: [TDB Public Overview](docs/TDB_PUBLIC_OVERVIEW.md)

## ASC Response Boundary

ASC is the bounded response and stabilization layer connected to ASA5. In the
current public surface it operates in shadow mode and can recommend paths such as:

- no action;
- audit-ready response;
- re-anchor;
- slowdown;
- containment;
- operator review.

ASC does not directly control the observed AI system. Public references to
automatic response mean routing or dispatching a classified signal to a configured
security workflow with audit logging and human governance.

Read: [Autonomous Response Boundary](docs/AUTONOMOUS_RESPONSE_BOUNDARY.md)

## Partner Evaluation

ASA5 is ready for controlled technical demonstrations and scoped partner
evaluation. A partner evaluation should use synthetic, public, or explicitly
authorized telemetry and should measure observability quality, false positives,
operator usefulness, integration fit, and failure boundaries.

It should not be represented as a certified production deployment.

Read: [Partner Evaluation Guide](docs/PARTNER_EVALUATION.md)

## Core V2 Console Preview

All images below use a controlled validation environment. They show the public-safe
operator surface and do not disclose private scoring logic, thresholds, credentials,
or raw private conversations.

### Security Overview

The command surface summarizes active runtime state, incident routing, review
coverage, and the live multi-session evidence field.

![ASA5 Core V2 Security Overview](docs/assets/core_v2_v1_3/core_v2_01_security_overview.png)

### Live Trajectory Field

The trajectory graph presents a buffered multi-session field with operational,
evidence-only, and governance-qualified distinctions.

![ASA5 Core V2 Live Trajectory](docs/assets/core_v2_v1_3/core_v2_02_live_trajectory.png)

### Governance Intelligence

Core V2 exposes governance state, risk, human-agency residual, invariant checks,
commitments, hypotheses, recovery, and evidence as separate inspectable surfaces.

![ASA5 Core V2 Governance Intelligence](docs/assets/core_v2_v1_3/core_v2_03_governance_intelligence.png)

### Trajectory Playback

Playback reconstructs the observable session condition without requesting hidden
model reasoning. It separates the operator readout from turn-level drift evidence.

![ASA5 Core V2 Trajectory Playback Summary](docs/assets/core_v2_v1_3/core_v2_05_trajectory_playback_summary.png)

![ASA5 Core V2 Trajectory Playback Evidence](docs/assets/core_v2_v1_3/core_v2_05b_trajectory_playback_evidence.png)

### Incident Workflow

The Incident Center provides a bounded, operator-facing view of critical and
pre-incident conditions in the controlled validation runtime.

![ASA5 Core V2 Incident Workflow](docs/assets/core_v2_v1_3/core_v2_06_incident_workflow.png)

### ASC Shadow Recommendations

ASC summarizes bounded advisory paths without executing them. The public view
keeps shadow-only status, audit readiness, human review, and response-path
distribution visible.

![ASA5 Core V2 ASC Shadow](docs/assets/core_v2_v1_3/core_v2_07_asc_shadow.png)

### Public-Safe Evidence Export

The export surface creates an audit-oriented evidence packet while excluding raw
conversation content.

![ASA5 Core V2 Evidence Export](docs/assets/core_v2_v1_3/core_v2_08_audit_evidence_export.png)

### Bounded Consequence Paths

The consequence demonstrator compares advisory correction paths, preserves human
decision authority, and labels path-support values as uncalibrated indicators rather
than outcome probabilities.

![ASA5 Core V2 Consequence Paths](docs/assets/core_v2_v1_3/core_v2_09_consequence_paths.png)

## Public Evidence and Integration Assets

- [Architecture Overview](docs/ARCHITECTURE.md)
- [Core V2 Public Overview](docs/CORE_V2_PUBLIC_OVERVIEW.md)
- [TDB Public Overview](docs/TDB_PUBLIC_OVERVIEW.md)
- [Validation Status](docs/VALIDATION_STATUS.md)
- [Security and Trust Boundary](docs/SECURITY_AND_TRUST_BOUNDARY.md)
- [External Interface v0.3](docs/ASA5_EXTERNAL_INTERFACE_V0_3.md)
- [OpenAPI 3.1 contract](openapi/asa5_external_api_v0_3.yaml)
- [Golden Trace](docs/GOLDEN_TRACE.md)
- [Operator Disagreement Log](docs/OPERATOR_DISAGREEMENT_LOG.md)
- [Public Scope](docs/PUBLIC_SCOPE.md)
- [Roadmap](docs/ROADMAP.md)
- [Public Screenshot Capture Guide](docs/SCREENSHOT_CAPTURE_GUIDE.md)
- [Disclaimer](DISCLAIMER.md)

The golden trace is an integration fixture. It is not a statistical validation
claim and does not disclose private scoring logic, thresholds, calibration, or
sensitive source content.

## Public Repository Boundary

This repository is a public architecture, evidence-fixture, and integration layer.
It intentionally excludes:

- private implementation code;
- detector and scoring internals;
- thresholds and calibration data;
- proprietary recovery-search logic;
- local databases, caches, credentials, and deployment secrets;
- private or identifying conversation data;
- unrestricted operational adapters.

## Created By

Mieczyslaw Kusowski  
HumanAI / Symbioza2025  
ASA — Asymmetric Stability Architecture
