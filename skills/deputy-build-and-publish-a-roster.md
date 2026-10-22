---
name: build-and-publish-a-roster
description: Create shifts for employees in an area, optionally auto-build them, then publish the roster so employees are notified.
api: openapi/deputy-roster-api-openapi.yml
apis:
- openapi/deputy-roster-api-openapi.yml
- openapi/deputy-schedule-agent-api-openapi.yml
operations:
- createRoster
- supervise_roster__post
- ScheduleAgentV2Controller_upsertShifts
- supervise_roster__autobuild_post
- supervise_roster__checkautobuild_jobkey_get
- supervise_roster__publish_post
- listRoster
generated: '2026-10-21'
method: generated
---

# Build and publish a roster (schedule shifts)

Create shifts for employees in an area, optionally auto-build them, then publish the roster so employees are notified.

## Steps

1. List existing shifts for the period with `listRoster` (GET /resource/Roster) to avoid double-booking.
2. Create a single shift with `createRoster` (POST /resource/Roster) or the supervise endpoint `supervise_roster__post` (POST /supervise/roster).
3. For batches, `ScheduleAgentV2Controller_upsertShifts` (POST /agent/schedule/v2/shifts:upsert) creates or updates up to 500 shifts per request; items are processed independently and partial failures are allowed, so inspect every item result. Use id=0 or omit id to create.
4. To let Deputy build the schedule, call `supervise_roster__autobuild_post` and poll `supervise_roster__checkautobuild_jobkey_get` with the returned job key.
5. Publish with `supervise_roster__publish_post` (POST /supervise/roster/publish).

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
