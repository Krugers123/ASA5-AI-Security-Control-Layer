# ASA 5 Public Protocol Overview

## Purpose

ASA 5 uses protocol layers to turn trajectory reading into security-relevant structure.

The public layer does not expose full protocol internals.
It exposes only the main protocol logic in partner-safe form.

## Public Protocol Families

### LTP-S

Threshold-sensitive logic for detecting when stable runtime behavior begins to move into a security-relevant instability zone.

### TIRP

Trajectory Integrity Risk Protocol.
Used to classify degradation of trajectory integrity across time.

### PISP

Pre-Incident Signal Protocol.
Used to identify security-relevant warning signals before visible incident state.

### SIGMA

Security Integration and Governance Mapping Architecture.
Used to connect ASA 5 outputs with policy, SOC, and governance surfaces.

### AGP

Authority and Governance Protocol.
Preserves operator and governance relevance across the security layer.

## Public Reading

Together, these protocols allow ASA 5 to act not only as an observability layer, but as a security-relevant trajectory interpretation layer.
