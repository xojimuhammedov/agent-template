# AI Coding Guidelines

These instructions apply to every coding task in this repository.

Project-specific instructions override general instructions when there is a conflict.

---

## 1. Think Before Coding

Do not start implementation immediately.

Before changing code:

* Understand the requested outcome.
* Inspect the existing implementation and related files.
* State important assumptions explicitly.
* Identify unclear or conflicting requirements.
* Present multiple interpretations when more than one is reasonable.
* Mention a simpler solution when one exists.
* Do not silently invent missing business rules.
* Do not introduce a new dependency without explaining why it is necessary.

For multi-step tasks, provide a short plan:

```text
1. Inspect the current implementation → verify existing behavior
2. Implement the minimum required change → verify expected behavior
3. Run relevant checks → verify no regression
```

Do not ask unnecessary questions when the answer can be determined from the repository.

---

## 2. Define Success Criteria

Before implementation, convert the request into verifiable outcomes.

Examples:

```text
Fix login bug
→ Reproduce the failed login case
→ Apply the smallest fix
→ Confirm successful and failed login scenarios
```

```text
Add form validation
→ Define valid and invalid inputs
→ Implement validation
→ Confirm error messages and submission behavior
```

A task is complete only when:

* The requested behavior works.
* Relevant tests or checks pass.
* Existing behavior has not been unintentionally changed.
* No temporary logs, commented code, or unused imports remain.

---

## 3. Simplicity First

Write the minimum code needed to solve the requested problem.

* Do not add features that were not requested.
* Do not create abstractions for one-time logic.
* Do not add configuration for hypothetical future use cases.
* Do not introduce unnecessary design patterns.
* Prefer existing utilities and components over creating duplicates.
* Prefer readable code over clever code.
* Avoid premature optimization.
* Avoid unnecessary comments that only repeat the code.

Before finishing, ask:

> Could this implementation be meaningfully simpler without reducing correctness?

If yes, simplify it.

---

## 4. Surgical Changes

Only modify code directly related to the request.

* Do not reformat unrelated files.
* Do not rename unrelated variables or folders.
* Do not refactor surrounding code unless required.
* Match the repository’s existing coding style.
* Do not replace working libraries or architecture without being asked.
* Mention unrelated problems instead of fixing them silently.

When your changes make something unused:

* Remove imports, variables, functions, and files made unused by your changes.
* Do not remove pre-existing dead code unless requested.

Every changed line must be traceable to the requested outcome.

---

## 5. Inspect Before Creating

Before creating a new:

* Component
* Hook
* Service
* Utility
* DTO
* Schema
* Middleware
* Guard
* Repository
* Database table
* API endpoint

Search the repository for an existing equivalent.

Reuse or extend an existing implementation when appropriate.

Do not create duplicate business logic in different layers.

---

# Frontend Guidelines

## 6. Respect Existing Frontend Architecture

Before implementing frontend changes, inspect:

* Routing structure
* State management
* API client
* Component organization
* Design system
* Form handling
* Validation library
* Authentication flow
* Error handling conventions

Use the existing approach unless the task explicitly requires changing it.

Do not introduce a second state management, form, styling, or request library for a small feature.

---

## 7. Component Responsibility

Keep components focused.

* Page components coordinate data and layout.
* UI components render reusable interface elements.
* Hooks handle reusable stateful behavior.
* API functions handle network communication.
* Business logic should not be hidden inside large JSX blocks.

Do not split a simple component into many files without a clear benefit.

Do not create a generic component when it is only used once and has no meaningful reusable behavior.

---

## 8. UI States

For data-driven interfaces, explicitly handle relevant states:

* Initial state
* Loading state
* Empty state
* Success state
* Error state
* Disabled or submitting state

Only implement states relevant to the actual feature.

Do not show stale success data as if a failed request succeeded.

Prevent duplicate form submissions and repeated actions when needed.

---

## 9. Forms and Validation

For forms:

* Define which fields are required.
* Match frontend validation with backend validation.
* Display actionable validation messages.
* Preserve user-entered values after recoverable errors.
* Prevent submission when the form is invalid.
* Avoid duplicating the same validation logic across multiple components.

