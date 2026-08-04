# Underdog Fantasy

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
