# Daisychain API Request: Messaging & Analytics Endpoints

This repo contains a proposed OpenAPI 3.1 spec requesting new endpoints for the [Daisychain API](https://go.daisychain.app/api-docs/index.html).

## Why

We currently rely on manual CSV exports (messages, campaigns, flows, people) to power an SMS analytics dashboard. This is slow, error-prone, and prevents real-time reporting. These endpoints would let us query the same data programmatically.

## What's Proposed

15 new **read-only** (GET) endpoints across 4 resource groups:

| Group | Endpoints | Description |
|---|---|---|
| **Messages** | `/messages`, `/messages/{id}`, `/people/{id}/messages` | List/filter messages by person, direction, campaign, date range |
| **Broadcasts** | `/broadcasts`, `/broadcasts/{id}`, `…/messages`, `…/variants`, `…/metrics` | Campaign listing, A/B variant details, and aggregate engagement metrics |
| **Automations** | `/automations`, `/automations/{id}`, `…/messages`, `…/metrics` | Flow listing, node-level message filtering, and aggregate metrics |
| **Conversations** | `/conversations/{id}`, `…/messages` | Conversation threads and chronological message history |

All endpoints use the existing `/api/v1/` prefix, `X-API-Token` authentication, and pagination conventions.

### Metrics Endpoints

The `…/metrics` endpoints provide pre-computed analytics that currently require client-side computation from raw CSV data:

- Response rate, opt-out rate, active responder rate
- Engagement depth (1, 2+, 3+ response buckets)
- Per-variant breakdowns of all the above

## Viewing the Spec

- **On GitHub**: Open [`daisychain-proposed-endpoints.yaml`](daisychain-proposed-endpoints.yaml) directly
- **Swagger UI**: Copy the [raw file URL](https://raw.githubusercontent.com/ariel-aipluso/daisychain-api-request/main/daisychain-proposed-endpoints.yaml) and paste it into [editor.swagger.io](https://editor.swagger.io)
