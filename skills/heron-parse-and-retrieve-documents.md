---
generated: '2026-08-14'
method: generated
name: Parse documents and retrieve results
description: Create an end user, upload PDF documents, run processing, and retrieve the parsed results.
api: Heron REST API (https://app.herondata.io/api)
operations:
  - POST /end_users
  - POST /end_users/{end_user_id_or_heron_id}/files/v2
  - POST /end_users/{end_user_id_or_heron_id}/start_workflow
  - GET /end_users/{end_user_id_or_heron_id}/files
source: >-
  Grounded in Heron's quickstart and API reference (docs.herondata.io) and verified
  against the published contract openapi/heron-openapi.json (harvested from
  https://app.herondata.io/swagger). Every path cited below exists in that spec. The
  spec declares an operationId on only 1 of 272 operations, so steps cite the real
  HTTP method+path rather than operationIds.
---

# Parse documents and retrieve results

Intake documents for a company (end user), parse them, and read back the structured output.

## Auth
- Send your API key in the `x-api-key` header (`key_` + 48 hex). See `authentication/heron-authentication.yml`.
- Use development credentials during onboarding; production credentials are issued separately.

## Steps
1. **Create the end user** — `POST /end_users` with your `end_user_id` (your own identifier) and company details. Capture the returned `heron_id` (`eus_...`).
2. **Upload documents** — `POST /end_users/{end_user_id_or_heron_id}/files/v2` with one or more PDFs (bank statements, tax returns, financial statements).
3. **Start processing** — `POST /end_users/{end_user_id_or_heron_id}/start_workflow` to kick off asynchronous parsing/classification/enrichment.
4. **Wait for completion** — subscribe to the `end_user.processed` webhook (and `pdf.processed` / `pdf.checks_passed`) rather than polling. See `asyncapi/heron-webhooks-asyncapi.yml`.
5. **Retrieve results** — `GET /end_users/{end_user_id_or_heron_id}/files` to read the parsed files and extracted data.

## Conventions
- Rate limits are per-endpoint/per-customer; read `x-ratelimit-remaining` / `x-ratelimit-reset` and back off on 429. See `conventions/heron-conventions.yml`.
- End users are addressable by either your `end_user_id` or the Heron `heron_id`.

## Errors
- Errors use `{code, description, name}`; a 422 `description` is an object of field-level validation messages. See `errors/heron-error-codes.yml`.
