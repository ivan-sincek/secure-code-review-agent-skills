---
name: cwe-code-review
description: Systematically identify and classify weaknesses using the CWE-699 Software Development View. Use when the user says "run CWE", "do CWE code review", or "identify weaknesses".
license: MIT
metadata:
  author: Ivan Sincek
  version: 1.1
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
    - CWE-320 Key Management Errors
    - CWE-1214 Data Integrity Issues
    - CWE-19 Data Processing Errors
    - CWE-137 Data Neutralization Issues
    - CWE-1225 Documentation Issues
    - CWE-1219 File Handling Issues
    - CWE-1227 Encapsulation Issues
    - CWE-389 Error Conditions, Return Values, Status Codes
    - CWE-569 Expression Issues
    - CWE-429 Handler Errors
    - CWE-199 Information Management Errors
    - CWE-452 Initialization and Cleanup Errors
    - CWE-1215 Data Validation Issues
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

## Output (JSON FORMAT)

Output ONLY the following sections:

```json
{
  "cwe_code_review": {},
  "weakness_details": [],
  "weakness_summary": []
}
```

See the example output in `examples/cwe_code_review.json`.

Quality assurance:

- Do not add or modify elements or formatting.
- Ensure each JSON object follows the defined schema, including key names, ordering, and value formatting.
- Use `N/A` when a value cannot be determined.
- Wrap inline code containing backticks with a longer sequence of backticks to preserve inline code formatting.

### Step 1 - CWE Code Review

```json
{
  "project_name": "Explicit and concise project name.",
  "created_by": "Explicit and concise LLM name.",
  "created_on": "Current date in the format `YYYY-MM-DD`.",
  "created_with": "Skill name and version in the format `Name v#.#`."
}
```

### Step 2 - Weakness Details

```json
{
  "id": "Unique identifier in the format `WEAKNESS-#`.",
  "name": "Explicit, concise, and title-case name in the format \"`weakness` in `entry point`\".",
  "severity": "Severity rating of the security impact. Use one of the following: `Critical`, `High`, `Medium`, `Low`, `Informational`.",
  "cvss": "Severity score of the security impact in the format `#.# CVSS:4.0/...`. Ensure the base score exactly matches the vector string.",
  "likelihood": "Likelihood rating of successfully exploiting the weakness under realistic conditions. Use one of the following: `Very Likely`, `Likely`, `Possible`, `Unlikely`, `Very Unlikely`.",
  "summary": "Explicit, concise, and single-sentence summary in the format \"`entry point` in `vulnerable system component` [allows `attack pattern`] due to `weakness`, resulting in `security impact`\".",
  "attack_scenario": ["Numbered sequence of steps describing how to successfully exploit the weakness from the entry point to the security impact, tracing the flow of attacker-controlled input from the source to the sink. Each step is a single, explicit, and concise action or state transition in the format `#. Description`. Causally link steps, forming a linear progression without branching. Include specific references to the source code and the exact attacker-controlled input used."],
  "existing_controls": ["Existing preventive, detective, and corrective security controls partially or fully mitigating the weakness. Each security control is a single, explicit, and concise action."],
  "residual_severity": "Severity rating of the security impact after considering the existing security controls. Use one of the following: `Critical`, `High`, `Medium`, `Low`, `None`.",
  "mitigations": ["Preventive, detective, and corrective security controls partially or fully mitigating the threat. Each security control is a single, explicit, and concise action."],
  "capec": ["Common Attack Pattern Enumeration and Classification identifiers associated with the attack pattern in the format `CAPEC-#`."],
  "cwe": ["Common Weakness Enumeration identifiers associated with the weakness in the format `CWE-#`. Prioritize Variant and Base abstractions."],
  "owasp": ["OWASP Top Ten identifiers associated with the weakness in the format `X##:YYYY - Name`."],
  "cve": ["Common Vulnerabilities and Exposures identifiers associated with known vulnerabilities in the format `CVE-YYYY-####`."],
  "confidence": "Confidence rating indicating the strength of the source code evidence supporting the weakness. Use one of the following: `Highest`, `High`, `Medium`, `Low`.",
  "locations": ["All source code locations where the weakness occurs in the format `path/to/file:#[-#]`."],
  "evidence": "A single minimal verbatim source code excerpt demonstrating the weakness enclosed in a fenced code block with the correct language identifier. For each vulnerable line, append the inline comment `VULNERABLE`."
}
```

### Step 3 - Weakness Summary

- Use verbatim values from the `Output - Weakness Details` section.
- Truncate each CVSS score to only the base score in the format `#.#`.

```json
{
  "id": "",
  "severity": "",
  "cvss": "",
  "likelihood": "",
  "residual_severity": "",
  "confidence": "",
  "name": ""
}
```
