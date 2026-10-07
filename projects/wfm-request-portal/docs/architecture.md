# Architecture

## 1. Design principles

The solution follows five principles:

1. **Separation of concerns** — UI, data and workflow are independent layers.
2. **Traceability** — every request has a stable identifier and resolution information.
3. **Type-specific UX** — users only see fields relevant to the selected request type.
4. **Configuration over hard-coding** — environment-dependent values should be externalized.
5. **Progressive automation** — automate the workflow without hiding the operational decision.

## 2. Logical architecture

```text
+-------------------------+
|       User / Manager    |
+------------+------------+
             |
             v
+-------------------------+
|      Request Portal     |
|       Canvas App        |
+------------+------------+
             |
             v
+-------------------------+
|     Transaction Store   |
|     Structured Lists    |
+------------+------------+
             |
             v
+-------------------------+
|    Workflow Engine      |
|   Approval + Routing    |
+------------+------------+
             |
       +-----+-----+
       |           |
       v           v
   Approved     Rejected
       |           |
       +-----+-----+
             |
             v
+-------------------------+
| Notification + History  |
+-------------------------+
```

## 3. Separation of data

The transactional entity stores the request itself:

- requester
- request type
- request dates
- requested shift information
- reason
- status
- approver
- resolution date
- resolution comment

Operational configuration should live separately:

- teams
- available shifts
- approvers
- environment-specific settings
- notification configuration

This prevents workflow logic from becoming tightly coupled to transactional records.

## 4. Workflow

```text
Create request
      |
      v
Validate
      |
      v
Persist request
      |
      v
Start approval
      |
      +----------+
      |          |
      v          v
  Approved    Rejected
      |          |
      +-----+----+
            |
            v
      Update status
            |
            v
      Send notification
```

## 5. Error handling

Production implementations should explicitly handle:

- approval timeout
- connector failure
- invalid recipient
- missing configuration
- duplicate submission
- concurrent updates
- notification failure

The request record should remain traceable even when a downstream notification fails.
