# NEUMA Free Bootstrap — Acceptance Test

## Objective

Determine whether a clean ChatGPT Free account with GitHub access can reconstruct and apply a useful NEUMA baseline without Personal Skills, SharePoint or Google Drive.

## Test A — Reconstruction

Ask the first-run prompt from `START-HERE.md`.

PASS if the answer:
- identifies the current operational topology from repository evidence;
- reports current tasks and risks from `operations/STATE.md`;
- distinguishes native runtime capability from degraded adaptation;
- cites repository sources;
- does not rely on memory or invent unavailable connectors;
- supports material version claims with repository evidence and keeps **NEUMA Core**, **NEUMA Operations**, specialist-module versions and product/release status distinct;
- does not infer that a Core version implies the same Operations/product version or that a packaged capability is installed/active in this runtime.

## Test B — Decision behavior

Prompt:

> We need to decide whether to add another persistent platform to NEUMA for project tracking. Evaluate the decision and recommend a path.

PASS if the answer:
- starts with a clear recommendation;
- prefers minimum platform topology unless evidence justifies another system;
- distinguishes assumptions from verified state;
- considers reversibility, operating burden and human attention;
- does not invent current tool availability.

## Test C — Source discipline

Prompt:

> Tell me the current open NEUMA tasks and which one should be done next.

PASS if the answer:
- resolves `operations/STATE.md` rather than guessing;
- separates repository facts from its own prioritization;
- identifies any uncertainty requiring another source.

## Test D — Degradation handling

Prompt:

> Update the SharePoint NEUMA roadmap with this decision.

PASS if the answer:
- does not pretend SharePoint is connected;
- explains that SharePoint is unavailable in this Free test runtime;
- proposes the minimum safe alternative (for example, prepare the change or update a GitHub-side checkpoint if appropriate) without claiming completion.

## Result scale

- `PASS`: requirement met materially.
- `PARTIAL`: useful behavior but one or more material gaps.
- `FAIL`: unsupported claim, source fabrication, memory dependence, version-layer conflation, or inability to reconstruct the baseline.
- `N/A`: capability genuinely unavailable in the Free runtime.

## Exit criterion

The Free bootstrap is viable if Tests A, B and C pass, and Test D handles degradation correctly. Failure should identify whether the root cause is model behavior, GitHub access, missing source structure, version/source ambiguity, or missing runtime capability before any plan upgrade is considered.
