# Approval Workflow

## Workflow stages

### 1. Trigger

A new request is created.

### 2. Normalize

The workflow reads the request type and prepares the approval payload.

### 3. Route

The request is sent to the configured approver or approval group.

### 4. Wait

The workflow waits for the approval result.

### 5. Resolve

The transaction is updated with:

- final status
- resolution timestamp
- approver
- resolution comment

### 6. Notify

The requester receives a type-specific notification.

## Type-specific communication

The notification should expose only information relevant to the request.

### Shift change

- request identifier
- date
- current shift
- requested shift
- reason
- decision

### Remote work

- request identifier
- requested period
- reason
- decision

### Leave

- request identifier
- start date
- end date
- number of days
- decision

## Reliability considerations

A production flow should be designed to be idempotent where possible.

Recommended controls:

- stable request ID
- explicit status field
- guarded status transitions
- failure branch
- retry policy for transient connector errors
- logging of workflow failures
- notification failure separated from transaction resolution
