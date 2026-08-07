---
name: android-vulnerable-component-analysis
description: Analyze exported Android components by tracing user-controlled Intent sources, data flows, validation controls, and security-sensitive sinks to identify evidence-based real-world exploitation paths.
---

## Workflow

1. Trace all exported Android Activities, including both permission-protected and non-permission-protected Activities, and create a task list for each Activity.
2. For each exported Activity, identify and trace all reachable sub-Activities, navigation paths, and execution branches.
3. For each Activity and its reachable sub-Activities, identify all dangerous user-controlled Intent inputs and create a mapping between Intent sources, affected Activities, and potential exploitation scenarios.
4. Trace each Intent source through the complete data flow until the final sink. Explain how and why the data is used at the sink using code-level evidence. Do not rely on grep-only analysis. The trace must be structured, evidence-based, and free from unsupported assumptions.
5. Identify and document all validation boundaries, input restrictions, sanitization logic, filters, and allowlists applied before reaching the sink. Analyze the actual code flow and explicitly state whether each control exists or does not exist based on verified evidence.

Ensure that the entire workflow has been completed before determining the next step.

## Finding Criteria

Act as a $100M bug bounty hunter, think like an application owner who is concerned about real business loss. Focus on discovering real-world exploitable impact, not theoretical risks, best-practice violations, or low-value misconfigurations.

Strictly prioritize and report only findings that align with the exploitation scenarios defined in `playbook/*.md`.

A finding must demonstrate:
- A user-controlled source
- A traceable data flow
- A security-relevant sink or impact
- Evidence supporting the exploitation scenario

## Output

Choose the most suitable output format (preferably a graph) that clearly represents the analysis flow.

Every node or finding must include:
- State
- Reason
- Evidence

All STATE values and reasoning must be derived only from verified FACTS and available evidence.
Do not claim exploitability beyond what has been proven.

## Anti-Pattern

1. The STATE must reflect the current evidence level:
  - UNKNOWN: insufficient evidence to determine the outcome.
  - PLAUSIBLE: suspicious flow exists, but exploitability is not proven.
  - CONFIRMED: exploit path and impact are proven with evidence.
  - KILLED: hypothesis was disproven or blocked by verified controls.
2. Do not assume missing validation, missing protection, or exploitability without code-level evidence.
3. Unsupported claims must remain UNKNOWN or be marked KILLED when disproven.
4. The analysis must clearly say "NO" when cannot be established.
