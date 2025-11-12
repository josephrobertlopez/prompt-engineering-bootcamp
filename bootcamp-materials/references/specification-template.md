# Feature Specification

**Location**: spec/specification.md
**Related**: knowledge-base.md (domain context), implementation-plan.md (how to build)
**Created**: [Date]
**Last Updated**: [Date]

**Small feature?** Just fill: Functional Requirements + Acceptance Criteria + Edge Cases
**API feature?** Add: API Contract + Business Rules
**Data feature?** Add: Data Model

---

## REQUIRED (Always fill these)

### Functional Requirements

- [ ] Requirement 1
- [ ] Requirement 2
- [ ] Requirement 3

### Acceptance Criteria

**MUST VERIFY** - How do we know we're done?

- [ ] Criterion 1 (testable)
- [ ] Criterion 2 (testable)
- [ ] Criterion 3 (testable)

---

## RECOMMENDED (Fill if applicable)

### User Story

**As a** [role]
**I want** [feature]
**So that** [benefit]

### API Contract

Document all endpoints this feature touches. Include:
- HTTP method + path
- Request body schema
- Response codes + bodies
- Authentication requirements

```
POST /api/v1/users
Request: {"email": "user@example.com", "name": "John Doe"}
Response 201: {"id": 123, "email": "user@example.com"}
Response 400: {"error": "Invalid email format"}
```

### Business Rules

- Rule 1: [Description]
- Rule 2: [Description]

---

## OPTIONAL (Add as needed)

### Data Model

- Entity: [UserProfile]
  - field1: [string (max 255)] [User's display name]
  - field2: [datetime] [Account creation timestamp]

### Edge Cases

- Case 1: [How to handle empty input]
- Case 2: [How to handle duplicate entries]

### Non-Functional Requirements

- Performance: [API response time < 200ms for 95th percentile]
- Security: [All passwords hashed with bcrypt]
- Scalability: [Support 10k concurrent users]

---

## Design Decisions

Record ABCD clarification decisions here:

- [Decision point]: Chose [option] because [reasoning]
- [Decision point]: Chose [option] because [reasoning]
