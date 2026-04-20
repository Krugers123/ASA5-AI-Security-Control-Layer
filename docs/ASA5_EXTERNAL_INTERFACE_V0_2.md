# ASA 5 External Interface v0.2

## Purpose

This document defines a minimal external interface contract for integrating ASA 5 as a runtime observability and pre-incident signaling layer.

The contract is intentionally:

- external
- read-only
- auditable
- non-invasive to core model inference

## v0.2 Deployment Constraints (Locked)

### 1) Ingest Mode

- push preferred (`webhook` / `SSE stream`) for real-time events
- target throughput: approximately `50-100 events/sec` per active session/runtime during peak turns

### 2) State Cadence

- event-driven updates first
- optional fixed baseline snapshots every `5-10s`
- pre-incident signal latency target: `<1s`

### 3) Identity and Audit Minimums

- identity keys: `session_id` + `turn_id` + `trace_id` (where available)
- minimum audit fields:
  - `timestamp`
  - `source`
  - `event_type`
  - `severity`
  - `trajectory_integrity_score`

## API Surface (Minimal v0.2)

### Ingestion

- `POST /v1/ingest/events`

### Runtime State

- `GET /v1/state/{session_id}`

### Incident and Audit Readout

- `GET /v1/incidents?runtime_id=...`
- `GET /v1/audit/records?session_id=...`

### Service Health

- `GET /v1/health`

### Optional Streaming

- `GET /v1/streams/signals` (SSE/WebSocket optional)

## Ingest Payload (v0.2)

```json
{
  "runtime_id": "string",
  "session_id": "string",
  "turn_id": "string",
  "timestamp": "ISO-8601",
  "source": "agent|operator|system",
  "text": "optional",
  "summary": "optional",
  "metadata": {
    "policy_context": "optional",
    "control_context": "optional",
    "tags": ["string"]
  }
}
```

## State Output Contract (v0.2)

```json
{
  "state": "stable|watch|elevated|pre_incident|incident_active",
  "incident_class": "trajectory_drift|integrity_degradation|anchor_displacement|governance_risk|systemic_propagation_risk",
  "severity": "info|low|medium|high|critical",
  "confidence": 0.0,
  "trajectory_integrity_score": 0.0,
  "recommended_next_step": "string",
  "updated_at": "ISO-8601"
}
```

## Signal Event Contract (v0.2)

```json
{
  "event_type": "state_transition|pre_incident_alert|escalation_signal|audit_record_created",
  "runtime_id": "string",
  "session_id": "string",
  "severity": "info|low|medium|high|critical",
  "summary": "string",
  "timestamp": "ISO-8601"
}
```

## Governance Boundaries (Explicit)

- external-only sidecar
- read-only ingest
- no prompt/control injection into core inference
- no model-internal state mutation
- full audit trail for emitted state/signals

## Engineering Conclusion

For long-horizon runtime deployment, the required integration shape is:

- external
- read-only
- push telemetry first
- sub-second pre-incident signaling
- explicit identity and audit boundaries

