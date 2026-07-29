# NEXT.JS

> **Building Production-Ready Applications with Modern React**
>
> A framework for creating scalable, performant, and maintainable full-stack web applications using React, TypeScript, and modern web development principles.

---

# Purpose

This document defines the Next.js architecture, concepts, patterns, and engineering standards used throughout the SENSEI Handbook.

Next.js is not treated as simply a React framework.

It is treated as an application architecture platform that provides solutions for:

- Routing.
- Rendering.
- Data fetching.
- Performance optimization.
- Backend integration.
- Deployment.
- Production scalability.

The goal is not only to learn Next.js features.

The goal is to understand why each feature exists and when it should be used.

---

# What Is Next.js?

Next.js is a React framework designed for building production-grade web applications.

It extends React by providing built-in solutions for common application requirements.

Next.js provides:

- File-based routing.
- Server-side rendering.
- Static generation.
- Server Components.
- API capabilities.
- Image optimization.
- Metadata management.
- Deployment optimization.

React provides the UI model.

Next.js provides the application structure.

---

# Why Next.js Exists

React solves the problem of building user interfaces.

However, production applications require more than UI components.

Applications also need:

- Routing.
- Data management.
- Performance optimization.
- SEO.
- Authentication integration.
- Server communication.
- Deployment strategies.

Next.js provides these features in a consistent architecture.

---

# Next.js Mental Model

The most important concept:

> **A Next.js application is a server-first application that can include interactive client experiences when needed.**

Modern Next.js encourages engineers to think:

- Server by default.
- Client only when necessary.
- Data close to where it is used.
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

The folder structure represents application routes.

---

# Routing

Routes are created through folders.

Example:

```text
app/
│
├── page.tsx
│
├── about/
│   └── page.tsx
│
└── dashboard/
    └── page.tsx
```

Produces:

```text
/
 /about
 /dashboard
```

Routing becomes predictable because the file system defines the application structure.

---

# Layouts

Layouts define shared UI around routes.

Examples:

- Navigation.
- Sidebars.
- Authentication wrappers.
- Dashboard structures.

Example:

```tsx
export default function DashboardLayout({
    children,
}: {
    children: React.ReactNode
}) {
    return (
        <DashboardShell>
            {children}
        </DashboardShell>
    )
}
```

Layouts prevent repeating common structures.

---

# Server Components

Server Components are the default in modern Next.js.

They run on the server and do not ship unnecessary JavaScript to the browser.

Benefits:

- Better performance.
- Smaller bundles.
- Direct data access.
- Improved scalability.

Use Server Components whenever interaction is not required.

---

# Client Components

Client Components are used when browser interaction is required.

Examples:

- Click events.
- State.
- Browser APIs.
- Interactive forms.

They are marked using:

```tsx
"use client";
```

Use Client Components intentionally.

Do not make everything a Client Component.

---

# Server vs Client Decision

Use Server Components for:

- Data fetching.
- Static content.
- Database access.
- Authentication checks.
- SEO content.

Use Client Components for:

- User interactions.
- Forms.
- Animations.
- Real-time UI.
- Browser APIs.

---

# Data Fetching

Next.js encourages fetching data close to where it is needed.

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

Next.js supports different rendering approaches.

## Static Rendering

Content is generated ahead of time.

Best for:

- Marketing pages.
- Documentation.
- Blogs.

---

## Dynamic Rendering

Content is generated per request.

Best for:

- Personalized dashboards.
- User-specific pages.
- Private data.

---

## Streaming

Allows parts of a page to load progressively.

Benefits:

- Faster perceived performance.
- Better user experience.

---

# Loading States

Every application should handle waiting states.

Example:

```text
dashboard/
│
├── page.tsx
└── loading.tsx
```

Loading states improve user experience.

---

# Error Handling

Next.js provides route-level error handling.

Example:

```text
dashboard/
│
├── page.tsx
└── error.tsx
```

Applications should gracefully handle failures.

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
│
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

Authentication should be handled through clear boundaries.

Example:

```text
User
 ↓
Login Form
 ↓
Auth Service
 ↓
Authentication Provider
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

# API Routes and Server Actions

Next.js supports backend functionality.

Use these carefully.

Good use cases:

- Form submissions.
- Server mutations.
- Secure operations.

Avoid turning Next.js into an unstructured backend.

Maintain clear boundaries.

---

# Performance Principles

Next.js performance depends on architecture.

Important practices:

- Use Server Components.
- Optimize images.
- Reduce client JavaScript.
- Use caching properly.
- Avoid unnecessary dependencies.
- Split large features.

Performance is a design decision.

---

# Common Next.js Mistakes

Avoid:

- Making every component client-side.
- Fetching everything in the browser.
- Ignoring caching behavior.
- Mixing backend and frontend responsibilities.
- Creating unnecessary API layers.
- Ignoring loading and error states.

---

# Best Practices

- Prefer Server Components.
- Keep Client Components small.
- Organize by features.
- Use TypeScript strictly.
- Document architectural decisions.
- Design routes intentionally.
- Understand rendering behavior.

---

# Next.js Development Checklist

Before completing a feature:

- Is the component server or client intentionally?
- Is data fetched from the correct location?
- Are loading states handled?
- Are errors handled?
- Is authentication secure?
- Is performance considered?
- Is the architecture maintainable?

---

# Summary

Next.js provides a powerful foundation for building modern applications.

However, the framework itself does not create good software.

Good software comes from understanding architecture, choosing the right rendering strategy, separating responsibilities, and making thoughtful engineering decisions.

Next.js should be used as a tool to express good architecture—not as a replacement for architectural thinking.

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
