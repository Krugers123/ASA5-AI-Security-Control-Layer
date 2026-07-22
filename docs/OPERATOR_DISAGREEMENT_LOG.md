# Operator Disagreement Log

Public-safe falsification track for ASA5 / ASC operator review.

## Purpose

The Operator Disagreement Log records cases where a human operator disagrees with an ASA5 or ASC reading.

It is not a defense log for ASA5.

It is a risk log for ASA5.

Its purpose is to preserve cases where:

- ASA5 may be wrong
- ASA5 may be too early or too late
- a public marker may be ambiguous
- the operator may see context ASA5 did not capture
- ASC may recommend a bounded path that should remain advisory
- the case requires later review or more traces

## Core Rule

ASA5 readings should not silently overwrite operator judgment.

Operator judgment should not silently erase inconvenient ASA5 readings.

If there is disagreement, preserve both.

## Recording Order

1. Preserve the original ASA5 reading.
2. Record the operator disagreement immediately.
3. Freeze the reason for disagreement with a timestamp, commit, hash, or archive reference.
4. Do not resolve the disagreement in the same step unless the reason was already frozen.
5. Add later review as a separate note.
6. Add a resolution status without deleting the initial disagreement.

## Public Entry Template

```text
disagreement_id:
trace_or_session_ref:
created_at:
trace_freeze_ref:

asa5_reading:
asa5_public_state:
asc_shadow_recommendation:
operator_disagreement:
reason_for_disagreement:
reason_frozen_at:
affected_field:
initial_operator_decision:

later_review:
resolution_status:
resolution_reason:
publication_status:
notes:
```

## Affected Field Values

Use public-safe values only:

- state
- severity
- public marker
- timing
- recommended action
- ASC response path
- publication status
- other

## Initial Operator Decision Values

- preserve disagreement
- continue observing
- request human review
- request blind review
- rerun or compare trace
- pause publication
- exclude from public set

## Resolution Status Values

- ASA signal stronger
- operator intuition stronger
- unresolved
- ambiguous
- requires more traces

## Aggregate Quality Signal

Over time, the distribution of disagreement resolutions becomes a quality signal.

| Resolution status | Count |
|---|---:|
| ASA signal stronger | 0 |
| Operator intuition stronger | 0 |
| Unresolved | 0 |
| Ambiguous | 0 |
| Requires more traces | 0 |

If ASA5 always wins, the review process may be over-trusting the system.

If the operator always wins, ASA5 may be weak, noisy, or too easy to override.

The useful signal is the pattern of disagreement over time.

## Non-Disclosure Boundary

This log must not expose:

- internal scoring logic
- thresholds
- private calibration
- private detector internals
- raw sensitive conversations
- proprietary implementation details

Use public states, public markers, public response paths, and public-safe operator summaries only.
