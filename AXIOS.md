# AXIOS

> **Reliable Communication Between Frontend Applications and APIs**
>
> Designing predictable, maintainable, and secure HTTP communication layers for modern frontend applications.

---

# Purpose

This document defines the Axios standards, architecture, and usage patterns used throughout the SENSEI Handbook.

Axios is not simply a request library.

It is part of the application's communication layer responsible for:

- Sending requests.
- Handling responses.
- Managing errors.
- Applying consistent configuration.
- Connecting frontend systems with APIs.

---

# What Is Axios?

Axios is a promise-based HTTP client used for communicating with backend APIs and external services.

It provides features such as:

- HTTP requests.
- Request configuration.
- Response handling.
- Interceptors.
- JSON handling.
- Error management.
- Request cancellation.

Axios focuses on communication.

It does not replace state management or application architecture.

---

# Why Axios Exists

Frontend applications communicate with many systems:

- Authentication services.
- Backend APIs.
- Payment providers.
- External platforms.

Without a structured communication layer, applications often develop:

- Duplicate request logic.
- Inconsistent errors.
- Repeated configuration.
- Difficult debugging.

Axios helps create predictable API communication.

---

# HTTP Communication Mental Model

A production request flow:

```text
Component

↓

Custom Hook

↓

Service Layer

↓

Axios Client

↓

Backend API

↓

UI Update
```

Components should not directly communicate with APIs.

---

# Core Principle

> **Components describe interfaces. Services handle communication.**

Avoid:

```tsx
function Login() {

    fetch("/api/login");

}
```

Prefer:

```text
Login Component

↓

useLogin Hook

↓

authService.login()

↓

Axios Client
```

This keeps responsibilities separated.

---

# Axios Architecture

Create a centralized Axios instance.

Example:

```text
lib/

└── axios.ts
```

Responsibilities:

- Base URL configuration.
- Default headers.
- Authentication handling.
- Error processing.
- Request configuration.

---

# Creating an Axios Instance

Example:

```ts
import axios from "axios";

export const api = axios.create({
    baseURL: process.env.NEXT_PUBLIC_API_URL,
    headers: {
        "Content-Type": "application/json",
    },
});
```

Benefits:

- Single configuration source.
- Easier maintenance.
- Consistent requests.

---

# Service Layer

API calls should not be scattered across components.

Recommended:

```text
services/

├── auth.service.ts
├── user.service.ts
├── project.service.ts
└── payment.service.ts
```

Example:

```ts
export async function getUsers() {

    const response = await api.get("/users");

    return response.data;

}
```

The service layer hides communication details from the UI.

---

# Error Handling

Applications should handle:

- Network failures.
- Server errors.
- Authentication failures.
- Validation errors.
- Timeout errors.

Example:

```ts
try {

    await api.get("/users");

} catch (error) {

    console.error(error);

}
```

Errors should provide useful feedback without exposing sensitive information.

---

# Axios Interceptors

Interceptors run logic before requests or responses.

Common uses:

- Adding authentication information.
- Logging requests.
- Handling global errors.
- Refreshing sessions.

Example:

```ts
api.interceptors.request.use(
    (config) => {

        return config;

    }
);
```

Interceptors should remain simple.

---

# Authentication Integration

Axios can help attach authentication information.

Flow:

```text
User Login

↓

Session Created

↓

Request Sent

↓

Backend Validates User
```

Axios transports authentication information.

The backend decides authorization.

Related:

- BETTER-AUTH.md
- NEXTJS.md

---

# Axios and TanStack Query

Axios and TanStack Query solve different problems.

Axios handles:

- HTTP communication.

TanStack Query handles:

- Server state.
- Caching.
- Synchronization.
- Background updates.

Architecture:

```text
Component

↓

TanStack Query Hook

↓

Service Function

↓

Axios

↓

Backend
```

---

# Fetch vs Axios

Both can communicate with APIs.

Use cases depend on project needs.

`fetch()`:

- Built into browsers and Next.js.
- Works well with modern server components.

Axios:

- Provides centralized configuration.
- Provides interceptors.
- Offers consistent request handling.

Choose based on architecture, not preference.

---

# Security Considerations

Frontend communication should:

- Never expose secrets.
- Validate input.
- Use HTTPS in production.
- Avoid logging sensitive data.
- Handle authentication safely.

---

# Common Mistakes

Avoid:

- Creating unnecessary Axios instances.
- Calling APIs directly inside components.
- Hardcoding URLs.
- Ignoring errors.
- Duplicating request logic.
- Mixing UI and communication logic.

---

# Best Practices

- Use a shared Axios client.
- Separate services from components.
- Define response types.
- Handle errors consistently.
- Keep communication logic centralized.
- Document important API behavior.

---

# Axios Checklist

Before completing API integration:

- Is communication centralized?
- Are services separated from UI?
- Are errors handled?
- Are response types defined?
- Is authentication secure?
- Are loading states considered?
- Is duplication removed?

---

# Summary

Axios is not just an HTTP library.

It is a communication boundary between frontend applications and external systems.

When used correctly, Axios creates predictable request patterns, cleaner components, easier debugging, and maintainable applications.

---

# Related Documents

- README.md
- ARCHITECTURE.md
- TYPESCRIPT.md
- REACT.md
- NEXTJS.md
- BETTER-AUTH.md
- TANSTACK-QUERY.md
- FRONTEND-STANDARDS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | AXIOS.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**TANSTACK-QUERY.md**
