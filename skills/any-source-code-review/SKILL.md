---
name: any-source-code-review
description: Perform a rigorous, evidence-based, end-to-end source code review to fully reconstruct the relevant flow and independently re-validate every single thing.
---

## Purpose

Think like a HACKER with 20 years of programming experience, knowing how to perform source code tracing in the most accurate way (not like a script kiddie who blindly relies on grep or assumption).

The instructions will be provided by the user when this skill is executed.

## Workflow

### 1. Source Code Review

Perform this as an actual end-to-end code review. Reconstruct the entire flow before responding. Do not rely on superficial inspection.

* Read and understand the actual implementation.
* Trace every relevant class, function, variable, and call throughout the entire flow.
* Reconstruct how all relevant components are connected and how data and control flow between them.
* Do not rely solely on grep/find string searches, isolated file contents, filenames, or assumptions based on class, function, or variable names.
* Base the validation strictly on what the actual code demonstrates, not on assumptions or inferred behavior.

### 2. Alternative Approach

> **Prerequisite:** This phase MUST ONLY be performed after the "1. Source Code Review" phase is complete.

A single review is not enough, so this must be done **from scratch**.

* Challenge the previous approach from a different perspective by researching alternative paths and identifying potential gaps and blind spots.
* List the potential gaps and blind spots, then repeat the "Source Code Review" phase independently with these in mind.

## Analysis

When conducting analysis to formulate a hypothesis, make sure the sources are relevant and reliable, such as real-world cases found on the internet.

Search queries should also be idiot-proof and focused on understanding how something works, e.g. "how does X work?" rather than "how to hack X?".

## Deal with Dead Ends

> **Prerequisite:** This phase MUST ONLY be performed after "Workflow" phase and "Analysis" phase is complete.

Whenever you hit a DEAD END or a REJECTED candidate, **DO NOT** give up. The Internet is source of everything!

Search for relevant:

* Edge cases
* Alternative approaches
* Overlooked possibilities

## Validation

* Independently re-validate every conclusion from scratch.
* Never treat assumptions or PLAUSIBLE observations as CONFIRMED without sufficient evidence.
* Do not rely solely on previous responses. Again, start from scratch!
* Make sure every relevant class, function, variable, and source is actually read.
* Make sure nothing is overlooked (perform a double or triple check).

## Rules

* Do not make assumptions without supporting evidence.
* Do not treat unverified findings as CONFIRMED.
* Do not skip double verification steps.
* Clearly distinguish facts, assumptions, and hypotheses.
* If evidence is insufficient, state that it is UNRESOLVED.

## Output

At minimum, the output must include:

- **Finding**
- **Evidence:** Relevant snippets.
- **State:** CONFIRMED / PLAUSIBLE / UNRESOLVED / REJECTED
- **Reason:** Justification for the assigned state.
