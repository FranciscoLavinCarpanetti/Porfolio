# WFM Request Portal

> Portfolio project — independent reconstruction inspired by workforce-management automation patterns.

A workflow-oriented portal for managing workforce requests such as shift changes, remote-work requests and leave requests.

The project demonstrates how a manual request process can be transformed into a structured, auditable workflow using a low-code architecture.

## Architecture

```text
Employee / Coordinator
        |
        v
   Request Portal
        |
        v
 Structured Data Store
        |
        v
 Approval Workflow
        |
   +----+----+
   |         |
Approved   Rejected
   |         |
   +----+----+
        |
        v
 Notifications + Audit Trail
```

## Functional scope

- Request creation by type.
- Type-specific forms.
- Validation of required fields.
- Request status lifecycle.
- Approval / rejection workflow.
- Resolution comments.
- Request history.
- Notifications based on request type and outcome.
- Separation between transactional data and operational configuration.

## Request types

| Type | Example information |
|---|---|
| Shift change | Current shift, requested shift, date, reason |
| Remote work | Requested dates, reason |
| Leave | Start date, end date, calculated number of days |

## Status lifecycle

```text
Pending
   |
   +----> Approved
   |
   +----> Rejected
```

## Technical concepts demonstrated

- Low-code application architecture.
- Workflow orchestration.
- Approval patterns.
- Data validation.
- Separation of UI, data and automation.
- Auditability.
- Environment-independent configuration.
- Power Platform ALM concepts.

## Portfolio note

This repository contains an **independent portfolio implementation**. It does not contain Telpark source code, credentials, internal URLs, employee data, SharePoint exports, or corporate configuration.

The objective is to demonstrate the engineering approach and architecture without exposing proprietary material.

## Roadmap

- [ ] Canvas App implementation
- [ ] Power Automate flow definitions
- [ ] Sample data
- [ ] Automated validation
- [ ] ALM / Solution structure
- [ ] DEV / TEST / PROD configuration model
- [ ] Architecture diagrams
- [ ] Demo screenshots
