# Environmental API Design Principles

Environmental and infrastructure software APIs should be designed for clarity, traceability, data quality, and long-term operational use.

## Core Principles

### 1. Use clear resource names

APIs should describe operational entities clearly:

```text
facilities
monitoring-stations
sample-results
inspection-records
incident-reports
compliance-submissions
evidence-records
```

### 2. Preserve audit context

Regulated workflows should preserve who submitted data, when it was submitted, what changed, and what evidence supports the record.

Example fields:

```json
{
  "createdBy": "demo.user@example.org",
  "createdAt": "2026-09-22T14:30:00Z",
  "reviewStatus": "pending_review",
  "evidenceRecordId": "ev_demo_001"
}
```

### 3. Separate draft, review, and submitted states

Environmental reports often move through lifecycle states:

```text
draft
submitted
under_review
approved
rejected
revised
archived
```

### 4. Include data quality metadata

Monitoring and reporting APIs should preserve information about method, source, units, confidence, and validation status.

### 5. Avoid silent overwrites

Updates should preserve change history. Systems should avoid replacing regulated data without an audit trail.

## Non-Production Notice

This document is a public demonstration guide. It does not describe any private Prime Logic production API.
