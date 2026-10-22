---
name: request-and-manage-leave
description: Create a leave request, validate it for approval and track it.
api: openapi/deputy-leave-request-api-openapi.yml
apis:
- openapi/deputy-leave-request-api-openapi.yml
operations:
- LeaveRequestV2Controller_create
- LeaveRequestV2Controller_validateLeaveRequestForApproval
- LeaveRequestV2Controller_get
- LeaveRequestV2Controller_list
- LeaveRequestV2Controller_update
generated: '2026-10-21'
method: generated
---

# Request and manage employee leave

Create a leave request, validate it for approval and track it.

## Steps

1. Create the request with `LeaveRequestV2Controller_create` (POST /management/v2/leave-requests).
2. Check it can be approved with `LeaveRequestV2Controller_validateLeaveRequestForApproval` (POST /management/v2/leave-requests/approval:validate).
3. Read it back with `LeaveRequestV2Controller_get`, list with `LeaveRequestV2Controller_list`, and amend with `LeaveRequestV2Controller_update` (PUT).

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
