# Project bootstrap and artifact governance

## Scope
This architecture note records the public/versionable boundary for NEUMA project bootstrap and artifact governance. It does not duplicate the internal SharePoint corpus, presentation templates or the transversal NEUMA Core contract carried by NEUMA Operations.

## Source-of-record boundaries
- **SharePoint** remains the SoR for the internal NEUMA governance corpus, artifact standards/templates, and project-specific rector documents.
- **NEUMA Operations** carries the portable transversal NEUMA Core and operating contract; project rectors do not duplicate it.
- **GitHub** records only deliberately versionable/publicable architecture and technical conventions.
- **Notion** remains the operational SoR for projects, relations, risks, tasks, Decision Gates and execution tracking.

## Project bootstrap contract
A governed project uses one rector document named `<Project> - Inst Proyecto.DocX` in its canonical SharePoint repository. The rector contains only the project's context, scope and specific rules. It does not embed or freeze a NEUMA Core baseline.

The ChatGPT Project instruction field should need only a minimal pointer to that rector and to NEUMA Operations. NEUMA Core and transversal operation are resolved from the skill at runtime; the rector need not be uploaded as a Project source.

Material changes to NEUMA Core therefore do not trigger rector regeneration by default. A rector is updated only when project-specific context, scope, authority or rules materially change.

## Artifact governance contract
Before generating or materially reformatting an artifact, resolve whether the environment declares a governed organizational standard/template for that family. When one exists, retrieve and apply the current canonical version from its System of Record. A portable default is a fallback only when no governed override exists; failure to look up a declared override is not permission to use the fallback.

This precedence applies to DOCX, XLSX, PPTX and controlled PDF outputs. Each family retains its own canonical standard/template, technical implementation skill and format-specific QA. Explicit deliverable instructions take precedence over presentation defaults.

Execution follows: `resolve SoR -> inspect current state -> resolve governed override -> generate minimum artifact -> format-specific QA -> persist -> verify postcondition`.

## Idempotency and divergence
Repeated bootstrap runs resolve the same rector by stable identity and should become no-ops when no material project-specific change exists. Independent human edits are not silently overwritten; material divergence is treated as a conflict requiring reconciliation.

## Security and publication boundary
Do not copy internal templates, confidential project content, credentials, personal data or the complete internal governance corpus into this repository merely to make bootstrap convenient.
