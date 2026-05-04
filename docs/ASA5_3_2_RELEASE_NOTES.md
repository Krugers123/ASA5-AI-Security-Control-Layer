# ASA 5.3.2 Release Notes

ASA 5.3.2 extends `ASA 5 Security Enterprise` as an operator-facing runtime security console for higher-volume AI security review.

This release focuses on three areas:

- enterprise-scale operator visibility
- hybrid human/system incident response
- trajectory forensics and evidence export

## Public Demo State

The current public-safe demo surface shows:

- 500 monitored runtime sessions
- 70 live incidents
- 20 critical `incident-active` signals
- 50 high-risk `pre-incident` signals
- 20 critical incidents automatically dispatched by ASA
- 47 high-risk incidents reviewed and routed by a human operator
- 3 high-risk incidents still pending operator review
- 70 evidence records available for public-safe export

## What Changed

### Security Overview

The Security Overview now presents a clearer enterprise response state:

- critical incidents
- high-risk incidents
- human-processed incidents
- system auto-dispatched incidents
- pending operator review
- automatic dispatch timing

This makes the console easier to read as a command surface rather than a research dashboard.

### Trajectory Playback

ASA 5.3.2 introduces a public-safe `Trajectory Playback` view.

It reconstructs the externally observable runtime path of a selected session using stored runtime events and ASA diagnostics. The view includes:

- session selection and search
- reconstructed drift path
- turn-level drift pressure
- drift delta and momentum
- state transition markers
- selected-turn evidence detail
- pinned evidence export controls

The goal is not to expose hidden model reasoning. The goal is to give operators an external forensic reconstruction of how observable trajectory risk developed over time.

### Hybrid Incident Response

The demo now separates:

- automatic critical dispatch
- human review of high-risk signals
- pending operator workload

Critical incidents can be routed immediately to downstream security response. High-risk incidents remain suitable for human operator review, security-owner routing, policy review, and audit.

### Evidence Export

The evidence export path now reflects the expanded demo corpus:

- 500 sessions analyzed
- 70 evidence records
- critical and high events included
- raw conversation content excluded
- public-safe HTML/PDF/JSONL export path preserved

This strengthens the role of ASA 5 as an audit-supporting runtime security layer.

## Security Boundary

ASA 5 remains external to the observed model or runtime.

It does not require:

- model weights
- training data
- internal activations
- hidden reasoning traces
- direct model-output control

ASA 5 reads external runtime telemetry and turns trajectory instability into operator-visible security signals.

## Positioning

ASA 5.3.2 should be understood as a working external AI runtime security console.

It is designed to help security operators, SOC teams, safety reviewers, and governance owners see pre-incident trajectory risk before it becomes visible failure.
