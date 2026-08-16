# API Security & Auth Protocol Reference

Two interactive, single-file HTML reference guides covering HTTP API security and authentication/authorization protocols, with dedicated guidance for LLM endpoints, agents, and MCP servers.

**Live demos:** [API Security in the AI Era](https://tgandhle.github.io/API-Security-Auth-Protocol-Reference/api-security-ai-era.html) · [Auth Protocols Guide](https://tgandhle.github.io/API-Security-Auth-Protocol-Reference/auth-protocols-guide.html)

## What's here

| File | What it covers |
|------|----------------|
| `auth-protocols-guide.html` | AuthN vs AuthZ across OAuth 2.0 + PKCE, OpenID Connect, SAML 2.0, Client Credentials, mTLS, DPoP, FAPI 2.0, MCP authorization, and the no-longer-recommended Implicit flow. Each card states its scope and standards basis. |
| `api-security-ai-era.html` | Explicit coverage of all ten OWASP API Security Top 10 risks, token lifecycle and key management, API boundaries, gateway controls, webhooks, CORS, AI and agent risks, and versioning. Includes an interactive security review checklist. |
| `standards-and-sources.md` | Versioned primary sources, coverage matrices, scope, and the rules used to distinguish standards requirements from project recommendations. |

Both files are static single-page HTML references. No build step, framework, or runtime application dependency is required. The pages load Google Fonts from Google's CDN, with system-font fallbacks if that fails; remove the `<link>` in each file's `<head>` if you need strict offline behavior.

## Why I built it

Most auth and API security references are either dense RFC prose or vendor marketing. I wanted a reference that is opinionated, gives a clear verdict on when to use each protocol, and treats AI-specific concerns (prompt injection via API, inference cost attacks, token exfiltration through LLM responses, sensitive data in model context) as first-class rather than an afterthought.

The content maps to versioned primary sources, including the OAuth and JWT RFCs, the OWASP API Security Top 10 (2023), the OWASP Top 10 for LLM Applications (2025), the OWASP Top 10 for Agentic Applications (2026), FAPI 2.0, and the MCP authorization specification (2025-11-25). Requirements are attributed to their source; project recommendations are labelled as recommendations.

## Scope

This is a comprehensive baseline for HTTP and JSON APIs that use OAuth, JWTs, service credentials, webhooks, LLMs, agents, or MCP. It does not claim complete treatment of GraphQL, gRPC, WebSocket, mobile platform, browser application, or cloud-provider configuration security. Those systems still need protocol-specific review.

See [`standards-and-sources.md`](standards-and-sources.md) for the coverage definition and source versions. Each control should answer five questions: what can fail, where enforcement belongs, what is required, how to test it, and which primary source supports it.

## What this demonstrates

- Working knowledge of modern auth protocols and their correct use cases, including the AuthN/AuthZ distinction that's commonly conflated
- Understanding of real API attack surface: JWT algorithm confusion, CORS origin reflection, webhook replay, token theft
- Applied AI security thinking, not just generic API hardening with an AI label
- Ability to turn dense technical material into a clear, well-designed, usable reference

## Running it

No setup required.

```
# Clone, then open either file directly
open auth-protocols-guide.html
# or serve locally
python3 -m http.server 8000
```

## Notes

This is reference material for design reviews and learning, not a substitute for a system-specific threat model. Standards and platform capabilities change. The source register records the version and review date used by these guides. Product selection should be based on deployment-specific acceptance tests, not a generic feature table.

## License

MIT. Use it, fork it, learn from it.
