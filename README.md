# Heron

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Heron (Heron Data) is a financial-services document-automation and cashflow-underwriting platform. Its API and AI platform handle document intake, classification, parsing and validation, enrichment, policy/rule evaluation, and CRM sync across 50+ document types (bank statements, tax returns, financial statements, ACORD forms). Lenders, MCA funders, brokers, and insurers upload documents for an "end user" (company), then read back parsed transactions, a Heron Score, scorecards, cashflow P&L, anomaly/fraud checks, and decline analytics. Heron publishes an OpenAPI 3.0 contract at app.herondata.io/swagger covering 226 paths and 272 operations, a conformant A2A agent card and a published Agent Skill on its documentation host, and a live unauthenticated MCP endpoint for documentation retrieval. The REST API authenticates with an x-api-key header, signals rate limits via x-ratelimit-* headers, and pushes async progress through webhooks. Backed by Insight Partners.

**Areas:** Company · Financial Services · Document Automation · Underwriting · Lending · Cash Flow Analytics · Fintech · Data Enrichment · Bank Statements · Transaction Enrichment · Agent Ready · A2A

## Heron on APIs.io

Everything profiled for Heron is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/heron/](https://apis.io/providers/heron/)** — or go straight to one of the APIs or properties below.

### APIs (47)

- [Heron Analytics API](https://apis.io/apis/heron/heron-analytics-api/) — The Analytics API from Heron — 1 operation(s) for analytics.
- [Heron Authentication API](https://apis.io/apis/heron/heron-authentication-api/) — The Authentication API from Heron — 1 operation(s) for authentication.
- [Heron Broker Funder Policies API](https://apis.io/apis/heron/heron-broker-funder-policies-api/) — The Broker Funder Policies API from Heron — 10 operation(s) for broker funder policies.
- [Heron Broker Submissions API](https://apis.io/apis/heron/heron-brokersubmissions-api/) — The BrokerSubmissions API from Heron — 6 operation(s) for brokersubmissions.
- [Heron Categories API](https://apis.io/apis/heron/heron-categories-api/) — The Categories API from Heron — 1 operation(s) for categories.
- [Heron Clear API](https://apis.io/apis/heron/heron-clear-api/) — The Clear API from Heron — 2 operation(s) for clear.
- [Heron Credentials API](https://apis.io/apis/heron/heron-credentials-api/) — The Credentials API from Heron — 4 operation(s) for credentials.
- [Heron CRM Integrations API](https://apis.io/apis/heron/heron-crmintegrations-api/) — The CrmIntegrations API from Heron — 2 operation(s) for crmintegrations.
- [Heron End Users API](https://apis.io/apis/heron/heron-end-users-api/) — The End Users API from Heron — 3 operation(s) for end users.
- [Heron End User Attributes API](https://apis.io/apis/heron/heron-enduserattributes-api/) — The EndUserAttributes API from Heron — 1 operation(s) for enduserattributes.
- [Heron End User Calculations API](https://apis.io/apis/heron/heron-endusercalculations-api/) — The EndUserCalculations API from Heron — 18 operation(s) for endusercalculations.
- [Heron End User Data Source Accounts API](https://apis.io/apis/heron/heron-enduserdatasourceaccounts-api/) — The EndUserDataSourceAccounts API from Heron — 3 operation(s) for enduserdatasourceaccounts.
- [Heron End User Data Sources API](https://apis.io/apis/heron/heron-enduserdatasources-api/) — The EndUserDataSources API from Heron — 3 operation(s) for enduserdatasources.
- [Heron End User Emails API](https://apis.io/apis/heron/heron-enduseremails-api/) — The EndUserEmails API from Heron — 1 operation(s) for enduseremails.
- [Heron End User Enrichers API](https://apis.io/apis/heron/heron-enduserenrichers-api/) — The EndUserEnrichers API from Heron — 5 operation(s) for enduserenrichers.
- [Heron End User Entity API](https://apis.io/apis/heron/heron-enduserentity-api/) — The EndUserEntity API from Heron — 14 operation(s) for enduserentity.
- [Heron End User Files API](https://apis.io/apis/heron/heron-enduserfiles-api/) — The EndUserFiles API from Heron — 18 operation(s) for enduserfiles.
- [Heron End User Financials API](https://apis.io/apis/heron/heron-enduserfinancials-api/) — The EndUserFinancials API from Heron — 1 operation(s) for enduserfinancials.
- [Heron End User Integrations API](https://apis.io/apis/heron/heron-enduserintegrations-api/) — The EndUserIntegrations API from Heron — 15 operation(s) for enduserintegrations.
- [Heron End User Queries API](https://apis.io/apis/heron/heron-enduserqueries-api/) — The EndUserQueries API from Heron — 1 operation(s) for enduserqueries.
- [Heron End User Rules API](https://apis.io/apis/heron/heron-enduserrules-api/) — The EndUserRules API from Heron — 1 operation(s) for enduserrules.
- [Heron Enriched Transactions API](https://apis.io/apis/heron/heron-enrichedtransactions-api/) — The EnrichedTransactions API from Heron — 2 operation(s) for enrichedtransactions.
- [Heron Enrichment Feedback API](https://apis.io/apis/heron/heron-enrichmentfeedback-api/) — The EnrichmentFeedback API from Heron — 4 operation(s) for enrichmentfeedback.
- [Heron File Class API](https://apis.io/apis/heron/heron-fileclass-api/) — The FileClass API from Heron — 4 operation(s) for fileclass.
- [Heron Funder Integrations API](https://apis.io/apis/heron/heron-funder-integrations-api/) — The Funder Integrations API from Heron — 4 operation(s) for funder integrations.
- [Heron Funder Submissions API](https://apis.io/apis/heron/heron-funder-submissions-api/) — The Funder Submissions API from Heron — 3 operation(s) for funder submissions.
- [Heron Funders API](https://apis.io/apis/heron/heron-funders-api/) — The Funders API from Heron — 4 operation(s) for funders.
- [Heron Ingestion API](https://apis.io/apis/heron/heron-ingestion-api/) — The Ingestion API from Heron — 1 operation(s) for ingestion.
- [Heron Integrations API](https://apis.io/apis/heron/heron-integrations-api/) — The Integrations API from Heron — 9 operation(s) for integrations.
- [Heron Interaction Logs API](https://apis.io/apis/heron/heron-interaction-logs-api/) — The Interaction Logs API from Heron — 1 operation(s) for interaction logs.
- [Heron ISO Application API](https://apis.io/apis/heron/heron-isoapplication-api/) — The ISOApplication API from Heron — 6 operation(s) for isoapplication.
- [Heron Merchants API](https://apis.io/apis/heron/heron-merchants-api/) — The Merchants API from Heron — 6 operation(s) for merchants.
- [Heron Parsed End User Submission API](https://apis.io/apis/heron/heron-parsedendusersubmission-api/) — The ParsedEndUserSubmission API from Heron — 1 operation(s) for parsedendusersubmission.
- [Heron Policy API](https://apis.io/apis/heron/heron-policy-api/) — The Policy API from Heron — 3 operation(s) for policy.
- [Heron Positions API](https://apis.io/apis/heron/heron-positions-api/) — The Positions API from Heron — 2 operation(s) for positions.
- [Heron Rules API](https://apis.io/apis/heron/heron-rules-api/) — The Rules API from Heron — 3 operation(s) for rules.
- [Heron Tags API](https://apis.io/apis/heron/heron-tags-api/) — The Tags API from Heron — 4 operation(s) for tags.
- [Heron Testing API](https://apis.io/apis/heron/heron-testing-api/) — The Testing API from Heron — 2 operation(s) for testing.
- [Heron Transactions API](https://apis.io/apis/heron/heron-transactions-api/) — The Transactions API from Heron — 2 operation(s) for transactions.
- [Heron User Merchant Groups API](https://apis.io/apis/heron/heron-usermerchantgroups-api/) — The UserMerchantGroups API from Heron — 1 operation(s) for usermerchantgroups.
- [Heron Users API](https://apis.io/apis/heron/heron-users-api/) — The Users API from Heron — 4 operation(s) for users.
- [Heron Watermarks API](https://apis.io/apis/heron/heron-watermarks-api/) — The Watermarks API from Heron — 1 operation(s) for watermarks.
- [Heron Webhooks API](https://apis.io/apis/heron/heron-webhooks-api/) — The Webhooks API from Heron — 3 operation(s) for webhooks.
- [Heron Workflows API](https://apis.io/apis/heron/heron-workflows-api/) — The Workflows API from Heron — 22 operation(s) for workflows.
- [Heron App Store API](https://apis.io/apis/heron/heron-app-store-api/) — The App Store API from Heron — 1 operation(s) for app store.
- [Heron Email Templates API](https://apis.io/apis/heron/heron-email-templates-api/) — The Email Templates API from Heron — 2 operation(s) for email templates.
- [Heron End User Accounts API](https://apis.io/apis/heron/heron-end-user-accounts-api/) — The End User Accounts API from Heron — 1 operation(s) for end user accounts.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Heron Webhooks](https://apis.io/asyncapis/heron/heron-webhooks-asyncapi/)

#### Event channels (11)

Individual events and webhooks the provider emits.

- [end_user.processed](https://apis.io/channels/heron/end-user-processed/)
- [end_user.review_required](https://apis.io/channels/heron/end-user-review-required/)
- [end_user.reviewed](https://apis.io/channels/heron/end-user-reviewed/)
- [end_user.transactions_updated](https://apis.io/channels/heron/end-user-transactions-updated/)
- [pdf.checks_failed](https://apis.io/channels/heron/pdf-checks-failed/)
- [pdf.checks_passed](https://apis.io/channels/heron/pdf-checks-passed/)
- [pdf.failed](https://apis.io/channels/heron/pdf-failed/)
- [pdf.processed](https://apis.io/channels/heron/pdf-processed/)
- [pdf.transactions_loaded](https://apis.io/channels/heron/pdf-transactions-loaded/)
- [transactions.deleted](https://apis.io/channels/heron/transactions-deleted/)
- [transactions.updated](https://apis.io/channels/heron/transactions-updated/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [heron](https://apis.io/servers/heron/heron/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Heron Openapi Overlay](https://apis.io/overlays/heron/heron-openapi-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Heron Authentication](https://apis.io/security/heron/heron-authentication/)
- [Heron Domain Security](https://apis.io/security/heron/heron-domain-security/)
- [Heron Trust Center](https://apis.io/security/heron/heron-trust-center/)
- [Heron Vulnerability Disclosure](https://apis.io/security/heron/heron-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Heron Plans Pricing](https://apis.io/plans/heron/heron-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Heron Rate Limits](https://apis.io/rate-limits/heron/heron-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.herondata.io/)
- [Documentation](https://docs.herondata.io/)
- [Getting started](https://docs.herondata.io/)
- [API reference](https://docs.herondata.io/api-reference/authentication)
- [Blog](https://www.herondata.io/blog)
- [Security](https://www.herondata.io/disclosure)
- [Compliance](https://www.herondata.io/security)
- [Terms of service](https://www.herondata.io/terms)
- [Privacy policy](https://www.herondata.io/privacy-policy)
- [GitHub](https://github.com/heron-data)
- [Status](https://status.herondata.io/)

## API Evangelist rating

**Kin Score 62.1** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 56.9 |
| Contract governance | 18.2 |
| Operational transparency | 73.7 |
| Developer ergonomics | 78.6 |
| Access clarity | 43.4 |

**Agent readiness 27.6** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | mostly (partial credit) |

**Regulatory alignment 36.0** — Insurance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/heron/](https://apis.io/providers/heron/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Heron: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/heron/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
