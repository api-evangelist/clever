# Clever (clever)

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

Clever is a K-12 EdTech identity platform that provides a unified single sign-on portal and roster synchronization service used by over 111,000 US schools, including 95 of the largest 100 districts. The Clever REST API enables application partners to securely access real-time student roster data, school and district information, class and section data, and user identity records through a single integration. Clever Complete offers Secure Sync for district-managed rostering, LMS Connect for gradebook syncing, and Single Sign-On via OAuth 2.0, OIDC, and SAML, eliminating the need for per-SIS integrations. Approximately 60 percent of US students log in monthly through Clever, making it the de facto identity layer for K-12 EdTech applications across the United States.

**APIs.json:** https://raw.githubusercontent.com/api-evangelist/clever/refs/heads/main/apis.yml

**Naftiko:** https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=clever-api-evangelist&utm_content=repo

## Tags

Education, K-12, EdTech, Single Sign-On, Rostering, Identity, SSO, Student Data, LMS, SIS

## APIs

| Name | Description | Docs |
|------|-------------|------|
| Clever Data API | RESTful API for district, school, student, teacher, section, and course data via Secure Sync (v3.1) | [Docs](https://dev.clever.com/docs/api-overview) |
| Clever Single Sign-On API | OAuth 2.0, OIDC, and SAML SSO integration for K-12 application partners | [Docs](https://dev.clever.com/docs/integration-types) |
| Clever LMS Connect API | Gradebook and LMS data sync integration available in API v3.1 | [Docs](https://dev.clever.com/docs/integration-types) |
| Clever Events API | Delta-sync event stream for incremental roster change notifications | [Docs](https://dev.clever.com/docs/api-overview) |

## Plans / Rate Limits / FinOps

| Resource | Path |
|----------|------|
| Plans & Pricing | [plans/clever-plans-pricing.yml](plans/clever-plans-pricing.yml) |
| Rate Limits | [rate-limits/clever-rate-limits.yml](rate-limits/clever-rate-limits.yml) |
| FinOps | [finops/clever-finops.yml](finops/clever-finops.yml) |

## Timestamps

- **Created:** 2026-06-13
- **Modified:** 2026-06-13

## Common

| Type | URL |
|------|-----|
| Website | https://clever.com |
| Documentation | https://dev.clever.com |
| GitHub Org | https://github.com/clever-inc |
| LinkedIn | https://www.linkedin.com/company/clever-inc-/ |
| Blog | https://www.clever.com/blog |
| Pricing | https://www.clever.com/pricing |
| Status Page | https://status.clever.com |
| X | https://twitter.com/clever |

## Maintainers

| Name | Email |
|------|-------|
| Kin Lane | kin@apievangelist.com |
