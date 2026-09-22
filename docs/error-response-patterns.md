# Error Response Patterns

Environmental and public-sector APIs should return clear, consistent, and actionable error responses.

## Standard Error Shape

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The submitted monitoring result is missing a required unit field.",
    "details": [
      {
        "field": "result.unit",
        "issue": "required"
      }
    ],
    "requestId": "req_demo_20260922_001"
  }
}
```

## Common Error Codes

```text
VALIDATION_ERROR
AUTHENTICATION_REQUIRED
ACCESS_DENIED
RESOURCE_NOT_FOUND
DUPLICATE_RECORD
CONFLICTING_VERSION
UNSUPPORTED_UNIT
INVALID_DATE_RANGE
SUBMISSION_LOCKED
RATE_LIMITED
```

## Recommended Practices

- Do not expose stack traces.
- Include a request identifier for support review.
- Provide field-level validation details where appropriate.
- Use consistent status codes and error codes.
- Avoid returning sensitive internal implementation details.

## Example: Locked Submission

```json
{
  "error": {
    "code": "SUBMISSION_LOCKED",
    "message": "This compliance submission has already been finalized and cannot be edited without reopening the review workflow.",
    "requestId": "req_demo_20260922_002"
  }
}
```
