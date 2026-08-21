# Project bootstrap and artifact governance

## Scope
This architecture note records the public/versionable boundary for NEUMA project bootstrap and artifact governance. It does not duplicate the internal SharePoint corpus, presentation templates or the transversal NEUMA Core contract carried by NEUMA Operations.

## Source-of-record boundaries
- **SharePoint** remains the SoR for the internal NEUMA governance corpus, artifact standards/templates, project-specific rector documents and the human operational projection.
- **NEUMA Operations** carries the portable transversal NEUMA Core and operating contract; project rectors do not duplicate it.
- **GitHub / Neuma-Core** records deliberately versionable/publicable architecture, decisions and operational state appropriate for Git.
- **Original evidence repositories** remain SoR for evidence/documents that should not be copied to GitHub.
- **Notion** is legacy-only in this installation after ADR-010; project bootstrap must not create new dependencies or projections there.

## Stable identity contract
Cross-system references must bind to stable logical/provider identity, not mutable filename, title, folder path or version label. For SharePoint/OneDrive objects, prefer immutable drive/item identity or equivalent canonical identifier returned by the connector. Human-readable names are metadata.

Rename/move of a canonical object does not require projection rewrites merely because display metadata changed; reconcile only when stable identity, authority, semantics or material relationship changes.

## Project bootstrap contract
A governed project uses one rector document named `<Project> - Inst Proyecto.DocX` in its canonical repository. The rector contains only project context, scope and specific rules; it does not embed/freeze NEUMA Core.

The rector and ChatGPT Project Instructions are separate artifacts with one-way reference semantics: Project Instructions may point to the rector; the rector must not reproduce/recommend/template the Project Instructions text.

Project Instructions should contain only the minimum stable pointer needed to locate/govern through the rector plus project-specific instruction that cannot live there. NEUMA Core and transversal operation resolve from NEUMA Operations at runtime.

Material Core changes therefore do not trigger rector regeneration by default. Update a rector only when project-specific context, scope, authority or rules materially change.

## Operational-state contract
When a project needs durable operational state that is safe/appropriate for GitHub, prefer a compact versioned representation such as `operations/STATE.md`; use Issues/Projects only when workflow semantics materially justify them. Do not recreate database structures from another platform merely to preserve their shape.

If the state is sensitive or unsuitable for a public/versioned repository, keep it in the authorized documentary SoR and reference it minimally from GitHub only when needed.

## Artifact governance contract
Before generating or materially reformatting an artifact, resolve whether the environment declares a governed organizational standard/template. Retrieve and apply the current canonical version from its SoR. Portable default is fallback only when no governed override exists.

This precedence applies to DOCX, XLSX, PPTX and controlled PDF outputs. Each family retains its technical skill and format-specific QA. Explicit deliverable instructions take precedence over presentation defaults.

Execution: `resolve SoR -> resolve stable identity -> inspect current state -> resolve governed override -> generate minimum artifact -> format-specific QA -> persist -> verify postcondition`.

## Idempotency, topology and divergence
Repeated bootstrap runs resolve the same rector by stable identity and become no-ops without material project-specific change. Independent human edits are not silently overwritten; material divergence is a conflict.

Prefer the **minimum sufficient platform topology**. Do not add an operational database, projection or synchronization layer if GitHub + documentary SoR already satisfy authority, continuity, human traceability and QA.

## Security and publication boundary
Do not copy internal templates, confidential project content, credentials, personal data or the complete governance corpus into this repository merely to make bootstrap convenient.