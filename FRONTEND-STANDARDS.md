# FRONTEND STANDARDS

> **The Engineering Standards for Building Production Frontend Applications**
>
> A consistent set of principles, conventions, and best practices for designing, developing, reviewing, and maintaining frontend software.

---

# Purpose

This document defines the engineering standards that every frontend project should follow.

Standards exist to reduce inconsistency, improve collaboration, simplify maintenance, and increase software quality.

Every frontend project documented in the SENSEI Handbook should align with these standards unless there is a well-documented reason to do otherwise.

---

# Why Standards Matter

Without standards:

- Projects become inconsistent.
- Components are duplicated.
- Code reviews become subjective.
- Onboarding becomes difficult.
- Technical debt increases.
- Maintenance becomes expensive.

Standards create predictable software.

Predictable software is easier to understand, test, review, and extend.

---

# Engineering Principles

Every frontend application should prioritize:

- Maintainability over shortcuts.
- Readability over cleverness.
- Simplicity over unnecessary abstraction.
- Consistency over personal preference.
- Reusability over duplication.
- Accessibility by default.
- Performance by design.
- Security by default.

These principles should influence every engineering decision.

---

# Project Structure

Projects should use a clear and scalable folder structure.

Organize code by responsibility rather than convenience.

Example:

```text
src/
│
├── app/
├── components/
├── features/
├── hooks/
├── lib/
├── services/
├── providers/
├── types/
├── utils/
├── styles/
└── constants/
```

Avoid deeply nested folders unless they improve organization.

Every folder should have a clear responsibility.

---

# Component Standards

Components should have a single responsibility.

Each component should:

- Be reusable when appropriate.
- Accept well-defined props.
- Avoid unnecessary side effects.
- Be easy to test.
- Be easy to understand.

Avoid creating components that perform unrelated responsibilities.

---

# Naming Conventions

Use descriptive and consistent names.

### Components

```text
UserCard.tsx
LoginForm.tsx
DashboardLayout.tsx
```

### Hooks

```text
useAuth.ts
useTheme.ts
useUsers.ts
```

### Utilities

```text
formatDate.ts
calculateTotal.ts
generateSlug.ts
```

### Types

```text
User.ts
AuthResponse.ts
Invoice.ts
```

Avoid abbreviations unless they are universally understood.

Names should communicate intent.

---

# File Organization

Each file should have one primary responsibility.

Large files should be split into smaller modules when they become difficult to navigate.

As a general guideline:

- Components should focus on UI.
- Hooks should manage reusable logic.
- Services should communicate with external systems.
- Utilities should contain pure helper functions.
- Types should define shared contracts.

---

# State Management

Choose the simplest state management solution that solves the problem.

General guideline:

- Local state for component-specific data.
- Context for shared UI state.
- TanStack Query for server state.
- URL parameters for navigation state.

Avoid storing server data in local component state when a dedicated server-state solution is more appropriate.

---

# API Communication

API communication should be centralized.

Avoid making HTTP requests directly inside components.

Instead:

```text
Component
      ↓
Hook
      ↓
Service
      ↓
API Client
```

Benefits include:

- Easier testing.
- Better reuse.
- Consistent error handling.
- Cleaner components.

---

# Error Handling

Errors should be handled intentionally.

Every application should provide:

- Loading states.
- Empty states.
- Error states.
- Retry mechanisms where appropriate.
- Helpful error messages.

Avoid exposing technical implementation details to users.

---

# Forms

Forms should:

- Validate user input.
- Display helpful validation messages.
- Prevent duplicate submissions.
- Handle loading states.
- Be accessible using keyboard navigation.

Never trust client-side validation alone.

---

# Styling Standards

Styling should prioritize consistency.

General rules:

- Use design tokens where possible.
- Avoid hardcoded values when reusable variables exist.
- Prefer reusable utility classes.
- Keep spacing consistent.
- Follow the established design system.

Visual consistency improves user experience.

---

# Accessibility Standards

Accessibility is a requirement.

Every interface should consider:

- Semantic HTML.
- Keyboard navigation.
- Visible focus states.
- Accessible labels.
- Sufficient color contrast.
- Screen reader compatibility.

Accessibility should be verified throughout development rather than added later.

---

# Performance Standards

Performance should be considered during implementation.

Good practices include:

- Lazy loading when appropriate.
- Optimized images.
- Avoiding unnecessary re-renders.
- Memoizing expensive calculations only when beneficial.
- Reducing unnecessary network requests.

Optimize based on evidence rather than assumptions.

---

# Security Standards

Frontend applications should:

- Validate user input.
- Sanitize displayed content.
- Protect sensitive information.
- Avoid exposing secrets.
- Respect authentication and authorization boundaries.

Security is a shared responsibility between frontend and backend.

---

# Code Review Standards

Before submitting code for review, verify:

- The feature works correctly.
- The code follows project conventions.
- There is no unnecessary duplication.
- The implementation is understandable.
- Edge cases have been considered.
- Documentation has been updated if necessary.

Code reviews should improve quality rather than simply approve changes.

---

# Documentation Standards

Every significant feature should include sufficient documentation.

Document:

- Architectural decisions.
- Non-obvious implementation details.
- Public APIs.
- Shared utilities.
- Reusable components.

Good documentation reduces future confusion.

---

# Git Standards

Every change should:

- Have a meaningful commit message.
- Represent a single logical change.
- Be reviewed before merging.
- Keep the main branch stable.

Avoid mixing unrelated changes into a single commit.

---

# Engineering Checklist

Before considering work complete, ask:

- Does this solve the correct problem?
- Is the implementation understandable?
- Is duplication minimized?
- Is the code reusable where appropriate?
- Is accessibility considered?
- Is performance acceptable?
- Is the feature secure?
- Has documentation been updated?
- Would another engineer understand this without explanation?

If any answer is "No," continue improving the implementation.

---

# Summary

Professional frontend engineering is not defined by the framework being used.

It is defined by consistency, maintainability, and thoughtful decision-making.

These standards establish the minimum quality expected across every frontend project built using the SENSEI Handbook.

Following these standards consistently leads to software that is easier to understand, easier to maintain, and more valuable over time.

---

# Related Documents

- README.md
- SENSEI.md
- CURRICULUM.md
- ARCHITECTURE.md
- DESIGN-SYSTEM.md
- REVIEW-CHECKLIST.md
- ENGINEERING-LAWS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | FRONTEND-STANDARDS.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**ENGINEERING-LAWS.md**
