---
name: onboard-an-employee
description: Create an employee, assign them to a location and invite them to Deputy.
api: openapi/deputy-employees-api-openapi.yml
apis:
- openapi/deputy-employees-api-openapi.yml
operations:
- Addanemployee
- Addalocationagainstanemployee
- InviteemployeetoDeputy
- Getdetailsforaemployeebyid
- EmployeesV2Controller_create
generated: '2026-10-21'
method: generated
---

# Add and onboard an employee

Create an employee, assign them to a location and invite them to Deputy.

## Steps

1. Create the employee with `Addanemployee` (POST /v1/supervise/employee), or the v2 setup `EmployeesV2Controller_create` (POST /management/v2/employees).
2. Link them to a location with `Addalocationagainstanemployee` (POST /v1/supervise/employee/{employeeid}/assoc/{locationid}).
3. Send the invitation with `InviteemployeetoDeputy` (POST /v1/supervise/employee/{employeeid}/invite).
4. Confirm with `Getdetailsforaemployeebyid`.

## Rules

- Base URL is your tenant: `https://{subdomain}.{region}.deputy.com/api` (region au, eu, na or deputy), per the spec `servers`.
- Authenticate with an OAuth 2.0 access token or a permanent API token as a Bearer token; see ../authentication/deputy-authentication.yml.
- Write calls are not documented as idempotent. Before retrying a create, list or query first so you do not create a duplicate.
- Error shapes: ../errors/deputy-problem-types.yml.
