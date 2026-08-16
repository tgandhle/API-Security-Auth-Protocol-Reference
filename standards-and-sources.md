# Standards, sources, and coverage

Last reviewed: 2026-08-16

This file defines what "comprehensive" means for this repository. The guides cover the listed baselines for HTTP and JSON APIs. A statement is normative only when it is tied to a cited specification using that specification's requirement language. Otherwise it is labelled **Project recommendation**.

## Scope

Included:

- HTTP API authentication, authorization, token handling, and gateway boundaries
- OAuth, OpenID Connect, JWT, mTLS, DPoP, FAPI, and MCP authorization
- All OWASP API Security Top 10 risks from the 2023 edition
- LLM and agent controls relevant at an API or tool boundary
- Operational verification signals and negative tests

Not covered in depth:

- GraphQL query planning, batching, field authorization, and introspection
- gRPC reflection, protobuf-specific validation, and streaming controls
- WebSocket session reauthorization and message-level controls
- Mobile platform credential storage and device attestation
- Cloud-provider-specific policy syntax and product configuration
- Compliance determinations for a particular organization or jurisdiction

## Primary standards

| Area | Source | Status used here | Review note |
|---|---|---|---|
| OAuth 2.0 | [RFC 6749](https://www.rfc-editor.org/rfc/rfc6749.html) | RFC | Base authorization framework. Read with RFC 9700. |
| OAuth security | [RFC 9700](https://www.rfc-editor.org/rfc/rfc9700.html) | Best Current Practice | Current security baseline for OAuth 2.0 deployments. |
| OAuth 2.1 | [draft-ietf-oauth-v2-1-15](https://datatracker.ietf.org/doc/draft-ietf-oauth-v2-1/) | Active Internet-Draft, 2026-03-02 | Work in progress, not an RFC. Do not present draft text as a stable RFC requirement. |
| OAuth bearer tokens | [RFC 6750](https://www.rfc-editor.org/rfc/rfc6750.html) | RFC | Bearer-token transport and threat considerations. |
| PKCE | [RFC 7636](https://www.rfc-editor.org/rfc/rfc7636.html) | RFC | Authorization-code interception protection. |
| OpenID Connect | [OpenID Connect Core 1.0 incorporating errata set 2](https://openid.net/specs/openid-connect-core-1_0.html) | OpenID Final Specification with errata | Standardized end-user authentication and ID Token validation. |
| SAML 2.0 | [OASIS SAML 2.0 Technical Overview](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.pdf) and [conformance requirements](https://docs.oasis-open.org/security/saml/v2.0/saml-conformance-2.0-os.pdf) | OASIS overview and standard | Browser SSO, assertions, profiles, and conformance. |
| JWT | [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519.html) | RFC | Generic JWT claims are application and profile dependent. |
| JWT security | [RFC 8725](https://www.rfc-editor.org/rfc/rfc8725.html) | Best Current Practice | Algorithm verification, explicit typing, and cross-JWT confusion. |
| JWT access tokens | [RFC 9068](https://www.rfc-editor.org/rfc/rfc9068.html) | RFC profile | Defines required claims for conforming OAuth JWT access tokens. |
| Revocation | [RFC 7009](https://www.rfc-editor.org/rfc/rfc7009.html) | RFC | Token revocation endpoint. |
| Introspection | [RFC 7662](https://www.rfc-editor.org/rfc/rfc7662.html) | RFC | Active-state lookup for tokens. |
| Token exchange | [RFC 8693](https://www.rfc-editor.org/rfc/rfc8693.html) | RFC | Delegation and impersonation token exchange. |
| Client authentication | [RFC 7523](https://www.rfc-editor.org/rfc/rfc7523.html), [RFC 8705](https://www.rfc-editor.org/rfc/rfc8705.html) | RFCs | `private_key_jwt`, mutual-TLS client authentication, and certificate-bound tokens. |
| Resource indicators | [RFC 8707](https://www.rfc-editor.org/rfc/rfc8707.html) | RFC | Binds an authorization request to a target resource. |
| DPoP | [RFC 9449](https://www.rfc-editor.org/rfc/rfc9449.html) | RFC | Application-layer proof of possession. |
| HTTP message signatures | [RFC 9421](https://www.rfc-editor.org/rfc/rfc9421.html) | RFC | Standard canonicalization and signature fields. The guide's HMAC snippet is illustrative and not an RFC 9421 wire example. |
| PAR | [RFC 9126](https://www.rfc-editor.org/rfc/rfc9126.html) | RFC | Pushed Authorization Requests. |
| Authorization server metadata | [RFC 8414](https://www.rfc-editor.org/rfc/rfc8414.html) | RFC | Authorization-server discovery metadata. |
| Protected resource metadata | [RFC 9728](https://www.rfc-editor.org/rfc/rfc9728.html) | RFC | Resource-server metadata and authorization-server locations. |
| FAPI 2.0 | [FAPI 2.0 Security Profile](https://openid.net/specs/fapi-security-profile-2_0-final.html) | OpenID Final Specification, 2025-02-22 | High-security OAuth 2.0 profile. |
| MCP authorization | [MCP 2025-11-25 authorization](https://modelcontextprotocol.io/specification/2025-11-25/basic/authorization) | Versioned MCP specification | Authorization is optional; the HTTP authorization flow has explicit discovery, PKCE, resource, audience, and token-handling requirements. |
| CORS | [WHATWG Fetch Standard, CORS protocol](https://fetch.spec.whatwg.org/#http-cors-protocol) | Living Standard | Browser cross-origin request and credential behavior. |
| API deprecation | [RFC 9745](https://www.rfc-editor.org/rfc/rfc9745.html) and [RFC 8594](https://www.rfc-editor.org/rfc/rfc8594.html) | RFCs | Deprecation metadata and planned sunset signaling. |

## Security baselines

| Baseline | Version | Coverage rule |
|---|---|---|
| [OWASP API Security Top 10](https://owasp.org/API-Security/editions/2023/en/0x00-header/) | 2023 | Every API1 through API10 risk has an explicit control section or cross-reference. |
| [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/) | 2025 | API-boundary controls are mapped explicitly. Model training and governance topics are marked out of scope where applicable. |
| [OWASP Top 10 for Agentic Applications](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) | 2026 | Tool, identity, privilege, supply-chain, memory, and inter-agent controls are mapped explicitly. |

## OWASP API Security Top 10 coverage

| Risk | Guide location | Coverage |
|---|---|---|
| API1 Broken Object Level Authorization | Authorization tab | Explicit |
| API2 Broken Authentication | Auth Mechanisms and JWT Security tabs | Explicit |
| API3 Broken Object Property Level Authorization | Authorization tab | Explicit |
| API4 Unrestricted Resource Consumption | Rate Limiting tab | Explicit |
| API5 Broken Function Level Authorization | Authorization tab | Explicit |
| API6 Unrestricted Access to Sensitive Business Flows | Authorization tab | Explicit |
| API7 Server Side Request Forgery | API Boundaries tab | Explicit |
| API8 Security Misconfiguration | Gateway Controls and CORS tabs | Explicit |
| API9 Improper Inventory Management | Versioning tab | Explicit |
| API10 Unsafe Consumption of APIs | API Boundaries tab | Explicit |

## OWASP Top 10 for LLM Applications coverage

This mapping covers controls that can be enforced or tested at an API, retrieval, model, or tool boundary. It does not claim to replace model-development governance.

| Risk | Guide location | Coverage |
|---|---|---|
| LLM01 Prompt Injection | AI-Specific Threats, Prompt Injection card | Explicit |
| LLM02 Sensitive Information Disclosure | AI-Specific Threats, Sensitive Data in Model Context card | Explicit |
| LLM03 Supply Chain | AI-Specific Threats, AI Supply Chain, Retrieval, and Memory card | Explicit |
| LLM04 Data and Model Poisoning | AI-Specific Threats, AI Supply Chain, Retrieval, and Memory card | API-boundary subset |
| LLM05 Improper Output Handling | AI-Specific Threats, Prompt Injection and Agent Authority cards; API Boundaries, Request and Response Contracts card | Explicit |
| LLM06 Excessive Agency | AI-Specific Threats, Agent Authority and Tool Use card | Explicit |
| LLM07 System Prompt Leakage | AI-Specific Threats, Prompt Injection card | Explicit |
| LLM08 Vector and Embedding Weaknesses | AI-Specific Threats, AI Supply Chain, Retrieval, and Memory card | Explicit |
| LLM09 Misinformation | AI-Specific Threats, Agent Authority and Tool Use card | High-impact action subset |
| LLM10 Unbounded Consumption | Rate Limiting tab and Model Endpoint Abuse card | Explicit |

## OWASP Top 10 for Agentic Applications coverage

| Risk | Guide location | Coverage |
|---|---|---|
| ASI01 Agent Goal Hijack | AI-Specific Threats, Prompt Injection and Agent Authority cards | Explicit |
| ASI02 Tool Misuse and Exploitation | AI-Specific Threats, Agent Authority and Tool Use card | Explicit |
| ASI03 Identity and Privilege Abuse | JWT Security, Delegation and Identity Chains card; AI-Specific Threats, Agent Authority card | Explicit |
| ASI04 Agentic Supply Chain Vulnerabilities | AI-Specific Threats, AI Supply Chain, Retrieval, and Memory card | Explicit |
| ASI05 Unexpected Code Execution | API Boundaries, Request and Response Contracts card; AI-Specific Threats, Agent Authority card | Explicit |
| ASI06 Memory and Context Poisoning | AI-Specific Threats, AI Supply Chain, Retrieval, and Memory card | Explicit |
| ASI07 Insecure Inter-Agent Communication | JWT Security, Delegation and Identity Chains card; Auth Protocols, MCP HTTP Authorization card | Explicit |
| ASI08 Cascading Failures | Authorization, Sensitive Business Flows card; AI-Specific Threats, Agent Authority card | Explicit |
| ASI09 Human-Agent Trust Exploitation | AI-Specific Threats, Agent Authority and Tool Use card | High-impact action subset |
| ASI10 Rogue Agents | AI-Specific Threats, Agent Authority and Tool Use card | Explicit |

## Maintenance rules

1. Keep dates and version identifiers on claims that can change.
2. Link requirements to primary standards, not vendor summaries.
3. Label opinionated defaults as project recommendations.
4. Do not use regulatory language such as "required for PHI" without a direct legal or regulatory source and jurisdiction.
5. Revalidate every vendor-comparison cell when its review date changes.
6. Remove or generate numeric coverage claims. Do not maintain unexplained hand-counted totals.
7. For every security control, include a negative test or detection signal that can falsify the claim.
