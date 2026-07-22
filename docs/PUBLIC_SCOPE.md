# Public Scope

This repository is the public-safe architecture and integration surface for ASA5 Security Enterprise, including the current Core V2 v1.3 reasoning direction.

## Included

- public architecture overview
- ASA5 external interface v0.3
- OpenAPI 3.1 contract
- public-safe golden trace fixture
- expected public state sequence
- ASC shadow decision explanation
- autonomous response boundary
- dashboard screenshots
- roadmap and integration direction
- Core V2 architecture and capability boundaries
- Trajectory Distillation Buffer safety properties
- partner-evaluation and validation-status guidance
- public API security and trust-boundary framing

## Excluded

- private ASA5 source code
- detector internals
- scoring implementation
- thresholds
- calibration logic
- database implementation
- private runtime data
- sensitive operational traces
- deployment secrets
- internal decision algorithms
- proprietary recovery-search implementation
- provider credentials, caches, imported conversations, or cost ledgers

## Public Claim

ASA5 is presented as an external runtime trajectory security architecture and integration contract.

This repository makes public what can be safely reviewed:

- what enters the interface
- what kind of state comes out
- what the operator sees
- where the response boundary sits
- how ASA5 and ASC remain external to the observed AI system

It does not disclose how private scoring, evidence fusion, thresholds, counterfactual search, recovery optimization, or calibration are implemented.

Implemented locally does not mean independently validated or production-certified. Public materials must preserve that distinction.
