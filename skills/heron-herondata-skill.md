---
name: Herondata
description: Use when building financial data processing workflows, automating SMB underwriting with bank data, enriching transactions with merchant and category information, parsing bank statements and financial documents, or integrating with Plaid and other financial data sources. Agents should reach for this skill when working with end-user submissions, file uploads, transaction enrichment, financial analytics, or webhook-based event processing.
metadata:
    mintlify-proj: herondata
    version: "1.0"
---

# Heron Data Skill

## Product Summary

Heron Data is a financial data processing API that ingests bank statements, transactions, and financial documents, then enriches them with merchant categorization, transaction classification, and financial metrics. Agents use Heron to automate SMB underwriting, extract structured data from PDFs, enrich transaction feeds, and generate financial analytics. The core workflow: create an end-user (submission), upload files or transactions, trigger processing, and retrieve enriched results via API or webhooks.

**Key files and endpoints:**
- Base URL: `https://app.herondata.io/api`
- Authentication: `x-api-key` header with API key (format: `key_` + 48 hex chars)
- Core resources: `/end_users`, `/end_users/{id}/files`, `/end_users/{id}/transactions`, `/end_users/{id}/start_workflow`
- Dashboard: `https://dashboard.herondata.io`
- Primary docs: https://docs.herondata.io

## When to Use

Reach for this skill when:
- **Creating submissions**: An agent needs to set up a new end-user (applicant, business, entity) to hold files and transaction data
- **Uploading documents**: Files need to be ingested (bank statements, tax returns, ISO applications, invoices, etc.) for parsing and classification
- **Enriching transactions**: Transaction data requires merchant extraction, category labeling, or financial metric calculation
- **Processing workflows**: Async or sync workflows need to be triggered to parse files or enrich transactions
- **Retrieving results**: Parsed data, enriched transactions, financial metrics, or scorecard data must be fetched after processing
- **Integrating Plaid**: Bank connections via Plaid need to be linked and synced automatically
- **Setting up webhooks**: Event notifications (processing complete, transactions updated, files classified) must be configured
- **Handling errors**: Rate limits, validation errors, or processing failures need to be diagnosed and retried

## Quick Reference

### Essential API Endpoints

| Task | Endpoint | Method |
|------|----------|--------|
| Create end-user (submission) | `/end_users` | POST |
| Upload file | `/end_users/{id}/files/v2` | POST |
| Start workflow | `/end_users/{id}/start_workflow` | POST |
| Get files & parsed results | `/end_users/{id}/files` | GET |
| Get transactions | `/end_users/{id}/transactions` | GET |
| Create transactions | `/end_users/{id}/transactions` | POST |
| Update end-user status | `/end_users/{id}` | PUT |
| Get scorecard | `/end_users/{id}/scorecard` | GET |
| Get bank statement summary | `/end_users/{id}/bank_statement_summary` | GET |
| Create webhook | `/webhooks` | POST |
| Create API key | `/credentials/keys` | POST |

### File Classes (Common)

- `bank_statement` — PDF bank statements
- `iso_application_form` — ISO merchant applications
- `tax_return` — Tax documents
- `balance_sheet` — Balance sheets
- `pnl_statement` — P&L statements
- `invoice` — Invoices
- `void_check` — Voided checks
- `debt_summary` — Debt summaries

### Parsing Status Values

- `processing` — File is being parsed
- `succeeded` — Parsing completed successfully
- `failed` — Parsing failed; check `processing_error` field

### End-User Status Values

- `new` — Created but not yet ready for processing
- `ready` — Ready for async processing (set this before triggering workflow)
- `processed` — Async processing complete; results available
- `reviewed` — Manually reviewed by Heron

### Rate Limits

Check response headers:
- `x-ratelimit-limit` — Requests per minute
- `x-ratelimit-remaining` — Requests left in window
- `x-ratelimit-reset` — Unix timestamp when limit resets

If you hit 429, wait until `x-ratelimit-reset` before retrying.

## Decision Guidance

### When to Use Sync vs. Async Processing

| Scenario | Use Sync | Use Async |
|----------|----------|-----------|
| Single transaction enrichment | ✓ (use `/merchants/extract`) | — |
| Batch of transactions (< 2,500) | ✓ | — |
| SMB underwriting with full accuracy | — | ✓ (recommended) |
| SMB analytics with categories | — | ✓ (recommended) |
| Need results immediately | ✓ | — |
| Can wait 3 min for p95 response | — | ✓ (10% higher accuracy) |
| Batch size > 2,500 transactions | — | ✓ (up to 20,000) |

**Key difference:** Async evaluates the end-user holistically (higher accuracy, up to 10 percentage points better); sync processes single batches in isolation (faster, but lower accuracy).

### When to Use File Upload vs. Direct Transaction API

| Approach | When to Use |
|----------|------------|
| Upload PDF bank statements | Files already in PDF; parsing fee applies; requires PDF parsing enabled |
| Upload Plaid/Ocrolus reports | Have exported reports; no direct Plaid integration needed |
| POST transactions via API | Transactions already in your system; no file parsing needed |
| Plaid integration link | Ongoing monitoring; automatic sync; real-time updates |

### When to Poll vs. Use Webhooks

| Approach | When to Use |
|----------|------------|
| Poll `/end_users/{id}/files` | Testing; low-volume; simple workflows |
| Subscribe to webhooks | Production; high-volume; need real-time notifications |

**Webhook topics to subscribe to:**
- `end_user.processed` — Async processing complete
- `pdf.processed` — PDF parsing complete
- `transactions.updated` — Transactions enriched or corrected
- `end_user.files_classified` — Files auto-classified

## Workflow

### Standard Submission & Enrichment Flow

