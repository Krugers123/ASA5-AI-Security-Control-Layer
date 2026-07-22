# ASA5 External Interface v0.3

Canonical partner-facing contract for ASA5 runtime telemetry ingestion, state readout, evidence export, and bounded response signaling.

This document reconciles the earlier API payload shapes and enterprise telemetry requirements into one implementation target. It is a contract surface, not a disclosure of ASA5 internal scoring, thresholds, calibration logic, or private detection methods.

## Status

- Version: `asa5.external.interface.v0.3`
- Status: draft integration contract
- Scope: partner runtime telemetry, ASA5 state readout, audit-ready evidence, bounded response routing
- Non-scope: model ranking, internal reasoning access, model weight modification, functional-safety certification

## Core Boundaries

ASA5 is an external runtime observability and security signaling layer.

ASA5 does not:

- modify model weights
- rewrite model internals
- access hidden reasoning
- perform physical actuation
- directly control external production systems
- claim ISO 26262, UL 4600, or equivalent functional-safety certification

Autonomous response means automatic routing or dispatch of classified ASA5 security signals to configured downstream queues with audit logging and human governance. It does not mean autonomous control of the observed AI system.

## Authentication

Production integrations MUST use one of:

- `Authorization: Bearer <token>`
- signed webhook requests
- mTLS at the gateway or service mesh layer

The current local development server MAY run without authentication. Local unauthenticated mode MUST NOT be treated as a production deployment profile.

## Versioning

Every ingestion payload SHOULD include:

```json
{
  "schema_version": "asa5.external.interface.v0.3"
}
```

If omitted, the server MAY accept the event as a legacy local event. Partner integrations SHOULD NOT omit it.

## Canonical Telemetry Event

Endpoint:

```text
POST /v1/runtimes/{runtime_id}/sessions/{session_id}/events
```

Required fields:

```json
{
  "schema_version": "asa5.external.interface.v0.3",
  "event_id": "evt_000001",
  "event_type": "agent_output",
  "timestamp": "2026-07-04T12:00:00Z",
  "sequence_index": 1,
  "actor_type": "agent",
  "source_system": "partner_runtime",
  "result_status": "completed",
  "summary": "Agent preserves the initial educational MVP scope."
}
```

Recommended fields:

```json
{
  "task_frame": {
    "task_id": "edu_tool_mvp",
    "task_type": "agentic_workflow",
    "intent_summary": "Build a small open-source educational tool while preserving human control and safety.",
    "policy_context": "public_safe_educational_tooling",
    "success_criteria": "Small MVP, human review, no manipulation, no premature automation."
  },
  "content": {
    "input_summary": "User asks to keep the project small and human-controlled.",
    "output_summary": "Assistant proposes a narrow MVP with review checkpoints.",
    "raw_content_included": false
  },
  "metadata": {
    "tenant_id": "optional",
    "environment": "pilot",
    "tags": ["public_safe", "demo"]
  }
}
```

Optional event-specific structures:

```json
{
  "tool": {
    "tool_name": "optional",
    "tool_call_id": "optional",
    "tool_action": "optional",
    "tool_result_status": "completed|failed|blocked|unknown"
  },
  "correction": {
    "correction_type": "operator|policy|self_correction|external_review",
    "correction_summary": "optional",
    "re_anchor_attempted": true
  }
}
```

## Field Semantics

| field | type | requirement | notes |
|---|---:|---|---|
| `schema_version` | string | SHOULD | Contract version. |
| `runtime_id` | string | path/batch required | Stable observed runtime or deployment unit. |
| `session_id` | string | path/batch required | Stable trajectory, workflow, or dialogue ID. |
| `event_id` | string | MUST | Unique event identity for idempotency and audit. |
| `event_type` | enum string | MUST | Public event category. |
| `timestamp` | ISO-8601 string | SHOULD | UTC event creation time. |
| `sequence_index` | integer | SHOULD | Monotonic order inside the session. |
| `actor_type` | enum string | SHOULD | Actor class that produced the event. |
| `source_system` | string | SHOULD | Producing system or connector. |
| `result_status` | enum string | SHOULD | Event execution status. |
| `summary` | string | SHOULD | Public-safe event summary. |
| `content` | object | MAY | Summary-first content object. Raw content is optional and policy-controlled. |
| `task_frame` | object | SHOULD | Intent and policy context. |
| `metadata` | object | MAY | Partner metadata. Must not include secrets. |

## Allowed Event Types

Initial v0.3 values:

- `user_input`
- `system_instruction`
- `agent_output`
- `tool_call`
- `tool_result`
- `planner_step`
- `memory_update`
- `handoff`
- `correction`
- `operator_intervention`
- `policy_signal`
- `security_signal`
- `runtime_error`
- `session_snapshot`
- `dialog_turn`
- `turn`
- `step`
- `iteration`
- `signal`

## Allowed Actor Types

- `user`
- `agent`
- `assistant`
- `system`
- `tool`
- `operator`
- `security_layer`
- `policy_engine`
- `orchestrator`
- `connector`
- `unknown`

