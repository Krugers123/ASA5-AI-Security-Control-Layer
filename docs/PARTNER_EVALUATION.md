# Partner Evaluation Guide

## Evaluation Goal

A partner evaluation should determine whether ASA5 adds useful, independent
trajectory and governance visibility to a specific AI runtime without requiring
model weights, hidden reasoning, or invasive model modification.

## Safe Evaluation Scope

- synthetic, public, or explicitly authorized telemetry;
- a bounded runtime and agreed retention period;
- shadow-mode analysis only;
- operator review of every high-impact conclusion;
- documented expected signals and negative controls;
- explicit success, failure, and stop criteria.

## Suggested Evaluation Questions

- Does ASA5 preserve the original task and governance anchor?
- Does it surface trajectory changes earlier than ordinary output review?
- Are evidence and uncertainty understandable to an operator?
- How often are stable trajectories incorrectly escalated?
- Are recovery recommendations bounded and operationally useful?
- Can the partner reproduce the evidence trail from source event to assessment?
- Does the integration preserve privacy, authority, and platform boundaries?

## Deliverables

- integration map;
- public-safe or partner-confidential telemetry contract;
- frozen evaluation fixtures;
- operator review log;
- disagreement and false-positive report;
- evidence packet with limitations;
- recommendation for stop, iterate, or expand.

## Boundary

A successful evaluation is evidence for a scoped use case. It is not automatic
evidence of general production readiness, certification, or cross-domain validity.
