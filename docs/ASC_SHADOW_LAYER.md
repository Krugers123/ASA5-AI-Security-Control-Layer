# ASC Shadow Layer

ASC - Asymmetric Stability Crystallizer - is the bounded response and stabilization layer connected to ASA5.

In the current ASA5 Security Enterprise public surface, ASC is shown in shadow mode.

## Shadow Mode

Shadow mode means:

- ASC generates advisory decisions
- ASC records what it would recommend
- ASC does not execute the response
- operators can inspect response readiness
- audit visibility is preserved

The console phrase is intentional:

```text
ASC shadow decisions are not actions.
They show what ASC would recommend if active response were enabled.
```

## Response Paths

Public response path categories include:

- `no_action`
- `audit_ready_response`
- `re_anchor`
- `slowdown`
- `containment`
- `operator_review`

These are public categories, not private implementation logic.

## Boundary Rule

ASC must never be the first observer of instability.

ASC responds only to already classified ASA5 trajectory state.

## Public Example

In the ASA5 Security Enterprise dashboard, ASC shadow mode can summarize advisory recommendations across many sessions:

- total shadow decisions
- human review required
- audit required
- active recommendations
- distribution by ASA state
- distribution by ASC path
- decision log for operator inspection

This supports large-session visibility without exposing private scoring internals.