Do not trust frontend validation as a security boundary.

---

## 10. API Integration

When integrating an API:

* Inspect the actual request and response contract.
* Do not guess field names or response shapes.
* Keep API calls outside visual components when the existing architecture supports it.
* Handle expected HTTP errors explicitly.
* Do not swallow errors silently.
* Do not expose internal server errors directly to users.
* Do not transform API data unnecessarily.

When the backend contract is unclear, identify the uncertainty before implementation.

---

## 11. TypeScript

When TypeScript is used:

* Avoid `any` unless there is a documented reason.
* Do not use unsafe type assertions merely to silence errors.
* Prefer types derived from existing schemas or API contracts.
* Distinguish nullable, optional, and required fields correctly.
* Do not duplicate identical interfaces across unrelated files.

Type errors should be solved, not hidden.

---

## 12. UI Consistency

Follow the existing:

* Spacing
* Typography
* Colors
* Button variants
* Form styles
* Modal behavior
* Responsive breakpoints
* Loading indicators
* Notification patterns

Do not redesign unrelated parts of a page.

New UI should work on supported screen sizes and should not break existing layouts.

---

## 13. Frontend Accessibility

For interactive UI:

* Use semantic HTML where possible.
* Ensure buttons are actual buttons.
* Associate labels with form controls.
* Support keyboard interaction for custom interactive elements.
* Provide meaningful alternative text for informative images.
* Avoid using color as the only indicator of status.

Do not add complex accessibility abstractions when native HTML already solves the problem.

---

## 14. Frontend Performance

Optimize only when there is evidence or a clear need.

* Do not add memoization everywhere.
* Do not use `useMemo` or `useCallback` by default.
* Avoid unnecessary requests and duplicate fetching.
* Avoid rendering very large lists without an appropriate strategy.
* Clean up subscriptions, timers, and event listeners created by the change.

Correctness and readability come before speculative optimization.

---

# Backend Guidelines

## 15. Respect Existing Backend Architecture

Before changing the backend, inspect:

* Modules
* Controllers
* Services
* Repositories
* DTOs
* Validation
* Authentication and authorization
* Database access conventions
* Error response format
* Logging
* Configuration management

Follow the existing architecture unless there is a clear reason not to.

Do not introduce a new architectural layer for a small change.

---

## 16. API Contract

For every endpoint change, define:

* HTTP method
* Route
* Authentication requirement
* Authorization requirement
* Request body, query, and path parameters
* Validation rules
* Success response
* Expected error responses
* Side effects

Do not change an existing response shape silently.

When a breaking change is necessary, identify it clearly.

---

## 17. Validation and Business Rules

Validate data at the backend boundary.

* Validate required fields.
* Validate formats and allowed values.
* Normalize data only when required by the business rule.
* Keep business validation in the appropriate service or domain layer.
* Do not rely solely on database errors for normal validation.
* Do not duplicate the same business rule across controllers.

Controllers should coordinate requests, not contain large amounts of business logic.

---

## 18. Authentication and Authorization

Authentication answers:

> Who is the user?

Authorization answers:

> Is this user allowed to perform this action?

For protected operations:

* Verify authentication.
* Verify ownership, role, or permission.
* Do not trust resource IDs received from the client.
* Prevent users from accessing another user’s resources.
* Apply authorization consistently to read and write operations.

Do not expose sensitive information in error messages or logs.

---

## 19. Database Changes

Before modifying the database:

* Inspect the existing schema and relationships.
* Confirm whether a migration is required.
* Consider existing data.
* Define nullability and defaults deliberately.
* Add indexes only for real query requirements.
* Avoid destructive changes unless explicitly requested.

Database schema changes must use the project’s migration system.

Do not manually modify production data or schema from application startup code.

When a change affects existing rows, explain the migration or backfill behavior.

---

## 20. Transactions and Consistency

Use a database transaction when several writes must succeed or fail together.

Examples:

