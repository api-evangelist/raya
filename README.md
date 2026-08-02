# Raya

Raya (legal entity **Raya App Inc**) is a private, membership-based global community for dating,
friendship, and professional networking. Founded by Daniel Gendelman in 2014 and launched in
February 2015 out of Los Angeles, California. Membership is application-only — applications are
reviewed on an ongoing basis by a global committee, an Instagram handle is required for identity
verification, and accepted members choose a 1, 6, or 12 month paid subscription. The product is
iOS-only.

- Website: https://www.rayatheapp.com/
- App Store: https://apps.apple.com/us/app/raya/id957215308
- Secondary market listing: https://forgeglobal.com/raya_stock/

## API surface

**None public.** As of 2026-08-02, enrichment probed `rayatheapp.com`, `www.rayatheapp.com`,
`raya.co`, `api.rayatheapp.com`, `api.raya.co` and `icecream.rayatheapp.com` and found:

- no developer portal, API documentation, or API reference
- no OpenAPI / Swagger / GraphQL / AsyncAPI contract
- no MCP server and no A2A agent card
- no first-party SDK on npm, PyPI, or the public GitHub org
- no `/.well-known/` document of any kind

`api.rayatheapp.com` and `icecream.rayatheapp.com` are private first-party mobile backends that
return `{"statusCode":404,"error":"Not Found","message":"Not Found"}` for every unauthenticated
path. The public web hosts run a client-rendered React SPA that answers **HTTP 200 with the same
HTML shell for every path** — so any 200 from those hosts for `/openapi.json`, `/llms.txt`, or
`/.well-known/*` is a catch-all false positive, not a document. See
[`well-known/raya-well-known.yml`](well-known/raya-well-known.yml) for the recorded probe.

The public GitHub org [RayaTheApp](https://github.com/RayaTheApp) contains only forks of third-party
open source (iOS/Swift libraries, GitHub Actions, infrastructure tooling) — no first-party SDKs or
specifications.

This repository is therefore an **identity-only** profile pending a public API surface.

## Artifacts

| Path | Type | Method |
|---|---|---|
| `apis.yml` | APIs.json 0.20 profile | searched |
| `security/raya-domain-security.yml` | DomainSecurity | probed |
| `well-known/raya-well-known.yml` | well-known probe record (no documents found) | probed |
| `llms/raya-llms.txt` | LLMsTxt | generated |
