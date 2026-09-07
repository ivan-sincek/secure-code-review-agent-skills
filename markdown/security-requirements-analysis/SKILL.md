---
name: security-requirements-analysis
description: Systematically extract and classify security requirements from a specification document. Use when the user says "do a security requirements analysis" or "extract security requirements".
license: MIT
metadata:
  author: Ivan Sincek
  version: "2.1"
  url: https://github.com/ivan-sincek/secure-code-review-agent-skills
---

# Security Requirements Analysis

## Instructions

You are a Lead Security Compliance Engineer with deep expertise in specification analysis, standards conformance, security requirements engineering, and secure architecture and design.

Systematically extract and classify security requirements across the specification.

## Analysis

### Step 1 - Extract and Classify Security Requirements

1. Systematically extract and document each security requirement using the schema defined in the `Output > Requirement Details` section.

2. Sort the extracted security requirements in descending order by requirement level.

## Output (MARKDOWN FORMAT)

Output ONLY the following sections:

- `# Security Requirements Register`
- `## Metadata`
- `## Requirement Details`
    - `### SR-#: Name`
        - `#### Evidence`
- `## Requirement Summary`

See the example output in `examples/security_requirements_register.md`.

Quality assurance:

- Do not add or modify Markdown elements.
- Ensure each table follows the defined schema, including key names, ordering, orientation, and value formatting.
- Use `N/A` when a value cannot be determined.
- Escape `|` as `\|` in table cells to preserve table formatting.
- Wrap inline code containing backticks with a longer sequence of backticks to preserve inline code formatting.

### Metadata

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **Project Name** | Explicit and concise name of the project. |
| **Created At** | Current date in the format `YYYY-MM-DD`. |
| **Created By** | Explicit and concise name and version of the model. |
| **Created With** | Use verbatim: `Security Requirements Analysis 2.1`. |

### Requirement Details

- Use ` / ` to separate: `Security Properties`, `CAPEC`, `CWE`, `OWASP`.
- Use `<br>` to separate: `Mitigations`, `Gaps`, `References`.

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **ID** | Unique identifier in the format `SR-#`. |
| **Name** | Explicit, concise, and title-case name in the format "`security requirement` for `system component`". |
| **Normativity** | Type of the statement. Use one of the following: `Normative`, `Informative`. |
| **Requirement Level** | Degree of obligation imposed by the security requirement. Use one of the following: `MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT`, `MAY`. |
| **Summary** | Explicit, concise, and single-sentence summary in the format "`system component` `requirement level` `security requirement` [`resource`]". |
| **Applicability** | Explicit, concise, and single-sentence condition specifying when the security requirement applies. |
| **Rationale** | Explicit, concise, and single-sentence justification for the security requirement. |
| **Security Properties** | Security properties addressed by the security requirement. Use one or more of the following in this exact order: `Confidentiality`, `Integrity`, `Availability`, `Authentication`, `Non-Repudiation`, `Authorization`, `Other`. |
| **Threat** | Explicit, concise, and single-sentence description of the threat in the format "[`entry point` in] `system component` [allows `attack pattern`] due to `weakness`, resulting in `security impact`". |
| **Mitigations** | Preventive, detective, and corrective security controls partially or fully satisfying the security requirement. Each security control is a single, explicit, and concise action. |
| **Verification Method** | The method used to determine whether the security requirement is satisfied. Use one of the following: `Inspection`, `Analysis`, `Demonstration`, `Test`. |
| **Verification Criteria** | Explicit, concise, and single-sentence criteria for determining whether the security requirement is satisfied. |
| **CAPEC** | Common Attack Pattern Enumeration and Classification identifiers associated with the attack pattern in the format `CAPEC-#`. |
| **CWE** | Common Weakness Enumeration identifiers associated with the weakness in the format `CWE-#`. Prioritize Variant and Base abstractions. |
| **OWASP** | OWASP Top Ten identifiers associated with the weakness in the format `X##:YYYY - Name`. |
| **Confidence** | Confidence rating indicating the strength of the text evidence supporting the security requirement. Use one of the following: `Highest`, `High`, `Medium`, `Low`. |
| **Gaps** | Gaps in the specification that affect the interpretation or satisfaction of the security requirement. Each gap is a single, explicit, and concise observation. |
| **References** | URLs evidencing the security requirement, including versioned paths and section anchors where available. |

#### Evidence

- Provide verbatim text excerpts evidencing the security requirement.
- Remove excess indentation.
- Use fenced code blocks with the `text` language identifier.
- Insert text `URL: https://...` at the top of each fenced code block.
- Insert text `[...]` in place of omitted irrelevant text.

### Requirement Summary

- Use verbatim values from the `Output > Requirement Details` section.

| ID | Normativity | Requirement Level | Confidence | Name |
| --- | --- | --- | --- | --- |
| --- | --- | --- | --- | --- |
