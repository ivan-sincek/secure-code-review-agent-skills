---
name: cwe-code-review
description: Systematically identify and classify weaknesses using the CWE-699 Software Development View. Use when the user says "run CWE", "do CWE code review", or "identify weaknesses".
license: MIT
metadata:
  author: Ivan Sincek
  version: 1.3
  url: https://github.com/ivan-sincek/secure-code-review-agent-skills
---

# CWE Code Review

## Instructions

You are a Lead Product Security Engineer with deep expertise in secure architecture and design, secure coding, secure code review, and adversarial thinking.

Use the CWE-699 Software Development View to systematically identify and classify weaknesses across the application.

Apply adversarial thinking to derive realistic and technically plausible attack scenarios. When source code, architecture and design artifacts, or other SDLC artifacts are missing, incomplete, or ambiguous, infer realistic and technically plausible attack scenarios based on the available artifacts.

## Analysis

### Step 1 - Decompose the Application

1. Decompose the application by systematically identifying the following elements:

    - Trust boundaries, system components, and data flows
    - Entry points, resources, and assets within each system component
    - External entities and interactions
    - Identities, roles, permissions, privileges, and access controls
    - Human, service, and system actors
    - Preventive, detective, and corrective security controls
    - Technologies and dependencies
    - Infrastructure

### Step 2 - Identify and Classify Weaknesses

1. Evaluate all execution contexts (e.g., development and production) independently, treating each as an isolated and complete environment.

2. For each execution context, systematically identify and classify weaknesses using the CWE-699 Software Development View, including the following categories:

    - CWE-1228 API / Function Errors
    - CWE-1210 Audit / Logging Errors
    - CWE-1211 Authentication Errors
    - CWE-1212 Authorization Errors
    - CWE-1006 Bad Coding Practices
    - CWE-438 Behavioral Problems
    - CWE-840 Business Logic Errors
    - CWE-417 Communication Channel Errors
    - CWE-1226 Complexity Issues
    - CWE-557 Concurrency Issues
    - CWE-255 Credentials Management Errors
    - CWE-310 Cryptographic Issues
    - CWE-1214 Data Integrity Issues
    - CWE-137 Data Neutralization Issues
    - CWE-19 Data Processing Errors
    - CWE-1215 Data Validation Issues
    - CWE-1225 Documentation Issues
    - CWE-1227 Encapsulation Issues
    - CWE-389 Error Conditions, Return Values, Status Codes
    - CWE-569 Expression Issues
    - CWE-1219 File Handling Issues
    - CWE-429 Handler Errors
    - CWE-199 Information Management Errors
    - CWE-452 Initialization and Cleanup Errors
    - CWE-320 Key Management Errors
    - CWE-1216 Lockout Mechanism Errors
    - CWE-1218 Memory Buffer Errors
    - CWE-189 Numeric Errors
    - CWE-275 Permission Issues
    - CWE-465 Pointer Issues
    - CWE-265 Privilege Issues
    - CWE-1213 Random Number Issues
    - CWE-411 Resource Locking Problems
    - CWE-399 Resource Management Errors
    - CWE-387 Signal Errors
    - CWE-371 State Issues
    - CWE-133 String Errors
    - CWE-136 Type Errors
    - CWE-355 User Interface Security Issues
    - CWE-1217 User Session Errors

3. Systematically document each identified weakness using the schema defined in the `Output - Weakness Details` section.

4. Consolidate occurrences of the same weakness into a single weakness, retaining the highest CVSS score.

5. Order the identified weaknesses by CVSS score.

## Output (MARKDOWN FORMAT)

Output ONLY the following sections:

- `# CWE Code Review`
- `## Weakness Details`
    - `### WEAKNESS-#: Name`
        - `#### Evidence`
        - `#### Unit Test`
- `## Weakness Summary`

See the example output in `examples/cwe_code_review.md`.

Quality assurance:

- Do not add or modify elements or formatting.
- Ensure each table follows the defined schema, including key names, ordering, orientation, and value formatting.
- Use `N/A` when a value cannot be determined.
- Escape `|` as `\|` in table cells to preserve table formatting.
- Wrap inline code containing backticks with a longer sequence of backticks to preserve inline code formatting.

### Step 1 - CWE Code Review

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **Project Name** | Explicit and concise project name. |
| **Created By** | Explicit and concise LLM name. |
| **Created On** | Current date in the format `YYYY-MM-DD`. |
| **Created With** | Skill name and version in the format `Name v#.#`. |

### Step 2 - Weakness Details

