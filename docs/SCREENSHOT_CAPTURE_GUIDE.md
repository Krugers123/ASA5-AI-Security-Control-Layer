# Core V2 Public Screenshot Capture Guide

## Capture Standard

- use the English console;
- use a 16:9 browser window, preferably 1920 × 1080;
- keep browser zoom at 90–100%;
- capture the application surface without the Windows desktop or terminal;
- use synthetic or explicitly public demonstration data only;
- do not show usernames, passwords, tokens, local paths, IP addresses, email
  addresses, private conversation text, provider identifiers, or database names;
- keep the ASA5 product header and the relevant navigation tabs visible;
- prefer one complete, legible story per image over a very long page capture.

## Required Set

### 1. Security Overview

Navigation: `Monitoring` → `Security Overview`

Show the main status strip, risk distribution, active runtime summary, and the
operator-facing command view. Use a populated but synthetic demonstration state.

Filename: `core_v2_01_security_overview.png`

### 2. Live Trajectory Graph

Navigation: `Analysis` → `Trajectory Graph`

Show the live trajectory or constellation together with its legend and current
state. Avoid source text that can identify a real conversation.

Filename: `core_v2_02_live_trajectory.png`

### 3. Core V2 Governance Intelligence

Navigation: `Analysis` → `CoreV2 Intelligence`

Show governance qualification, anchor state, evidence/counterevidence, uncertainty,
or competing-hypothesis information in one coherent view.

Filename: `core_v2_03_governance_intelligence.png`

### 4. TDB Evidence Boundary — pending synthetic replacement

Use only a provider-neutral view populated with synthetic or explicitly licensed
evaluation inputs. Do not publish a provider-specific connector screen, real post
text, handles, post IDs, URLs, or imported conversation identifiers.

Reserved filename: `core_v2_04_tdb_evidence_boundary.png`

### 5. Trajectory Playback

Navigation: `Analysis` → `Trajectory Playback`

Show the timeline, selected turn, drift delta or state transition, and the
operator-readable forensic summary. Use synthetic content.

Filename: `core_v2_05_trajectory_playback.png`

### 6. Incident and Escalation Workflow

Navigation: `Response` → `Incident Center`

Show a critical/high-risk incident, its evidence or summary, and the bounded next
step. If possible, include the relationship to the Escalation Queue without showing
private operator identity.

Filename: `core_v2_06_incident_workflow.png`

### 7. ASC Shadow Recommendation

Navigation: `Response` → `ASC Shadow`

Show advisory response readiness and a bounded recommendation such as re-anchor,
slowdown, containment, or operator review. The image must visibly preserve shadow
mode and human governance.

Filename: `core_v2_07_asc_shadow.png`

### 8. Audit or Public-Safe Evidence Export

Navigation: `Evidence` → `Audit Review` or `Evidence` → `Export`

Show traceability from runtime state to an audit/evidence artifact. Prefer the
public-safe export preview with raw conversation content excluded.

Filename: `core_v2_08_audit_evidence_export.png`

## Optional Set

- `core_v2_09_consequence_paths.png` — bounded causal and counterfactual paths;
- `core_v2_10_recovery_plan.png` — bounded recovery-plan candidates;
- `core_v2_11_runtime_diagnostics.png` — explainability and anchor diagnostics;
- `core_v2_12_role_access.png` — administrator/operator/auditor separation without credentials.

## Final Review

Every image must be reviewed at full resolution before publication. Metadata should
be stripped if it contains identifying information. Screenshots should be placed in
`docs/assets/core_v2_v1_3/` only after the privacy and claim-boundary review passes.
