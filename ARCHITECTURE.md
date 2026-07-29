# ARCHITECTURE

> **Designing Software Before Building It**
>
> A guide to thinking in systems, defining responsibilities, and creating maintainable software architectures.

---

# Purpose

This document defines the architectural principles used throughout the SENSEI Handbook.

Architecture is not about choosing frameworks or libraries.

It is about organizing software so that it remains understandable, maintainable, scalable, and adaptable throughout its lifetime.

Every production application documented in this handbook should begin with architectural planning before implementation.

---

# What Is Software Architecture?

Software architecture is the high-level design of a software system.

It defines:

- The major parts of the application.
- The responsibilities of each part.
- How those parts communicate.
- The rules that govern the system.

Think of architecture as the blueprint of a building.

Just as builders rely on blueprints before construction begins, engineers rely on architecture before implementation begins.

---

# Why Architecture Matters

Good architecture provides:

- Clear responsibilities.
- Easier maintenance.
- Better scalability.
- Reduced technical debt.
- Simpler onboarding.
- More predictable development.

Poor architecture often leads to:

- Tight coupling.
- Repeated logic.
- Difficult debugging.
- Confusing folder structures.
- Expensive refactoring.

Architecture determines how easily software can evolve.

---

# Core Architectural Principles

Every project should follow these principles.

## Separation of Concerns

Each part of the application should have a single responsibility.

For example:

- UI displays information.
- Services communicate with APIs.
- Hooks manage reusable logic.
- Utilities perform pure computations.

Avoid mixing unrelated responsibilities within the same file or component.

---

## Single Responsibility

Every module should have one primary reason to change.

Examples:

- A button component should render a button.
- An API client should make HTTP requests.
- A utility should perform one reusable task.

Components that perform multiple unrelated tasks become difficult to maintain.

---

## High Cohesion

Related functionality should stay together.

For example:

```text
features/
└── authentication/
    ├── components/
    ├── hooks/
    ├── services/
    ├── types/
    └── utils/
```

Grouping related code improves discoverability and maintenance.

---

## Loose Coupling

Different parts of the application should depend on abstractions rather than implementation details.

Changing one module should require minimal changes elsewhere.

Loose coupling increases flexibility.

---

## Composition Over Inheritance

Build applications by combining small, focused components.

React naturally encourages composition.

Prefer:

```text
Dashboard
├── Sidebar
├── Header
├── Statistics
└── ActivityFeed
```

Rather than creating deeply nested inheritance hierarchies.

Composition creates reusable systems.

---

# Thinking Before Coding

Before writing production code, answer these questions:

1. What problem are we solving?
2. Who uses this feature?
3. What data is required?
4. Where does the data come from?
5. Which components are responsible?
6. What happens if something fails?
7. How will this feature grow?

If these questions cannot be answered, more design work is needed.

---

# Layers of a Frontend Application

A production frontend should separate responsibilities into logical layers.

```text
User Interface
        │
        ▼
Components
        │
        ▼
Hooks
        │
        ▼
Services
        │
        ▼
API Client
        │
        ▼
Backend
```

Each layer has a single responsibility.

---

## Presentation Layer

Responsible for:

- Rendering UI.
- Displaying data.
- Handling user interaction.

Should avoid business logic whenever possible.

---

## Business Logic Layer

Responsible for:

- Data transformation.
- Validation.
- Reusable logic.
- Application rules.

Business logic should be reusable and independent of the UI.

---

## Data Layer

Responsible for:

- API communication.
- Caching.
- Authentication requests.
- External services.

Components should not communicate directly with external APIs.

---

# Feature-Based Architecture

Organize applications around features rather than file types whenever practical.

Example:

```text
features/
│
├── auth/
├── dashboard/
├── users/
├── notifications/
└── settings/
```

Each feature contains everything required for that feature.

Benefits include:

- Better organization.
- Easier scaling.
- Improved ownership.
- Reduced coupling.

---

# Folder Structure

Recommended structure:

```text
src/
│
├── app/
├── components/
├── features/
├── hooks/
├── lib/
├── providers/
├── services/
├── styles/
├── types/
├── utils/
└── constants/
```

Every folder should have a clearly defined responsibility.

Avoid placing unrelated files together.

---

# Data Flow

Data should move predictably through the application.

Typical flow:

```text
User Action
      │
      ▼
Component
      │
      ▼
Custom Hook
      │
      ▼
Service
      │
      ▼
API Client
      │
      ▼
Backend
```

The response follows the same path back to the user interface.

Predictable data flow simplifies debugging.

---

# State Management Strategy

Not all state belongs in the same place.

Use the appropriate tool for the appropriate type of state.

| State Type | Recommended Location |
|------------|----------------------|
| Local UI State | React State |
| Shared UI State | Context |
| Server State | TanStack Query |
| URL State | Router |
| Form State | Form Library |

Avoid storing server state in component state.

---

# Error Handling Strategy

Every application should anticipate failure.

Plan for:

- Network errors.
- Validation failures.
- Authentication failures.
- Missing data.
- Loading delays.

Every feature should define:

- Loading state.
- Success state.
- Empty state.
- Error state.

Reliable software plans for failure.

---

# Scalability

Good architecture makes growth easier.

Design applications so they can support:

- More users.
- More developers.
- More features.
- Larger datasets.
- Additional services.

Scalable architecture minimizes future restructuring.

---

# Maintainability

Maintainable software is software that engineers enjoy working on.

Improve maintainability by:

- Keeping files focused.
- Writing clear documentation.
- Following conventions.
- Removing duplication.
- Refactoring regularly.

Every engineering decision should reduce future maintenance effort.

---

# Common Architectural Mistakes

Avoid these patterns:

- Business logic inside UI components.
- Large "God Components."
- Circular dependencies.
- Duplicate API calls.
- Deeply nested folders.
- Excessive abstraction.
- Tight coupling between features.

Recognizing these early prevents long-term technical debt.

---

# Architecture Review Checklist

Before implementing a new feature, verify:

- The problem is clearly defined.
- Responsibilities are separated.
- Data flow is predictable.
- Components remain focused.
- APIs are centralized.
- State management is appropriate.
- Error handling is planned.
- The design supports future growth.

Architecture should be reviewed before code is written.

---

# Summary

Architecture is the foundation of every successful software system.

Good architecture reduces complexity, improves collaboration, and enables software to evolve without constant redesign.

Throughout the SENSEI Handbook, architecture is treated as the first engineering activity—not the last.

Every project should begin by designing the system before implementing the solution.

---

# Related Documents

- README.md
- SENSEI.md
- FRONTEND-STANDARDS.md
- DESIGN-SYSTEM.md
- REACT.md
- NEXTJS.md
- ENGINEERING-LAWS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | ARCHITECTURE.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**DESIGN-SYSTEM.md**
