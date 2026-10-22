---
name: subscribe-to-webhooks
description: Register, list and remove webhook subscriptions so an integration is notified of Deputy record changes.
api: openapi/deputy-webhook-api-openapi.yml
apis:
- openapi/deputy-webhook-api-openapi.yml
operations:
- createWebhook
- listWebhook
- getWebhookById
- deleteWebhook
generated: '2026-10-21'
method: generated
---

# Subscribe to Deputy webhooks

Register, list and remove webhook subscriptions so an integration is notified of Deputy record changes.

## Steps

1. Register a subscription with `createWebhook` (POST /resource/Webhook); see https://developer.deputy.com/docs/webhook-overview for topics and payloads.
2. List subscriptions with `listWebhook` and read one with `getWebhookById`.
3. Remove a subscription with `deleteWebhook` (DELETE /resource/Webhook/{id}).

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
