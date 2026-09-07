# Security Requirements Register

## Metadata

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **Project Name** | The OAuth 2.0 Authorization Framework (RFC 6749) |
| **Created At** | 2026-05-31 |
| **Created By** | Claude Opus 4.6 |
| **Created With** | Security Requirements Analysis 2.1 |

## Requirement Details

### SR-1: Resource Owner Identity Verification for the Authorization Endpoint

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **ID** | SR-1 |
| **Name** | Resource Owner Identity Verification for the Authorization Endpoint |
| **Normativity** | Normative |
| **Requirement Level** | MUST |
| **Summary** | The authorization server MUST verify the identity of the resource owner before issuing an authorization grant. |
| **Applicability** | Applies to every request to the authorization endpoint. |
| **Rationale** | An authorization grant represents a resource owner's delegation of access; without verifying that identity, the server cannot determine whose resources are delegated. |
| **Security Properties** | Authentication |
| **Threat** | The authorization endpoint allows an attacker to obtain an authorization grant due to missing resource owner identity verification, resulting in unauthorized delegation of protected resources. |
| **Mitigations** | Require a verified resource owner session before rendering the consent screen.<br>Bind the issued authorization grant to the verified resource owner's identity. |
| **Verification Method** | Test |
| **Verification Criteria** | The authorization server must not issue an authorization grant except for the resource owner whose identity it verified for that authorization request. |
| **CAPEC** | CAPEC-115 / CAPEC-151 |
| **CWE** | CWE-306 |
| **OWASP** | A01:2021 - Broken Access Control / A07:2021 - Identification and Authentication Failures |
| **Confidence** | Highest |
| **Gaps** | The mechanism, strength, and freshness of resource owner authentication are explicitly out of scope. |
| **References** | https://www.rfc-editor.org/rfc/rfc6749#section-3.1 |

#### Evidence

```text
URL: https://www.rfc-editor.org/rfc/rfc6749#section-3.1
The authorization endpoint is used to interact with the resource
owner and obtain an authorization grant.  The authorization server
MUST first verify the identity of the resource owner.  The way in
which the authorization server authenticates the resource owner
(e.g., username and password login, session cookies) is beyond the
scope of this specification.
```

### SR-2: Redirection URI Consistency Validation for the Authorization Code Grant

| <!-- Key --> | <!-- Value --> |
| --- | --- |
| **ID** | SR-2 |
| **Name** | Redirection URI Consistency Validation for the Authorization Code Grant |
| **Normativity** | Normative |
| **Requirement Level** | MUST |
| **Summary** | The authorization server MUST ensure that the token request presents a redirection URI identical to the one included in the initial authorization request. |
| **Applicability** | Applies to every authorization code grant token request where the initial authorization request included a `redirect_uri` parameter. |
| **Rationale** | The redirection URI determines where an authorization code is delivered; without comparing it at the token endpoint, an authorization code delivered to one destination can be redeemed from another. |
| **Security Properties** | Integrity / Authentication |
| **Threat** | The token endpoint allows an attacker to redeem a victim's authorization code due to missing redirection URI consistency validation, resulting in unauthorized access to the victim's protected resources. |
| **Mitigations** | Persist the redirection URI presented in the authorization request alongside the issued authorization code.<br>Compare the two redirection URIs with simple string comparison and reject the token request if the URIs do not match.<br>Invalidate the authorization code when the comparison fails. |
| **Verification Method** | Test |
| **Verification Criteria** | A token request presenting a `redirect_uri` parameter different from the one included in the initial authorization request must be rejected with `invalid_grant`.<br>A token request omitting a `redirect_uri` parameter when it was present in the initial authorization request must be rejected with `invalid_grant`. |
| **CAPEC** | CAPEC-21 |
| **CWE** | CWE-346 |
| **OWASP** | A01:2021 - Broken Access Control |
| **Confidence** | Highest |
| **Gaps** | The specification provides no proof-of-possession binding between the authorization request and the token request (added later by PKCE, RFC 7636), so an attacker who intercepts an authorization code delivered to the legitimate redirection URI can redeem it against a public client. |
| **References** | https://www.rfc-editor.org/rfc/rfc6749#section-4.1.3<br>https://www.rfc-editor.org/rfc/rfc6749#section-10.6 |

#### Evidence

```text
URL: https://www.rfc-editor.org/rfc/rfc6749#section-4.1.3
The authorization server MUST:
[...]
-  ensure that the "redirect_uri" parameter is present if the
   "redirect_uri" parameter was included in the initial authorization
   request as described in Section 4.1.1, and if included ensure that
   their values are identical.
```

```text
URL: https://www.rfc-editor.org/rfc/rfc6749#section-10.6
In order to prevent such an attack, the authorization server MUST
ensure that the redirection URI used to obtain the authorization code
is identical to the redirection URI provided when exchanging the
authorization code for an access token.  [...]
```

## Requirement Summary

| ID | Normativity | Requirement Level | Confidence | Name |
| --- | --- | --- | --- | --- |
| SR-1 | Normative | MUST | Highest | Resource Owner Identity Verification for the Authorization Endpoint |
| SR-2 | Normative | MUST | Highest | Redirection URI Consistency Validation for the Authorization Code Grant |
