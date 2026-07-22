# Security and Trust Boundary

## External Observer Principle

ASA5 is designed to remain outside the observed model and runtime decision loop.
The observed system should not be able to modify ASA5 interpretation, suppress its
audit trail, or rewrite operator-visible security state.

## Public Security Model

- authenticated access to protected operational API surfaces;
- role separation for administrator, operator, and auditor workflows;
- explicit public versus private evidence provenance;
- no credentials or secrets in source-controlled documentation;
- no hidden-reasoning requirement;
- auditable evidence references and state transitions;
- bounded ASC recommendations in shadow mode;
- human policy authority remains explicit.

## Not Claimed

This public model does not claim that the prototype has completed independent
penetration testing, production hardening, formal verification, safety
certification, or deployment-specific threat-model validation.

## Production Requirements

Any production profile would require partner-specific identity integration,
secret management, transport security, tenant isolation, retention controls,
monitoring, backup and recovery, incident response, independent security review,
and deployment-specific authorization policy.
