# Secure Code Review Agent Skills

Easy-to-use, customizable, high-quality secure code review skills for AI agents.

Cost-effective skills that deliver zero-shot, actionable results, with support for Markdown and JSON output formats.

My other skills:

- [Threat Modeling Agent Skills](https://github.com/ivan-sincek/threat-modeling-agent-skills)
- [Vulnerability Management Agent Skills](https://github.com/ivan-sincek/vulnerability-management-agent-skills)

## Table of Contents

* [CWE Secure Code Review](#cwe-secure-code-review)
* [Security Requirements Analysis](#security-requirements-analysis)
* [How to Use](#how-to-use)

## CWE Secure Code Review

* Used to identify weaknesses based on the Common Weakness Enumeration (CWE).
* Applies structured, single-step kill-chain reasoning without considering business context, objectives, or potential impact.
* Works well with both lower-end and higher-end LLMs.

**Skill:** [cwe-secure-code-review/SKILL.md](https://github.com/ivan-sincek/secure-code-review-agent-skills/blob/main/markdown/cwe-secure-code-review/SKILL.md)

**Example:** [cwe-secure-code-review/examples/cwe_secure_code_review_report.md](https://github.com/ivan-sincek/secure-code-review-agent-skills/blob/main/markdown/cwe-secure-code-review/examples/cwe_secure_code_review_report.md)

## Security Requirements Analysis

* Used to extract security requirements from a specification document.
* Works well with both lower-end and higher-end LLMs.
* Can be followed by [STRIDE threat modeling](https://github.com/ivan-sincek/threat-modeling-agent-skills#stride-threat-modeling-framework) to gain further insight into potential threats.

**Skill:** [security-requirements-analysis/SKILL.md](https://github.com/ivan-sincek/secure-code-review-agent-skills/blob/main/markdown/security-requirements-analysis/SKILL.md)

**Example:** [security-requirements-analysis/examples/security_requirements_register.md](https://github.com/ivan-sincek/secure-code-review-agent-skills/blob/main/markdown/security-requirements-analysis/examples/security_requirements_register.md)

## How to Use

* Copy the contents of the [markdown](https://github.com/ivan-sincek/secure-code-review-agent-skills/tree/main/markdown) directory into your project's `.claude/skills/` directory.
* Alternatively, manually upload each `SKILL.md` file to your Claude app under `Customize -> Skills`.

Basic prompt:

```text
Perform CWE secure code review and save the output to "cwe_secure_code_review_report.md".
```

Advanced prompt:

```text
- Perform CWE secure code review and save the output to "cwe_secure_code_review_report.md".
- Convert "cwe_secure_code_review_report.md" to "cwe_secure_code_review_report.html".
- Ensure the `body` CSS rule includes `width: 100%; max-width: 100%;`.
- Ensure the `td` CSS rule includes `word-break: keep-all;`.
- Add a table of contents.
- Make the non-key-value tables sortable.
```
