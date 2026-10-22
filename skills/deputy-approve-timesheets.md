---
name: approve-timesheets
description: Find timesheets for a period and approve them (pay and time) ahead of payroll export.
api: openapi/deputy-timesheet-api-openapi.yml
apis:
- openapi/deputy-timesheet-api-openapi.yml
- openapi/deputy-timesheet-approval-api-openapi.yml
operations:
- listTimesheet
- getTimesheetById
- TsaV2Controller_approveTimesheet
- TsaV2Controller_approveTimeTimesheet
generated: '2026-10-21'
method: generated
---

# Review and approve timesheets for payroll

Find timesheets for a period and approve them (pay and time) ahead of payroll export.

## Steps

1. List candidate timesheets with `listTimesheet` (GET /resource/Timesheet) and inspect one with `getTimesheetById`.
2. Approve pay and time with `TsaV2Controller_approveTimesheet` (POST /tsa/v2/timesheets/{id}:approve), or time only with `TsaV2Controller_approveTimeTimesheet` (POST /tsa/v2/timesheets/{id}:approve-time).

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
