# ASA 5 Enterprise Control Mapping

Public-safe mapping note for enterprise AI security, governance, SOC, and audit review.

## Purpose

ASA 5 is an external runtime security and evidence layer for long-horizon AI systems.

This document explains how ASA 5 can support enterprise control conversations without claiming standalone compliance.

ASA 5 does not replace AI governance frameworks, security verification standards, SOC processes, or audit programs.

It provides an external runtime signal surface that can help those systems measure, review, escalate, and audit trajectory-level risk.

## Position

ASA 5 is designed around a separation principle:

`the AI runtime generates the trajectory; the stability and security signal should be measured outside the model loop.`

ASA 5 does not require:

- model weights
- training data
- hidden activations
- hidden chain-of-thought
- internal model control
- direct modification of model outputs

ASA 5 requires structured runtime telemetry:

- runtime identity
- session identity
- ordered events
- timestamps
- actor or event source
- task or policy frame
- input/output summaries
- tool or action metadata when available
- correction, retry, handoff, or operator-intervention markers
- risk metadata when available

This keeps ASA 5 suitable for enterprise review because it can operate as an external observability and evidence layer rather than an internal model intervention.

## Mapping Summary

| Enterprise area | ASA 5 support |
| --- | --- |
| AI risk governance | External security layer, operator authority, policy review, audit boundaries |
| Runtime monitoring | Trajectory integrity signals, drift indicators, pre-incident states |
| Security operations | Escalation queue, auto escalation for bounded critical cases, downstream routing |
| Evidence and audit | Public-safe evidence export, incident records, operator review state |
| Human oversight | Human-owned policy authority, post-dispatch review, audit trail |
| Agentic systems | Long-horizon trajectory analysis, correction integrity, recovery loss, automation boundaries |

## NIST AI RMF Mapping

NIST AI RMF is organized around risk-management functions such as governance, mapping, measurement, and management.

ASA 5 can support these functions as a runtime evidence layer.

### Govern

ASA 5 supports governance by keeping the security layer external to the observed AI runtime.

Relevant ASA 5 surfaces:

- operator-facing security console
- human-owned policy authority
- audit review path
- bounded autonomous response model
- separation between AI runtime and security signal generation

### Map

ASA 5 supports system mapping by requiring stable runtime and session context.

Relevant ASA 5 surfaces:

- runtime identity
- session identity
- task frame
- policy context
- event ordering
- source and actor metadata

### Measure

ASA 5 supports measurement by converting runtime behavior into trajectory security states.

Relevant ASA 5 surfaces:

- drift and integrity signals
- trajectory compression indicators
- correction integrity signals
- recovery loss signals
- pre-incident and incident-active classification
- evidence export

### Manage

ASA 5 supports risk management by making detected instability actionable.

Relevant ASA 5 surfaces:

- escalation queue
- auto escalation for bounded critical incidents
- downstream security routing
- operator review
- audit trail
- evidence packets for external review

## CSA AI Controls Matrix Mapping

The CSA AI Controls Matrix is a vendor-agnostic framework for cloud-based AI systems and includes control objectives, implementation guidance, auditing guidance, and mappings to other standards.

ASA 5 can support CSA-style control implementation and evidence generation in areas such as:

- runtime monitoring
- operational accountability
- security event evidence
- auditability
- security response routing
- policy-bound autonomous response
- separation of concerns between AI runtime and security control layer

ASA 5 should be understood as a supporting control layer, not as a claim of complete CSA AICM compliance by itself.

## OWASP AISVS Mapping

OWASP AISVS is a catalogue of testable security requirements for AI-enabled systems and includes areas such as model behavior and safety assurance, autonomous orchestration, monitoring, logging, anomaly detection, and human oversight.

ASA 5 is most directly relevant to:

- monitoring, logging, and anomaly detection
- human oversight and trust
- autonomous orchestration and agentic action security
- model behavior, output control, and safety assurance
- infrastructure, configuration, and deployment security boundaries

ASA 5 focuses on trajectory-level runtime behavior.

It is not only an input/output filter. It observes how a runtime evolves across a sequence and flags instability before visible failure becomes obvious.

## SOC / SIEM Integration Surface

ASA 5 states can be mapped into enterprise security workflows.

Example mapping:

| ASA 5 state | Enterprise interpretation | Example action |
| --- | --- | --- |
| `watch` | low-level trajectory signal | monitor and retain evidence |
| `elevated` | increased instability or policy pressure | notify operator or increase sampling |
| `pre-incident` | security-relevant early warning | route to review queue |
| `incident-active` | critical runtime integrity event | escalate to security owner or downstream security automation |

ASA 5 can provide structured records for integration with:

- SOC workflows
- SIEM pipelines
- audit systems
- case management
- incident reconstruction
- policy review

## Bounded Autonomous Response

ASA 5 supports autonomous response only as a bounded security pathway.

Public-safe boundary:

- automatic action is limited to configured response profiles
- critical incidents can be routed to downstream security automation
- operator review remains required
- policy authority remains human-owned
- post-event evidence remains available for audit

The goal is not uncontrolled autonomous enforcement.

The goal is to preserve response time in high-volume or critical conditions while keeping accountability, review, and policy authority outside the AI runtime.

## Telemetry Dependency

ASA 5 detection quality depends on telemetry quality.

This is an intentional enterprise boundary.

ASA 5 does not need internal model access, but enterprise deployment requires a stable external view of runtime behavior.

Minimum useful telemetry includes:

- ordered events
- reliable timestamps
- stable runtime and session identifiers
- task or policy frame
- action/tool metadata where available
- correction and handoff markers
- risk or policy metadata where available

For more detail, see:

- [ASA 5 Runtime Telemetry Requirements](ASA5_RUNTIME_TELEMETRY_REQUIREMENTS.md)
- [ASA 5 Enterprise Deployment Principles](ASA5_ENTERPRISE_DEPLOYMENT_PRINCIPLES.md)
- [ASA 5 Enterprise Scalability Principles](ASA5_ENTERPRISE_SCALABILITY_PRINCIPLES.md)

## Compliance Boundary

ASA 5 does not claim standalone compliance with NIST AI RMF, CSA AI Controls Matrix, OWASP AISVS, or any other framework.

ASA 5 can support enterprise compliance and assurance programs by providing:

- runtime security evidence
- trajectory integrity signals
- escalation records
- audit artifacts
- operator review state
- bounded autonomous response records

The correct enterprise framing is:

`ASA 5 supports control evidence and runtime security workflows for AI systems.`