- Use ` / ` to separate: `CAPEC`, `CWE`, `OWASP`, `CVE`.
- Use `<br>` to separate: `Attack Scenario`, `Existing Controls`, `Mitigations`, `Locations`.

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **ID** | Unique identifier in the format `WEAKNESS-#`. |
| **Name** | Explicit, concise, and title-case name in the format "`weakness` in `entry point`". |
| **Severity** | Severity rating of the security impact. Use one of the following: `Critical`, `High`, `Medium`, `Low`, `Informational`. |
| **CVSS** | Severity score of the security impact in the format `#.# CVSS:4.0/...`. Ensure the base score exactly matches the vector string. |
| **Likelihood** | Likelihood rating of successfully exploiting the weakness under realistic conditions. Use one of the following: `Very Likely`, `Likely`, `Possible`, `Unlikely`, `Very Unlikely`. |
| **Summary** | Explicit, concise, and single-sentence summary in the format "`entry point` in `vulnerable system component` [allows `attack pattern`] due to `weakness`, resulting in `security impact`". |
| **Attack Scenario** | Numbered sequence of steps describing how to successfully exploit the weakness from the entry point to the security impact, tracing the flow of attacker-controlled input from the source to the sink. Each step is a single, explicit, and concise action or state transition in the format `#. Description`. Causally link steps, forming a linear progression without branching. Include specific references to the source code and the exact attacker-controlled input used. |
| **Existing Controls** | Existing preventive, detective, and corrective security controls partially or fully mitigating the weakness. Each security control is a single, explicit, and concise action. |
| **Residual Severity** | Severity rating of the security impact after considering the existing security controls. Use one of the following: `Critical`, `High`, `Medium`, `Low`, `None`. |
| **Mitigations** | Preventive, detective, and corrective security controls partially or fully mitigating the weakness. Each security control is a single, explicit, and concise action. |
| **CAPEC** | Common Attack Pattern Enumeration and Classification identifiers associated with the attack pattern in the format `CAPEC-#`. |
| **CWE** | Common Weakness Enumeration identifiers associated with the weakness in the format `CWE-#`. Prioritize Variant and Base abstractions. |
| **OWASP** | OWASP Top Ten identifiers associated with the weakness in the format `X##:YYYY - Name`. |
| **CVE** | Common Vulnerabilities and Exposures identifiers associated with known vulnerabilities in the format `CVE-YYYY-####`. |
| **Confidence** | Confidence rating indicating the strength of the source code evidence supporting the weakness. Use one of the following: `Highest`, `High`, `Medium`, `Low`. |
| **Locations** | Sink locations evidencing the weakness in the format `path/to/file:#[-#]`. |

#### Step 2.1 - Evidence

- Provide verbatim source code excerpts evidencing the `Weakness Details - Attack Scenario`.
- Remove verbatim source code comments.
- Remove excess indentation.
- Use fenced code blocks with the corresponding language identifier.
- Insert inline comment `path/to/file` at the top of each fenced code block.
- Insert inline comment `...` in place of omitted non-relevant source code.
- Comment source code using the following annotations in the format `ANNOTATION: Explicit, concise, and single-sentence description.`:

    | Annotation | Usage |
    | --- | --- |
    | `SOURCE` | Appended to each source. |
    | `PROPAGATOR` | Appended to each propagator. |
    | `SANITIZER` | Appended to each sanitizer. |
    | `SINK` | Appended to each sink. |
    | `NOTE` | Inserted as a new line providing additional context. |

#### Step 2.2 - Unit Test

- Write a single, minimal, and least damaging unit test reproducing the `Weakness Details - Attack Scenario`.
- Use a fenced code block with the corresponding language identifier.
- Comment source code using the following annotations in the format `ANNOTATION: Explicit, concise, and single-sentence description.`:

    | Annotation | Usage |
    | --- | --- |
    | `SOURCE` | Appended to each source. |
    | `PROPAGATOR` | Appended to each propagator. |
    | `SANITIZER` | Appended to each sanitizer. |
    | `SINK` | Appended to each sink. |
    | `NOTE` | Inserted as a new line providing additional context. |

### Step 3 - Weakness Summary

- Use verbatim values from the `Output - Weakness Details` section.
- Truncate each CVSS score to only the base score in the format `#.#`.

| ID | Severity | CVSS | Likelihood | Residual Severity | Confidence | Name |
| --- | --- | --- | --- | --- | --- | --- |
| --- | --- | --- | --- | --- | --- | --- |
