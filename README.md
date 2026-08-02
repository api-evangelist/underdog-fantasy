# Underdog Fantasy

Underdog (Underdog Sports, formerly Underdog Fantasy) is a Brooklyn, New York based sports gaming
company founded in 2020 by Jeremy Levine. It operates daily fantasy sports, pick'em contests, and —
since 2025 — federally regulated sports prediction markets on its own proprietary technology stack.

- https://www.underdogsports.com/
- https://forgeglobal.com/underdog-fantasy_stock/

## API status

**Underdog publishes no public API.** There is no developer portal, no API documentation, no
OpenAPI/Swagger document, no GraphQL endpoint, no MCP server, and no A2A agent card. Contract
discovery on 2026-08-02 probed `underdogfantasy.com`, `underdogsports.com`,
`api.underdogfantasy.com`, `stats.underdogfantasy.com`, `app.underdogsports.com`,
`underdogpredict.com`, `legal.underdogsports.com` and `help.underdogsports.com` for
`/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`, `/docs`,
`/redoc`, `/graphql`, `/llms.txt`, `/.well-known/agent-card.json` and `/.well-known/agent.json`.
Every probe returned 404 or 403.

`api.underdogfantasy.com` is the non-public backend for the mobile and web applications; it returns
404 at the root and for every spec path. `legal.underdogsports.com` answers HTTP 200 with the same
Webflow single-page-app HTML for *every* path and was rejected as a false positive.

Third-party "Underdog odds API" products are scrapers or aggregators run by other companies.
`docs.underdogprotocol.com` and `underdog.readme.io` belong to Underdog Protocol, an unrelated
Solana NFT infrastructure company.

## What the company does publish

| Surface | Location |
|---|---|
| security.txt (RFC 9116) | https://underdogfantasy.com/.well-known/security.txt |
| PGP public key | https://underdogfantasy.com/.well-known/udsecurity.asc |
| Status page (Honeybadger) | https://status.underdogfantasy.com/ — components: API, Stats |
| Legal center | https://legal.underdogsports.com/ |
| Help center | https://help.underdogsports.com/en/ |
| GitHub organization | https://github.com/Underdog-Inc |

## Artifacts in this repo

- `well-known/` — verbatim security.txt + PGP key, plus the full `/.well-known/` probe index
- `security/` — domain security posture (TLS/HSTS/DNSSEC/CAA/SPF/DMARC) and the vulnerability
  disclosure profile derived from security.txt
- `lifecycle/` — status page and legal-document versioning
- `packages/` — package-registry and GitHub organization survey (no API client SDK exists)
- `llms/` — generated `llms.txt`

## Known provider issues worth reporting

The security.txt served from `underdogfantasy.com` declares
`Canonical: https://underdogsports.com/.well-known/security.txt` and
`Encryption: https://underdogsports.com/.well-known/udsecurity.asc`, but **both of those URLs return
HTTP 404**. Under RFC 9116 a Canonical URI that does not serve the file is a conformance defect.