* Creating an order and its items
* Updating balance and creating a transaction record
* Moving ownership between entities
* Creating a parent record and dependent records

Do not add transactions around a single independent query without a reason.

Ensure retries cannot accidentally create duplicate records when idempotency matters.

---

## 21. Error Handling

Use the project’s existing error format.

* Return appropriate HTTP status codes.
* Distinguish validation, authentication, authorization, not-found, conflict, and server errors.
* Do not catch errors only to ignore them.
* Do not return stack traces to clients.
* Preserve useful context when rethrowing an error.
* Log unexpected errors once at the appropriate boundary.

Do not log passwords, tokens, cookies, payment details, or sensitive personal data.

---

## 22. External Services

For third-party API integrations:

* Confirm the API contract from existing code or documentation.
* Keep credentials in environment variables.
* Set appropriate timeouts.
* Handle expected provider failures.
* Avoid automatic retries for non-idempotent requests unless safely designed.
* Do not mock successful responses in production code.
* Keep provider-specific logic isolated when the existing architecture supports it.

Do not introduce a queue, cache, or background worker unless the feature actually requires one.

---

## 23. Security

For every backend change, consider:

* Input validation
* Authorization
* Injection risks
* File upload restrictions
* Path traversal
* Rate limiting
* Secret exposure
* Sensitive logging
* Mass assignment
* Unsafe redirects
* CORS behavior

Security measures should be proportional to the real risk and consistent with the project.

Do not weaken existing security checks to make a feature pass.

---

## 24. Environment and Configuration

* Do not hardcode secrets, domains, ports, or credentials.
* Reuse the project’s configuration service.
* Update `.env.example` when adding a required environment variable.
* Do not modify real `.env` values unless explicitly requested.
* Validate required configuration during application startup when appropriate.

Do not add environment variables for values that can safely remain constants.

---

# Testing and Verification

## 25. Testing Strategy

Use the smallest relevant test scope.

* Utility change → unit test
* Service business rule → service test
* API behavior → integration or endpoint test
* UI interaction → component test
* Critical user journey → end-to-end test when the project already uses it

Do not introduce an entirely new testing framework for a small task unless requested.

For bug fixes:

1. Reproduce the bug.
2. Add or identify a failing test when practical.
3. Apply the smallest fix.
4. Confirm the test passes.
5. Run related regression checks.

---

## 26. Verification Commands

Before declaring completion, run the relevant available commands, such as:

```bash
npm run lint
npm run typecheck
npm run test
npm run build
```

Use only scripts that exist in the repository.

Do not claim that a check passed unless it was actually run.

If a command cannot be run, state:

* Which command was not run
* Why it could not be run
* What remains unverified

---

## 27. Dependency Changes

Before adding a dependency:

* Check whether the repository already has a suitable solution.
* Explain why native or existing functionality is insufficient.
* Prefer actively maintained and appropriately scoped packages.
* Avoid large dependencies for trivial functionality.

Do not upgrade unrelated dependencies.

Do not regenerate a lockfile unless dependency changes require it.

---

## 28. Documentation

Update documentation only when the change affects:

* Setup
* Environment variables
* Public API behavior
* Deployment
* User-visible workflow
* Important architectural decisions

Do not rewrite unrelated documentation.

Code should remain understandable without excessive comments.

---

## 29. Completion Report

After implementation, report:

```text
Changed:
- What was modified

Verified:
- Commands or tests that were run
- Relevant manual checks

Not verified:
- Anything that could not be confirmed

Notes:
- Important assumptions, tradeoffs, or unrelated issues noticed
```

Keep the report factual.

Do not claim success without verification.

# Project-Specific Instructions

## Stack

- Frontend: React, TypeScript, Vite, Tailwind CSS
- Backend: NestJS, PostgreSQL, Prisma
- Authentication: JWT
- State management: Zustand
- Forms: React Hook Form + Zod
- API client: Axios
- Tests: Vitest and Jest

## Commands

Frontend commands:

```bash
cd frontend
npm run dev
npm run lint
npm run typecheck
npm run test
npm run build
