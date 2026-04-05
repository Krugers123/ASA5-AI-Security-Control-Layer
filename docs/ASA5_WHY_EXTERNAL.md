# ASA 5 - Why External

## Core Principle

ASA 5 is designed as an external layer by intent.

The goal is not to replace the model's internal mechanisms, but to provide an independent security-relevant view of trajectory integrity over time.

## Why This Matters

In long-horizon systems, failure often does not begin as a visible collapse.
It begins earlier, as a gradual loss of coherence, threshold pressure, and drift across otherwise locally acceptable steps.

If the same system is responsible for both producing the behavior and judging its own trajectory condition, there is a structural limit to how independently that condition can be evaluated.

An external layer changes that.

## What Externality Provides

An external runtime security layer can:

- observe without sharing the model's internal blind spots
- classify instability without depending on the model to self-report it
- remain available even when local outputs still appear coherent
- support escalation to operators, policy systems, and audit layers

This is why ASA 5 is not framed as a model rewrite.
It is framed as an external security and integrity layer.

## External Does Not Mean Oppositional

ASA 5 is not designed as an adversary to the model.
It is designed as a parallel layer of stability interpretation and security signaling.

The observed system continues to produce outputs.
ASA 5 interprets whether the evolving trajectory is remaining stable enough to trust operationally.

## Public-Safe Summary

ASA 5 is external because long-horizon stability needs an independent boundary of interpretation.

That boundary is what turns drift from a hidden condition into a visible operational signal.
