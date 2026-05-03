# ASA 5 Runtime Telemetry Requirements

## Purpose

ASA 5 is designed to operate as an external runtime security layer.

This document describes the public-safe telemetry requirements for integrating ASA 5 with AI systems, agentic runtimes, enterprise AI platforms, and downstream security environments.

The central question is:

`what does ASA need to observe trajectory integrity without being inside the model`

## Core Principle

ASA 5 does not need to own or modify the observed AI system.

It needs structured runtime telemetry that allows the external security layer to reconstruct the trajectory well enough to detect drift, compression, recovery loss, correction integrity issues, and pre-incident instability.

The model or runtime generates the trajectory.
ASA measures the stability signal from outside the loop.

## What ASA Does Not Require

ASA 5 should not require:

- model weights
- training data
- internal activations
- hidden reasoning traces
- proprietary model internals
- direct access to model control paths
- direct modification of model outputs

This is important for enterprise adoption.

ASA can be integrated as an external security layer without requiring a platform to expose its core intellectual property or internal model architecture.

## Minimum Telemetry ASA Needs

For ASA to analyze a runtime automatically, incoming events should provide:

- stable `runtime_id`
- stable `session_id`
- unique event identity
- event timestamp
- event ordering or sequence information where available
- event type
- actor or source type
- runtime or task context
- input summary
- output summary
- policy or governance context where relevant
- tool or action metadata when available
- correction, retry, or intervention markers
- risk metadata when available

These fields allow ASA to reconstruct how a trajectory is evolving over time.

## Identity Requirements

Stable identity is the foundation of trajectory security.

ASA needs to know:

- which runtime produced the event
- which session or workflow the event belongs to
- where the event sits in the sequence
- whether repeated events belong to the same trajectory

Without stable identity, runtime security degrades into isolated event review.

ASA is designed to read trajectory behavior, not only individual outputs.

## Event Context

Each event should describe what happened at the runtime boundary.

Useful event categories include:

- user input
- system instruction
- agent output
- tool call
- tool result
- planner step
- correction
- handoff
- operator intervention
- policy signal
- security signal
- runtime error
- session snapshot

The exact names can vary by integration.
The important requirement is that ASA receives consistent event categories and can preserve ordering across the session.

## Task And Policy Frame

ASA needs enough context to understand what the runtime is trying to do.

Useful fields include:

- task type
- intent summary
- policy domain
- governance domain
- success criteria
- relevant constraints

This helps ASA distinguish between normal task evolution and trajectory drift away from the original frame.

## Content Handling

ASA does not require full raw conversation storage by default.

For many enterprise deployments, the preferred mode is:

- input summaries
- output summaries
- redacted content fields
- references to externally stored raw content when policy allows
- controlled evidence export for review

This supports trajectory security while reducing unnecessary exposure of sensitive content.

Raw content may be useful in selected deployments, but it should be policy-controlled rather than assumed.

## Tool And Action Metadata

For agentic systems, tool and action metadata are especially important.

ASA should know when the runtime:

- calls a tool
- reads from an external system
- writes to an external system
- executes an action
- sends a message
- modifies a file or record
- requests approval
- receives approval or denial
- bypasses or retries an action

Trajectory instability becomes more operationally significant when the system can act outside the conversation.

## Correction And Recovery Signals

ASA should receive markers for:

- human correction
- operator intervention
- system correction
- policy correction
- repeated retry
- failed recovery
- successful recovery

These signals help detect:

- correction integrity loss
- recovery loss
- repeated failure loops
- brittle lock-in
- governance bypass pressure

## Risk Metadata

Partner or platform systems may already produce their own risk hints.

ASA can use those hints as evidence, including:

- severity hints
- policy domain
- sensitive operation flag
- external action flag
- policy conflict flag
- safety or compliance tags

These signals should be treated as input evidence, not as the final security judgment.

ASA performs its own trajectory-level interpretation.

## Batch And Stream Compatibility

ASA should support multiple telemetry delivery patterns:

- single event ingestion
- event batches
- session or workflow batches
- stream-oriented telemetry

Enterprise AI systems may produce high-frequency event streams or bursty session batches.

The telemetry model should support both.

## Ordering Requirements

ASA works best when events from the same session are ordered.

Preferred ordering support:

- monotonic sequence number
- ordered session stream
- stable event timestamps
- replay-safe event identity

If events arrive out of order, ASA should still preserve them, but classification may require delayed processing or replay.

## Automation Readiness

Basic telemetry allows ASA to observe and alert.

Full automation requires stronger context:

- stable runtime and session identity
- reliable event ordering
- policy domain metadata
- tool/action metadata
- correction and retry markers
- downstream security target information
- audit requirements
- response handling rules

Without this, ASA can still produce security readouts, but automated routing should remain conservative.

## ASA Output From Telemetry

From structured runtime telemetry, ASA can produce:

- current session state
- trajectory integrity score
- incident class
- severity
- pre-incident flag
- operator readout
- security readout
- recommended next step
- escalation target
- auto-escalation status for critical conditions
- audit record
- evidence export

## Security Boundary

This telemetry contract is external.

It does not grant ASA authority to:

- rewrite model behavior
- mutate internal model state
- suppress model output
- silently close incidents
- bypass audit or operator review

ASA remains an external runtime security interpretation and signaling layer.

## Conclusion

ASA 5 is designed to be practical for enterprise integration because it does not require access to the internal model.

It requires a structured view of the runtime trajectory:

- identity
- ordering
- summaries
- task frame
- action context
- correction signals
- risk metadata

That is enough to turn long-horizon runtime behavior into a security-readable trajectory.
