---
name: clock-an-employee-on-and-off
description: 'Run the timesheet lifecycle for an employee: start, pause/unpause for breaks, end, then read the resulting timesheet.'
api: openapi/deputy-timesheet-api-openapi.yml
apis:
- openapi/deputy-timesheet-api-openapi.yml
- openapi/deputy-timesheets-api-openapi.yml
operations:
- Startanemployeestimesheet(ClockOn)
- Pauseorunpauseemployeestimesheet(takeabreak/finishbreak)
- Stopanemployeestimesheet(ClockOff)
- Viewatimesheetbyid
- listTimesheet
generated: '2026-10-21'
method: generated
---

# Clock an employee on, take a break, and clock off

Run the timesheet lifecycle for an employee: start, pause/unpause for breaks, end, then read the resulting timesheet.

## Steps

1. Start the timesheet with `Startanemployeestimesheet(ClockOn)` (POST /v1/supervise/timesheet/start).
2. Toggle a break with `Pauseorunpauseemployeestimesheet(takeabreak/finishbreak)` (POST /v1/supervise/timesheet/pause); the same call starts and finishes a break.
3. End the shift with `Stopanemployeestimesheet(ClockOff)` (POST /v1/supervise/timesheet/end).
4. Read the result with `Viewatimesheetbyid` (GET /v1/supervise/timesheet/{timesheetid}/details), or list with `listTimesheet`.

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
