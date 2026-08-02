# Secure Code Review Agent Skills

Easy-to-use, easy-to-customize, and high-quality secure code review skills for AI agents.

Supporting Markdown and JSON output formats.

My other skills:

- [Threat Modeling Agent Skills](https://github.com/ivan-sincek/threat-modeling-agent-skills)

## Table of Contents

* [Secure Code Review](#secure-code-review)
  * [CWE](#cwe)
* [How to Use](#how-to-use)

## Secure Code Review

### CWE

* Used to identify weaknesses based on Common Weakness Enumeration (CWE).
* Applies structured, single-step kill chain reasoning without considering business context, objectives, or impact.
* Scoped to the application.
* Works well with both lower-end and higher-end LLMs.

**Skill:** [cwe-code-review/SKILL.md](https://github.com/ivan-sincek/secure-code-review-agent-skills/blob/main/markdown/cwe-code-review/SKILL.md)

## How to Use

* Copy the contents of the [markdown](https://github.com/ivan-sincek/secure-code-review-agent-skills/tree/main/markdown) directory into your project's `.claude/skills/` directory.
* Alternatively, manually upload each `SKILL.md` file to your Claude app under `Customize -> Skills`.

Basic prompt:

```text
Perform CWE code review and save the output to "cwe_code_review.md".
```

Advanced prompt:

```text
- Perform CWE code review and save the output to "cwe_code_review.md".
- Convert "cwe_code_review.md" to "cwe_code_review.html".
- Ensure the `body` CSS rule includes `width: 100%; max-width: 100%;`.
- Ensure the `td` CSS rule includes `word-break: keep-all;`.
- Add a table of contents.
- Make the non-key-value tables sortable.
```