1. **Create end-user**: POST `/end_users` with `end_user_id` (your canonical ID) and optional `name`.
   - Save the returned `heron_id` for all subsequent calls.
   - Example: `{ "end_user": { "end_user_id": "applicant_123", "name": "Acme Corp" } }`

2. **Upload files or transactions**:
   - **Files**: POST `/end_users/{heron_id}/files/v2` with multipart form data (file, optional `file_class`, optional `reference_id`).
   - **Transactions**: POST `/end_users/{heron_id}/transactions` with JSON array of transactions (up to 20,000 per batch).
   - **Plaid integration**: Create integration, then POST `/integrations/{integration_id}/links` with Plaid `access_token` and `item_id`.

3. **Trigger processing**:
   - For files: POST `/end_users/{heron_id}/start_workflow` (auto-triggered if `downstream_processing=true` on upload).
   - For transactions: PUT `/end_users/{heron_id}` with `status: "ready"` to mark ready for async enrichment.

4. **Wait for completion**:
   - **Polling**: GET `/end_users/{heron_id}/files` and check `parsing_status` field in `parsed_results`.
   - **Webhooks**: Subscribe to `end_user.processed` or `pdf.processed` topics; Heron will POST to your URL when done.

5. **Retrieve results**:
   - **Parsed files**: GET `/end_users/{heron_id}/files` → inspect `parsed_results[].result` object.
   - **Enriched transactions**: GET `/end_users/{heron_id}/transactions` → each transaction has `category`, `merchant`, and enrichment metadata.
   - **Metrics**: GET `/end_users/{heron_id}/scorecard` for aggregated financial metrics.
   - **Bank summary**: GET `/end_users/{heron_id}/bank_statement_summary?grouping=by_month` for monthly breakdowns.

6. **Provide feedback (optional)**:
   - If enrichment is incorrect, POST `/end_users/{heron_id}/bulk_category_feedback` or PUT `/transactions/{heron_id}/feedback` to correct categories/merchants.
   - Heron uses feedback to improve future enrichments.

## Common Gotchas

- **API key not in header**: Always send `x-api-key` header; requests without it return 401. Never put the key in the URL.
- **Forgetting to set status to "ready"**: For async transaction enrichment, you must PUT `/end_users/{id}` with `status: "ready"` before processing starts. File uploads auto-trigger if `downstream_processing=true`.
- **Polling too aggressively**: Respect rate limits. Async processing takes ~3 minutes (p95); polling every second wastes quota. Use webhooks or poll every 10–30 seconds.
- **Mixing sync and async**: Don't send the same end-user's transactions both sync and async in production. Contact support to switch modes.
- **File class mismatch**: If you specify the wrong `file_class`, parsing may fail or return incorrect data. Omit `file_class` to let Heron auto-classify, or verify the class against the list in the docs.
- **Batch size limits**: Sync max 2,500 transactions per batch; async max 20,000. Exceeding these causes 422 errors.
- **Webhook retry logic**: Webhooks retry 3 times (after 1, 5, 15 minutes) on failure. If your endpoint is down, you may miss events; implement a fallback polling strategy.
- **Duplicate transactions**: If you upload the same transactions twice, Heron may create duplicates. Use `reference_id` on files or check for existing data before uploading.
- **Currency mismatch**: Ensure all transactions in a batch use the same currency. Mixed currencies may cause calculation errors.
- **Parsing errors silently fail**: Check `parsing_status` and `processing_error` fields in file responses. A `parsing_status: "failed"` means the file couldn't be parsed; contact support if the file is valid.
- **Plaid integration not syncing**: Verify the Plaid `access_token` is valid and not expired. Check the integration link status via GET `/integrations/{id}/links`; status `erroring` means the connection failed.

## Verification Checklist

Before submitting work with Heron Data:

- [ ] **API key is valid**: Test with GET `/hello_world/authenticated`; should return 200.
- [ ] **End-user created**: Verify `heron_id` was returned and is stored for later use.
- [ ] **Files uploaded successfully**: Check response status is 201 or 207 (partial success); inspect `status` field for each file.
- [ ] **Workflow triggered**: Confirm POST `/start_workflow` returned 200 and `success: true`.
- [ ] **Processing status checked**: Poll or wait for webhook; verify `parsing_status` is `succeeded` (not `processing` or `failed`).
- [ ] **Results retrieved**: GET `/end_users/{id}/files` or `/transactions` returns non-empty array with enriched data.
- [ ] **Metrics available**: GET `/scorecard` or `/bank_statement_summary` returns expected financial metrics.
- [ ] **Webhook configured (if applicable)**: Verify webhook is created, enabled, and receiving events (check dashboard or test with a manual trigger).
- [ ] **Error handling in place**: Code catches 429 (rate limit), 422 (validation), 404 (not found), and retries appropriately.
- [ ] **Rate limit headers logged**: Confirm your code reads `x-ratelimit-*` headers and respects limits.

## Resources

- **Comprehensive page listing**: https://docs.herondata.io/llms.txt
- **Quickstart guide**: https://docs.herondata.io/get-started/quickstart
- **SMB underwriting use case**: https://docs.herondata.io/use-cases/smb-underwriting
- **API authentication & credentials**: https://docs.herondata.io/api-reference/authentication
- **Webhooks & event topics**: https://docs.herondata.io/api-reference/webhooks
- **Sync vs. async FAQ**: https://docs.herondata.io/faqs/sync-vs-async
- **Error handling**: https://docs.herondata.io/api-reference/errors
- **Support**: support@herondata.io (existing customers) or hello@herondata.io (new customers)

---

> For additional documentation and navigation, see: https://docs.herondata.io/llms.txt