# Project bootstrap and artifact governance

## Scope
This architecture note records the public/versionable boundary for NEUMA project bootstrap and artifact governance. It does not duplicate the internal SharePoint corpus or presentation templates.

## Source-of-record boundaries
- **SharePoint** remains the SoR for the internal NEUMA governance corpus, the current Project Core, artifact standards/templates, and project-specific rector documents.
- **GitHub** records only deliberately versionable/publicable architecture and technical conventions.
- **Notion** remains the operational SoR for projects, relations, risks, tasks, Decision Gates and execution tracking.

## Project bootstrap contract
A governed project uses one autosufficient rector document named `<Project> - Inst Proyecto.DocX` in its canonical SharePoint repository. At creation or material update it incorporates the then-current NEUMA Project Core plus project-specific rules and the canonical repository reference. The ChatGPT Project instruction field should need only a minimal pointer to that rector and repository; the rector need not be uploaded as a Project source.

The embedded Core is a **baseline**, not an assertion of perpetual synchronization. Material Core changes should trigger a controlled rector refresh when relevant.

## Artifact governance contract
Project artifacts resolve their canonical standards/templates from the NEUMA SharePoint corpus before generation when available. Current governed families are DOCX, XLSX, PPTX and controlled PDF outputs. Format-specific technical skills and explicit deliverable instructions take precedence over presentation defaults.

Execution follows: `resolve SoR -> inspect current state -> select governed standard -> generate minimum artifact -> format-specific QA -> persist -> verify`.

## Idempotency and divergence
Repeated bootstrap runs resolve the same rector by stable identity and should become no-ops when no material change exists. Independent human edits are not silently overwritten; material divergence is treated as a conflict requiring reconciliation.

## Security and publication boundary
Do not copy internal templates, confidential project content, credentials, personal data or the complete internal governance corpus into this repository merely to make bootstrap convenient.