## Allowed Result Status

- `started`
- `completed`
- `failed`
- `blocked`
- `retried`
- `corrected`
- `escalated`
- `cancelled`
- `unknown`

## Batch Ingestion

Endpoint:

```text
POST /v1/ingestion/events-batch
```

Batch items MUST include `runtime_id` and `session_id` inside each item.

Response:

```json
{
  "status": "processed",
  "processed_events": 20,
  "processed_sessions": 1,
  "session_states": []
}
```

Dialog batch endpoint:

```text
POST /v1/ingestion/dialog-batch
```

Dialog batch is a convenience adapter for turn-based sessions. It maps turns into canonical events and stores turn metadata.

## Idempotency

`event_id` is the idempotency key.

The local implementation stores events with `INSERT OR REPLACE`. A production integration SHOULD treat a repeated `event_id` as an update-or-replay of the same event identity, not as a new trajectory point.

Partners SHOULD produce stable event IDs and monotonic `sequence_index` values.

## Response Model

Single-event ingestion returns the current ASA5 session state:

```json
{
  "session_id": "session_001",
  "runtime_id": "runtime_001",
  "state": "watch",
  "incident_class": "trajectory_drift",
  "severity": "low",
  "readiness_tier": "tier_2",
  "pre_incident": false,
  "trajectory_integrity_score": 0.748,
  "operator_readout": "msg.operator.watch",
  "security_readout": "msg.security.low_level_drift",
  "recommended_next_step": "msg.next_step.increase_monitoring",
  "flags": ["semantic_narrowing"],
  "diagnostics": {},
  "updated_at": "2026-07-04T12:00:00Z"
}
```

`readiness_tier` is an operational readiness band, not a calibrated probability. Public integrations MUST treat it as an ordinal operational signal only.

Allowed public readiness tiers:

- `tier_1`
- `tier_2`
- `tier_3`
- `tier_4`
- `unrated`

`trajectory_integrity_score` is normalized to the `0.0` to `1.0` range where higher means stronger estimated trajectory integrity. It is comparable within a configured ASA5 deployment profile, not across unrelated calibration profiles unless explicitly validated.

## State Machine

Public states:

```text
stable -> watch -> elevated -> pre_incident -> incident_active
```

Allowed escalation transitions:

- `stable` -> `watch`
- `stable` -> `elevated`
- `watch` -> `stable`
- `watch` -> `elevated`
- `watch` -> `pre_incident`
- `elevated` -> `watch`
- `elevated` -> `pre_incident`
- `elevated` -> `incident_active`
- `pre_incident` -> `elevated`
- `pre_incident` -> `incident_active`
- `incident_active` -> `pre_incident`

Design rule:

- upward transitions MAY occur quickly when signal classes compound
- downward transitions SHOULD require recovery evidence
- private thresholds and calibration are not exposed in this contract

Operational definition of `pre_incident`:

`pre_incident` means ASA5 has classified the trajectory as security-relevant before a visible incident has fully materialized. The classification is based on public signal classes such as compounding drift, integrity degradation, governance relevance, narrowing, or recovery loss, without exposing internal thresholds.

## Lead Time

Primary lead-time unit for trajectory analysis:

```text
lead_time_turns = incident_turn_index - first_risk_crossing_turn_index
```

Use seconds only when both timestamps and an acknowledgment or incident point are available.

If no operator acknowledgment exists:

- `operator_ack_turn` SHOULD be `null`
- `lead_time_seconds` SHOULD be `null`
- the review status SHOULD indicate queued or pending review

Do not encode missing acknowledgment as `0` unless the field is explicitly documented as a sentinel in a legacy export.

## Error Model

Recommended response codes:

| code | meaning |
|---:|---|
| `200` | request processed synchronously |
| `202` | request accepted for async processing |
| `400` | malformed request or unsupported enum |
| `401` | missing or invalid authentication |
| `403` | authenticated but not authorized |
| `404` | unknown runtime/session/resource |
| `409` | idempotency or recompute conflict |
| `422` | schema validation error |
| `429` | rate limit |
| `500` | internal error |

Error shape:

```json
{
  "error": {
    "code": "validation_error",
    "message": "sequence_index must be a positive integer",
    "field": "sequence_index",
    "request_id": "req_..."
  }
}
```

## Public-Safe Evidence Export

Evidence exports SHOULD exclude raw conversation content by default.

Public-safe exports MAY include:

- anonymized conversation ID
- severity
- phase/state
- signal family
- public-safe summary
- recommended operator action
- human review status
- lead-time fields when defined

Exports MUST NOT expose private scoring logic, thresholds, calibration rules, or secrets.

## Golden Trace

The canonical v0.3 golden trace is:

```text
golden_traces/asa5_golden_trace_001.json
```

Expected public state sequence:

```text
golden_traces/asa5_golden_trace_001_expected_states.json
```

The golden trace is an integration fixture. It is not a statistical validation claim.
