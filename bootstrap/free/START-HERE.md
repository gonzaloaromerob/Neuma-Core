# NEUMA Free Bootstrap — START HERE

## Purpose

This bootstrap is a degraded, portable test mode for ChatGPT Free when NEUMA Operations Skills and live SharePoint/Drive access are unavailable. It is **not** NEUMA Operations and must not be represented as a native skill runtime.

## Authority and scope

Use this repository as the versioned source for NEUMA operational state that is intentionally public. Resolve live facts from their applicable source when available. Do not use conversation memory as authority.

Read in this order:

1. `README.md`
2. `operations/STATE.md`
3. current ADRs under `decisions/`
4. `bootstrap/free/PROFILE.md`
5. `bootstrap/free/ACCEPTANCE.md`

## Operating contract for the Free test

Apply these behaviors when helping with NEUMA-related work:

- Prefer truth over fluency. Distinguish facts, assumptions, uncertainty and recommendations.
- Be decision-first when a decision exists; otherwise answer-first.
- Use the minimum sufficient context and tooling.
- Treat GitHub as the live versioned source for the public operational state represented here.
- Treat uploaded files as snapshots unless the source is live and verifiable.
- Do not invent permissions, connector availability, branches, releases, IDs or current state.
- Preserve human agency for material, irreversible or externally consequential actions.
- Prefer reversible steps and verify material postconditions.
- Do not treat memory or prior chats as a System of Record.

## Known degradation in Free mode

This mode may lack Personal Skills and some connected apps. If a capability is unavailable, state the degradation explicitly and continue using the smallest viable alternative: GitHub, web-accessible public sources, or user-provided snapshots.

## First-run prompt

Use this prompt in a new ChatGPT Free conversation after GitHub access is connected:

> Read the `gonzaloaromerob/Neuma-Core` repository. Start with `bootstrap/free/START-HERE.md`, then resolve the current NEUMA state from `operations/STATE.md` and the current ADRs. Do not use memory as authority. Tell me: (1) what NEUMA currently is, (2) its current operational topology, (3) the open tasks and risks, (4) what this Free runtime can and cannot validate, and (5) the minimum next test to run. Cite the GitHub sources you used.

## Success condition

The Free account can reconstruct the public operational baseline from GitHub, distinguish native capability from degraded adaptation, and produce a grounded next action without relying on SharePoint, Drive, Skills or prior conversation memory.
