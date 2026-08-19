---
generated: '2026-08-14'
method: generated
name: Underwrite an end user
description: After documents are processed, pull the Heron Score, scorecard, and cashflow analytics to underwrite a company.
api: Heron REST API (https://app.herondata.io/api)
operations:
  - GET /api/end_users/{end_user_id_or_heron_id}/heron_score
  - GET /api/end_users/{end_user_id_or_heron_id}/scorecard
  - GET /api/end_users/{end_user_id_or_heron_id}/bank_statement_summary
  - GET /api/end_users/{end_user_id_or_heron_id}/profit_and_loss
  - GET /api/analytics/decline
source: >-
  Grounded in Heron's API reference (docs.herondata.io/api-reference/
  endusercalculations and /analytics) and verified against the published contract
  openapi/heron-openapi.json (harvested from https://app.herondata.io/swagger).
  Every path cited below exists in that spec. The spec declares an operationId on
  only 1 of 272 operations, so steps cite the real HTTP method+path.
---

# Underwrite an end user

Turn processed transaction data into an underwriting decision using Heron's calculation and analytics endpoints.

## Auth
- `x-api-key` header (`key_` + 48 hex). See `authentication/heron-authentication.yml`.

## Prerequisites
- The end user's documents have been parsed (see `heron-parse-and-retrieve-documents.md`) and the `end_user.processed` webhook has fired.

## Steps
1. **Get the Heron Score (beta)** — `GET /api/end_users/{end_user_id_or_heron_id}/heron_score` returns the creditworthiness score with its feature-group contribution breakdown.
2. **Get the scorecard** — `GET /api/end_users/{end_user_id_or_heron_id}/scorecard` returns scorecard metrics and rule violations. If a rule is violated, expect the `end_user.review_required` webhook. Use `/scorecard/async` to request one for a date.
3. **Get the bank-statement summary** — `GET /api/end_users/{end_user_id_or_heron_id}/bank_statement_summary` returns the by-month summary.
4. **Get the cashflow P&L** — `GET /api/end_users/{end_user_id_or_heron_id}/profit_and_loss` returns the computed profit-and-loss table; adjust `/profit_and_loss_layout` first if the default layout is wrong.
5. **Review decline analytics** — `GET /api/analytics/decline` returns portfolio-level pass/fail/missing counts across a date range. Returns 400 if analytics is not configured for the account.

## Conventions
- Beta endpoints (Heron Score, Missing Accounts) may change; check the reference before relying on their shape. See `lifecycle/heron-lifecycle.yml`.
- Honor rate-limit headers; see `conventions/heron-conventions.yml`.

## Errors
- `{code, description, name}` envelope; see `errors/heron-error-codes.yml` and the contract census in `errors/heron-problem-types.yml`. A 404 here can mean the end user belongs to another account, not that it does not exist.
