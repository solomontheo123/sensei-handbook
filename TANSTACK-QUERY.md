# TANSTACK QUERY

> **Managing Server State with Predictable Data Synchronization**
>
> Building modern frontend applications by separating server data management from UI state and creating reliable, scalable data-fetching architecture.

---

# Purpose

This document defines the TanStack Query architecture, principles, and engineering standards used throughout the SENSEI Handbook.

TanStack Query is not simply a data-fetching library.

It is a server-state management solution designed to solve the difficult problems created when frontend applications communicate with external data sources.

This document explains:

- What server state is.
- How it differs from client state.
- Why manual data management becomes difficult.
- How TanStack Query creates predictable data synchronization.
- How it integrates with Next.js, Axios, and application architecture.

---

# What Is TanStack Query?

TanStack Query is a library for managing asynchronous server state in frontend applications.

It handles:

- Fetching data.
- Caching responses.
- Synchronizing data.
- Managing loading states.
- Handling errors.
- Performing mutations.
- Updating stale information.

Previously known as React Query, TanStack Query has evolved into a framework-independent data synchronization solution.

---

# Why TanStack Query Exists

Modern applications constantly communicate with external systems.

Examples:

- User profiles.
- Projects.
- Messages.
- Notifications.
- Products.
- Analytics.

Managing this manually creates problems:

- Duplicate requests.
- Repeated loading logic.
- Stale data.
- Manual cache management.
- Difficult synchronization.

TanStack Query solves these problems by managing the relationship between the frontend and server data.

---

# Client State vs Server State

Understanding this difference is one of the most important frontend architecture concepts.

---

# Client State

Client state exists only inside the application.

Examples:

- Modal visibility.
- Theme selection.
- Form values.
- Sidebar state.
- UI preferences.

Common tools:

- React State.
- Context API.
- Zustand.
- Redux.

Client state represents application behavior.

---

# Server State

Server state comes from external systems.

Examples:

- Database records.
- User information.
- API responses.
- Authentication sessions.

Server state has unique challenges:

- It can become outdated.
- Other users can modify it.
- Requests can fail.
- It requires synchronization.

TanStack Query manages this category.

---

# Core Mental Model

The most important principle:

> **The server is the source of truth.**

The frontend does not permanently own server data.

Instead, it maintains a synchronized representation of server information.

Architecture:

```text
Backend Database

        ↓

API

        ↓

TanStack Query Cache

        ↓

React Components

        ↓

User Interface
```

---

# Core Features

## Queries

Queries retrieve and cache server data.

Example:

```tsx
const { data, isLoading } = useQuery({
    queryKey: ["users"],
    queryFn: getUsers,
});
```

---

## Automatic Caching

TanStack Query stores previous results.

Benefits:

- Faster interfaces.
- Reduced unnecessary requests.
- Better user experience.

---

## Background Refetching

TanStack Query can refresh stale data automatically.

Examples:

- Returning to a page.
- Reconnecting to the internet.
- After mutations.

---

## Mutations

Mutations handle changes to server data.

Examples:

- Creating users.
- Updating profiles.
- Deleting projects.

Example:

```tsx
const mutation = useMutation({
    mutationFn:createProject,
});
```

---

# Query Keys

Query keys identify cached data.

Example:

```tsx
queryKey:["users"]
```

Specific resource:

```tsx
queryKey:["user", userId]
```

Good query keys should be:

- Predictable.
- Unique.
- Consistent.

---

# Query Architecture

Recommended structure:

```text
src/

├── features/

│   └── users/

│       ├── hooks/
│       │   └── useUsers.ts
│       │
│       ├── services/
│       │   └── user.service.ts
│       │
│       └── types/
│           └── user.ts
```

Flow:

```text
Component

↓

Custom Query Hook

↓

Service Function

↓

Axios

↓

Backend API
```

---

# Custom Query Hooks

Avoid placing queries directly inside components.

Prefer:

```tsx
useUsers()
useProjects()
useProfile()
```

Example:

```tsx
export function useUsers(){

    return useQuery({
        queryKey:["users"],
        queryFn:getUsers
    });

}
```

Benefits:

- Reusable logic.
- Cleaner components.
- Easier testing.
- Better separation of concerns.

---

# Query States

Every server request has states:

```text
Loading

↓

Success

↓

Error
```

Every state should have a designed user experience.

Example:

```tsx
if(isLoading){
    return <Loading />;
}

if(error){
    return <Error />;
}

return <Users data={data}/>;
```

---

# Cache Synchronization

After modifying data, the cache must remain accurate.

Example:

```text
Create Project

↓

Backend Updated

↓

Invalidate Query

↓

Fresh Data Loaded
```

This prevents outdated interfaces.

---

# Optimistic Updates

Optimistic updates update the interface before server confirmation.

Example:

```text
User Action

↓

Immediate UI Update

↓

Server Request

↓

Confirm or Rollback
```

Useful for fast interactions.

Use carefully because failed requests require rollback handling.

---

# Integration With Axios

TanStack Query and Axios solve different problems.

Axios handles:

- HTTP communication.
- Request configuration.

TanStack Query handles:

- Server state.
- Caching.
- Synchronization.
- Background updates.

Architecture:

```text
React Component

↓

TanStack Query

↓

Service Layer

↓

Axios

↓

Backend API
```

---

# Integration With Next.js

TanStack Query works alongside Next.js.

Use Server Components for:

- Initial data loading.
- Static content.
- Server-side operations.

Use TanStack Query for:

- Interactive client data.
- Frequently changing information.
- User-driven updates.

They are complementary tools.

---

# Common Mistakes

Avoid:

- Using TanStack Query for UI state.
- Calling APIs directly from components.
- Poor query key design.
- Ignoring cache invalidation.
- Refetching without reason.
- Treating TanStack Query as a backend replacement.

---

# Best Practices

Follow these principles:

- Separate server state from client state.
- Create reusable query hooks.
- Keep API communication in service layers.
- Use meaningful query keys.
- Handle loading and error states.
- Invalidate stale data correctly.
- Optimize only after measurement.

---

# TanStack Query Checklist

Before adding a query:

- Is this server state?
- Is the query key meaningful?
- Is API communication separated?
- Are loading states handled?
- Are errors handled?
- Is cache invalidation considered?
- Is duplication avoided?

---

# Summary

TanStack Query changes how frontend engineers manage server data.

Instead of manually controlling every request, cache, and synchronization process, engineers define a predictable relationship between the application and backend data.

The goal is not to remove responsibility.

The goal is to create a reliable architecture where server state is handled consistently and efficiently.

---

# Related Documents

- README.md
- ARCHITECTURE.md
- TYPESCRIPT.md
- REACT.md
- NEXTJS.md
- AXIOS.md
- BETTER-AUTH.md
- FRONTEND-STANDARDS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | TANSTACK-QUERY.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**TICKETS.md**
