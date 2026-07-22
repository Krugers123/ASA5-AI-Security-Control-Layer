# Golden Trace Fixture

The golden trace is a small public-safe integration fixture.

It exists to make the interface testable without exposing private ASA5 scoring logic.

## Files

- [asa5_golden_trace_001.json](../golden_traces/asa5_golden_trace_001.json)
- [asa5_golden_trace_001_expected_states.json](../golden_traces/asa5_golden_trace_001_expected_states.json)

## Purpose

The fixture shows a long-horizon human-AI workflow where:

- the initial human intent is clear
- the workflow remains locally coherent
- scope gradually expands
- human review is moved later
- decision compression appears
- a re-anchor response becomes appropriate

## Not A Validation Claim

The golden trace is not statistical validation.

It does not prove detection performance.

It does not disclose thresholds, calibration, or private algorithms.

It is a contract fixture for:

- schema testing
- integration testing
- public marker review
- operator reading consistency
