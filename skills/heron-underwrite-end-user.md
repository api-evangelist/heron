---
generated: '2026-07-19'
method: generated
name: Underwrite an end user
description: After documents are processed, pull the Heron Score, scorecard, and cashflow analytics to underwrite a company.
api: Heron REST API (https://app.herondata.io/api)
operations:
  - GET EndUser Heron Score (beta)
  - GET EndUser scorecard
  - GET EndUser bank statement summary
  - GET EndUser cashflow P&L
  - GET decline analytics for a user
source: >-
  Grounded in Heron's API reference (docs.herondata.io/api-reference/
  endusercalculations and /analytics). Steps cite documented operation pages
  since no consolidated OpenAPI is published.
---

# Underwrite an end user

Turn processed transaction data into an underwriting decision using Heron's calculation and analytics endpoints.

## Auth
- `x-api-key` header (`key_` + 48 hex). See `authentication/heron-authentication.yml`.

## Prerequisites
- The end user's documents have been parsed (see `heron-parse-and-retrieve-documents.md`) and the `end_user.processed` webhook has fired.

## Steps
1. **Get the Heron Score (beta)** — retrieve the creditworthiness score with its feature-group contribution breakdown (`docs.herondata.io/api-reference/endusercalculations/get-enduser-heron-score-beta.md`).
2. **Get the scorecard** — pull scorecard metrics and rule violations (`.../get-enduser-scorecard.md`). If a rule is violated, expect the `end_user.review_required` webhook.
3. **Get the bank-statement summary** — monthly summary for the end user (`.../get-enduser-bank-statement-summary.md`).
4. **Get the cashflow P&L** — computed profit-and-loss table (`.../get-enduser-cashflow-p&l.md`); adjust the layout first with the P&L-layout update if needed.
5. **Review decline analytics** — for portfolio-level pass/fail/missing counts across a date range (`.../analytics/get-decline-analytics-for-a-user.md`).

## Conventions
- Beta endpoints (Heron Score, Missing Accounts) may change; check the reference before relying on their shape. See `lifecycle/heron-lifecycle.yml`.
- Honor rate-limit headers; see `conventions/heron-conventions.yml`.

## Errors
- `{code, description, name}` envelope; see `errors/heron-error-codes.yml`.
