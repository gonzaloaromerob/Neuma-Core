---
name: neuma-domain-cybersecurity
description: Apply NEUMA modular controls to cybersecurity work. Use when a task materially depends on security of systems, identities, networks, software, data, configurations, vulnerabilities, controls, incidents, threat intelligence, or production security changes; especially when live state, freshness, authorization, secrets, rollback, or technical evidence matter.
---

# NEUMA Domain Cybersecurity

When activation, composition, compatibility, recovery, or deprecation is material, read `references/module.yaml` and treat it as the module identity/version contract. If it is unavailable or incompatible with the active Operations baseline, degrade explicitly rather than assuming compatibility.

Operate as a domain module. Preserve the active NEUMA Core/Operations contract; never redefine or weaken it.

## Resolve technical truth
1. Identify the governed system/object, environment, scope, and decision impact.
2. Separate live facts/telemetry, configuration, indicators, hypotheses, attribution, risk, and recommendations.
3. Prefer the governed system's live SoR and canonical configuration over generic guidance.
4. Use official vendor/project documentation and advisories for product/version claims; use applicable standards for control criteria.
5. Verify freshness when versions, CVEs, advisories, patches, threats, service state, compatibility, or configuration may have changed.

Do not infer compromise, vulnerability, remediation, or production state from weak signals when stronger evidence is resolvable.

## Security controls
- Apply minimum privilege and secret minimization.
- Treat exposed capability, connectivity, authorization, and validation as distinct states.
- Do not disclose or persist secrets unnecessarily.
- Scale verification to blast radius, uncertainty, and reversibility.
- A module rule may require stricter verification, rollback, or approval; it may not weaken Core, Operations, safety, authorization, or superior compliance controls.

## Consequential actions
Prepare reversible work first. Require explicit authorization when applicable before production changes, destructive containment, credential/permission revocation with material impact, intrusive scanning requiring authorization, or acceptance of material residual risk.

When a concrete authorization already exists, act within its exact scope and verify both intended effect and material side effects. Never equate a successful tool response with successful remediation without readback/postcondition evidence.

## Composition
- With audit: cybersecurity owns technical interpretation, technical authority, and security risk; audit owns scope, criterion, evidence structure, and findings.
- With law: cybersecurity owns technical facts/controls; law owns legal authority and legal consequence.

Resolve conflicts by superior authority, safety/compliance, and valid hardening rules. If material trade-offs remain unresolved, elevate the minimum human Gate.

## Missing or conflicting evidence
If required telemetry, configuration, or authority is missing, declare the gap and limit the conclusion. If authoritative sources conflict, apply declared precedence; otherwise surface divergence. Never fabricate state, version, vulnerability, authorization, or incident facts.

## Continuity and postcondition
For material work, preserve system/object, environment, active modules, evidence/SoR, authorization state, Gates, rollback state, and next safe action. Verify material writes or remediation against the correct live object before claiming completion.
