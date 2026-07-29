# TANSTACK QUERY

> **Managing Server State with Predictable Data Synchronization**
>
> Building modern frontend applications by separating server data management from UI state and creating reliable, scalable data-fetching architecture.

---

# Purpose

This document defines the TanStack Query architecture, principles, and engineering standards used throughout the SENSEI Handbook.

TanStack Query is not simply a data-fetching library.

It is a server-state management solution designed to handle the difficult problems that appear when frontend applications communicate with external data sources.

This document explains:

- What server state is.
- Why traditional state management approaches fail.
- How TanStack Query solves these problems.
- How it integrates with Next.js, Axios, and application architecture.
- Best practices for production applications.

---

# What Is TanStack Query?

TanStack Query is a library for managing asynchronous server state in frontend applications.

It handles:

- Fetching data.
- Caching responses.
- Synchronizing data.
- Updating stale information.
- Managing loading states.
- Handling errors.
- Performing mutations.

Previously known as React Query, TanStack Query has evolved into a framework-independent data synchronization solution.

---

# Why TanStack Query Exists

Modern applications constantly communicate with servers.

Examples:

- User profiles.
- Projects.
- Messages.
- Notifications.
- Products.
- Dashboard analytics.

Managing this data manually creates problems:

- Duplicate requests.
- Complex loading states.
- Manual caching.
- Stale data.
- Difficult synchronization.
- Repeated error handling.

TanStack Query solves these problems by managing server state automatically.

---

# Client State vs Server State

One of the most important frontend architecture concepts is understanding the difference between client state and server state.

---

# Client State

Client state exists only inside the application.

Examples:

- Modal visibility.
- Theme selection.
- Form inputs.
- Sidebar state.
- UI preferences.

Tools:

- React state.
- Context API.
- Zustand.
- Redux.

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
- Multiple users can modify it.
- Network requests can fail.
- It must be synchronized.

TanStack Query manages this category.

---

# Core Mental Model

The most important idea:

> **The server is the source of truth.**

The frontend does not permanently own server data.

Instead, it creates a synchronized view of server information.

The relationship:

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

TanStack Query provides:

## Query Management

Fetching and caching server data.

Example:

```tsx
const { data, isLoading } = useQuery({
    queryKey: ["users"],
    queryFn: getUsers,
});
```

---

## Automatic Caching

Previously fetched data can be reused.

Benefits:

- Faster interfaces.
- Reduced network requests.
- Better user experience.

---

## Background Refetching

TanStack Query can automatically refresh stale data.

Examples:

- When a user returns to a page.
- After a period of inactivity.
- After a mutation.

---

## Mutations

Mutations handle data changes.

Examples:

- Creating users.
- Updating profiles.
- Deleting projects.

Example:

```tsx
const mutation = useMutation({
    mutationFn: createProject,
});
```

---

# Query Keys

Query keys identify cached data.

Example:

```tsx
queryKey: ["users"]
```

For specific resources:

```tsx
queryKey: ["user", userId]
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
│
├── features/
│   │
│   └── users/
│       │
│       ├── hooks/
│       │   └── useUsers.ts
│       │
│       ├── services/
│       │   └── user.service.ts
│       │
│       └── types/
│           └── user.ts
```

The flow:

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

Avoid putting queries directly inside components.

Instead:

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

Applications should design for every state.

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

# Mutations and Cache Updates

After changing data, the cache should remain synchronized.

Example:

```text
Create Project

↓

Backend Updated

↓

Invalidate Projects Query

↓

Fresh Data Loaded
```

This prevents outdated interfaces.

---

# Optimistic Updates

Optimistic updates update the UI before the server confirms success.

Example:

User clicks "like":

```text
User Action

↓

UI Updates Immediately

↓

Server Request

↓

Confirm or Rollback
```

Useful for fast interactions.

Use carefully.

---

# Integration With Axios

TanStack Query and Axios have different responsibilities.

Axios:

- Sends HTTP requests.
- Handles communication.

TanStack Query:

- Manages server state.
- Handles caching.
- Synchronizes data.

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

API
```

---

# Integration With Next.js

In modern Next.js applications:

Use Server Components for:

- Initial data loading.
- Static content.
- Server-side operations.

Use TanStack Query for:

- Interactive client data.
- Frequently changing data.
- User-driven updates.

They complement each other.

---

# Common Mistakes

Avoid:

- Using TanStack Query for local UI state.
- Fetching data directly inside components.
- Creating inconsistent query keys.
- Ignoring cache invalidation.
- Refetching unnecessarily.
- Treating it as a replacement for APIs.

---

# Best Practices

Follow these principles:

- Separate server state from client state.
- Create reusable query hooks.
- Keep API calls in service layers.
- Use meaningful query keys.
- Handle loading and error states.
- Invalidate stale data correctly.
- Measure before optimizing.

---

# TanStack Query Checklist

Before adding a query:

- Is this server state?
- Is the query key meaningful?
- Is the API call separated?
- Are loading states handled?
- Are errors handled?
- Is cache invalidation considered?
- Is duplication avoided?

---

# Summary

TanStack Query changes the way frontend engineers think about data.

Instead of manually controlling every request, cache, and synchronization problem, engineers define the relationship between the application and server data.

The goal is not to remove responsibility.

The goal is to create a predictable architecture where server state is handled consistently and efficiently.

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
