# NEXT.JS

> **Building Production-Ready Applications with Modern React**
>
> A framework for creating scalable, performant, and maintainable full-stack applications using React, TypeScript, and modern web architecture.

---

# Purpose

This document defines the Next.js architecture, concepts, and engineering standards used throughout the SENSEI Handbook.

Next.js is not treated as only a React framework.

It is treated as an application architecture platform that provides solutions for:

- Routing.
- Rendering.
- Data fetching.
- Performance optimization.
- Backend integration.
- Deployment.

The goal is not memorizing features.

The goal is understanding why each feature exists and when it should be used.

---

# What Is Next.js?

Next.js is a React framework designed for production applications.

React provides the UI model.

Next.js provides application structure.

It includes:

- File-based routing.
- Server Components.
- Rendering strategies.
- Data fetching patterns.
- Image optimization.
- Metadata management.
- Deployment support.

---

# Why Next.js Exists

React solves UI creation.

Production applications require more:

- Routing.
- SEO.
- Data handling.
- Authentication integration.
- Performance optimization.
- Server communication.

Next.js provides these capabilities through a consistent architecture.

---

# Next.js Mental Model

The most important concept:

> **Next.js is server-first, with client interaction added only when necessary.**

Think:

- Server by default.
- Client intentionally.
- Data close to where it is needed.
- Performance through architecture.

---

# App Router Architecture

Modern Next.js applications use the App Router.

Example:

```text
app/
│
├── layout.tsx
├── page.tsx
├── loading.tsx
├── error.tsx
└── dashboard/
    └── page.tsx
```

The file structure defines application routes.

---

# Routing

Routes are created through folders.

Example:

```text
app/
│
├── page.tsx
├── about/
│   └── page.tsx
└── dashboard/
    └── page.tsx
```

Creates:

```text
/
/about
/dashboard
```

This makes application navigation predictable.

---

# Server Components

Server Components are the default in modern Next.js.

They run on the server and reduce unnecessary JavaScript sent to the browser.

Benefits:

- Smaller bundles.
- Better performance.
- Direct data access.
- Improved scalability.

Server Components can render Client Components when interaction is required.

Use them whenever browser interaction is unnecessary.

---

# Client Components

Client Components are used for browser-based behavior.

Examples:

- State.
- Events.
- Forms.
- Browser APIs.
- Animations.

They are marked with:

```tsx
"use client";
```

Do not make every component a Client Component.

---

# Server vs Client Decision

Use Server Components for:

- Data fetching.
- Authentication checks.
- Static content.
- Database access.
- SEO pages.

Use Client Components for:

- User interaction.
- Forms.
- Real-time UI.
- Browser APIs.

---

# Data Fetching

Next.js encourages fetching data close to where it is used.

Example:

```tsx
async function UsersPage() {

    const users = await getUsers();

    return (
        <UserList users={users}/>
    );
}
```

Avoid unnecessary client-side fetching when server rendering is appropriate.

---

# Rendering Strategies

## Static Rendering

Generated ahead of time.

Best for:

- Marketing pages.
- Documentation.
- Blogs.

---

## Dynamic Rendering

Generated per request.

Best for:

- Dashboards.
- Personalized pages.
- Private data.

---

## Streaming

Loads parts of the application progressively.

Benefits:

- Faster perceived performance.
- Better user experience.

---

# Loading and Error Handling

Applications should handle failures and waiting states.

Example:

```text
dashboard/

├── page.tsx
├── loading.tsx
└── error.tsx
```

Good applications provide feedback during every state.

---

# Metadata and SEO

Next.js provides built-in metadata management.

Example:

```tsx
export const metadata = {
    title: "Dashboard",
    description: "User dashboard",
};
```

SEO should be considered during development.

---

# Project Architecture

Recommended structure:

```text
src/

├── app/
├── components/
├── features/
├── hooks/
├── lib/
├── services/
├── providers/
├── types/
└── utils/
```

Architecture should remain feature-oriented and scalable.

---

# Authentication Architecture

Authentication should have clear boundaries.

Example:

```text
User
 ↓
Login Form
 ↓
Auth Service
 ↓
Session
 ↓
Protected Routes
```

Authentication logic should not be scattered throughout components.

Related:

- BETTER-AUTH.md
- ARCHITECTURE.md

---

# Performance Principles

Important practices:

- Prefer Server Components.
- Reduce client JavaScript.
- Optimize images.
- Understand caching.
- Split large features.
- Avoid unnecessary dependencies.

Performance starts during architecture.

---

# Common Mistakes

Avoid:

- Making everything client-side.
- Fetching everything in the browser.
- Ignoring caching.
- Mixing backend and frontend responsibilities.
- Ignoring loading states.
- Creating unnecessary complexity.

---

# Best Practices

- Understand rendering behavior.
- Keep Client Components small.
- Use TypeScript strictly.
- Organize by features.
- Design routes intentionally.
- Document architectural decisions.

---

# Next.js Development Checklist

Before completing a feature:

- Is server/client usage intentional?
- Is data fetched correctly?
- Are loading states handled?
- Are errors handled?
- Is authentication secure?
- Is performance considered?
- Is the architecture maintainable?

---

# Summary

Next.js is a tool for expressing good application architecture.

The framework does not automatically create good software.

Good engineering comes from understanding rendering, separating responsibilities, and making intentional architectural decisions.

---

# Related Documents

- README.md
- ARCHITECTURE.md
- DESIGN-SYSTEM.md
- TYPESCRIPT.md
- REACT.md
- BETTER-AUTH.md
- TANSTACK-QUERY.md
- FRONTEND-STANDARDS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | NEXTJS.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**BETTER-AUTH.md**
