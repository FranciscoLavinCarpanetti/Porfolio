# Data Model

## Request entity

The portfolio implementation uses a simplified request model.

| Field | Type | Purpose |
|---|---|---|
| id | Integer / GUID | Stable request identifier |
| requestType | Choice | Shift change, remote work, leave |
| requester | Text / reference | Person creating the request |
| requestDate | DateTime | Creation timestamp |
| status | Choice | Pending, approved, rejected |
| startDate | Date | Start of requested period |
| endDate | Date | End of requested period |
| daysRequested | Integer | Inclusive number of requested days |
| currentShift | Choice | Current shift where applicable |
| requestedShift | Choice | Requested shift where applicable |
| reason | Multiline text | Business justification |
| approver | Text / reference | Decision owner |
| resolutionDate | DateTime | Decision timestamp |
| resolutionComment | Multiline text | Decision explanation |

## Inclusive date calculation

For a request covering both start and end dates:

```text
daysRequested = dateDiff(startDate, endDate) + 1
```

This prevents the common off-by-one error in inclusive leave periods.

## Validation rules

### Leave

- Start date is required.
- End date is required.
- End date must not precede start date.
- Reason is not required by default.

### Shift change

- Date is required.
- Current shift is required.
- Requested shift is required.
- Reason is required.

### Remote work

- Start date is required.
- End date is required.
- Reason is required.

## Status transitions

Only the workflow should normally move a request from:

```text
Pending -> Approved
Pending -> Rejected
```

A completed request should not be silently overwritten by a subsequent submission.
