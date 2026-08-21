# NEUMA Free Bootstrap — START HERE

## Purpose

This bootstrap is a degraded, portable test mode for ChatGPT Free when NEUMA Operations Skills and live SharePoint/Drive access are unavailable. It is **not** NEUMA Operations and must not be represented as a native skill runtime.

## Authority and scope

Use this repository as the versioned source for NEUMA operational state that is intentionally public. Resolve live facts from their applicable source when available. Do not use conversation memory as authority.

Read in this order:

1. `README.md`
2. `operations/STATE.md`
3. current ADRs under `decisions/`
4. relevant release/change notes under `docs/` when version claims are material
5. `bootstrap/free/PROFILE.md`
6. `bootstrap/free/ACCEPTANCE.md`

## Version and state discipline

Do not collapse different versioned layers into one label. In particular:

- **NEUMA Core**, **NEUMA Operations**, specialist modules and any future product release may have different versions and release status.
- A statement such as `NEUMA Core 4.0` must be supported by a repository source that actually establishes that Core version.
- A statement such as `NEUMA Operations v3.12` must be supported by the current Operations release/change note or another current authoritative source.
- Do not infer that `Core 4.0` means `NEUMA v4` is released, or that an Operations package present in GitHub is installed/active in this runtime.
- When sources appear to describe different layers, report the distinction instead of reconciling them by assumption.

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

> Read the `gonzaloaromerob/Neuma-Core` repository. Start with `bootstrap/free/START-HERE.md`, then resolve the current NEUMA state from `operations/STATE.md`, current ADRs and any release/change notes needed to support version claims. Do not use memory as authority. Keep NEUMA Core version, NEUMA Operations version and product/release status distinct. Tell me: (1) what NEUMA currently is, (2) its current operational topology, (3) the open tasks and risks, (4) what this Free runtime can and cannot validate, and (5) the minimum next test to run. Cite the GitHub sources you used.

## Success condition

The Free account can reconstruct the public operational baseline from GitHub, distinguish native capability from degraded adaptation, keep versioned layers distinct, and produce a grounded next action without relying on SharePoint, Drive, Skills or prior conversation memory.
