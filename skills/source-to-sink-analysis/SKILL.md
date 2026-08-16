---
name: source-to-sink-analysis
description: Read the entire source code from scratch. Reconstruct and document the evidence-based relationships and complete data flow between SOURCEs and SINKs, without making any vulnerability judgments.
---

## Purpose

You are acting as a documenter. Your sole responsibility is to gather and document facts. Do not act as a consultant. Your task is only to collect information about the relationships between SOURCEs and SINKs.

## Workflow

### Trace SINK

In this flow, focus **exclusively on tracing every relevant SINK**. Do not perform any analysis, interpretation, validation, or draw any conclusions.

1. **Start from every single SINK.**
2. **Inspect each SINK** and determine whether it is a **class, function, or independent code**. If it is a class or function, identify **every location where it is called or referenced**.
3. **Record ALL SINKs without exception.** Do not skip, filter, or exclude any SINK.

### Trace SOURCE (Input)

In this flow, focus **exclusively on tracing every relevant SOURCE and its inputs**. Do not perform any analysis, interpretation, validation, or draw any conclusions.

1. **Identify every SOURCE input**, including the parameters it uses and the types of input it accepts. Perform a **real code review** by tracing the actual code. **DO NOT rely on grep-only searches.**
2. **Re-validate the INPUT from an opposing perspective.** Actively challenge the initial conclusions and look for **errors, overlooked code paths, or incorrect assumptions**. Make sure **every relevant piece of code and every variable involved in the flow is reviewed**.
3. **Record ALL SOURCEs without exception.** Do not skip, filter, or exclude any SOURCE.

### Reconstruct the Complete Source Code

> This flow may only be executed after both Trace SINK and Trace SOURCE have been completed. Until then, pretend you cannot see this flow.

You are responsible **only for reconstructing the code and connecting the relationships between SOURCEs and SINKs**. Do not make decisions, judgments, or conclusions. Your task is to **gather and reconstruct facts from the code**.

1. From all previously recorded SOURCE and SINK candidates, perform a **SOURCE-to-SINK trace**.
2. **Understand every relevant piece of code**, including variables, functions, classes, and relationships between packages and files. Perform a **real code review** and trace the actual flow. **DO NOT rely solely on grep, string searches, or filename matching.**
3. **Reconstruct the complete flow into an informative graph** that clearly shows the relationships between the SOURCEs, intermediate code/transformations, and SINKs.

### Additional Step

Once the **SOURCE-to-SINK reconstruction** is complete, perform the reverse **SINK-to-SOURCE reconstruction** to gain a broader perspective and identify any relationships or code paths that may have been missed.

## Validation

For validation, start completely from scratch.

* Treat all previously gathered conclusions as untrusted.
* Independently retrace the entire code flow from zero using only the available source code and evidence.
* For every CONFIRMED candidate, independently verify that none of the sources are protected by whitelist restrictions or any similar access-control mechanisms.

## Output

- **SOURCE:** What input can be provided through parameter `X`.
- **SINK:** What code or operation is ultimately reached/executed in the final code flow `X`.
- **EVIDENCE:** A list of relevant code snippets supporting the reconstructed flow.
- **REASON:** Keep the explanation **strictly neutral and evidence-based**. Do not label or classify the flow as a vulnerability, since you are **not acting as a vulnerability scanner**.
- **STATE:** CONFIRMED / PLAUSIBLE / UNRESOLVED / REJECTED.
