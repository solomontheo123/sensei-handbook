# AXIOS

> **Reliable Communication Between Frontend Applications and APIs**
>
> Designing predictable, maintainable, and secure HTTP communication layers for modern frontend applications.

---

# Purpose

This document defines the Axios standards, architecture, and usage patterns used throughout the SENSEI Handbook.

Axios is not simply a tool for making API requests.

It is part of the application's communication architecture.

A professional frontend application should have a predictable strategy for:

- Sending requests.
- Handling responses.
- Managing errors.
- Attaching authentication.
- Logging failures.
- Maintaining consistency.

---

# What Is Axios?

Axios is a promise-based HTTP client used for communicating with external services and backend APIs.

It provides a simpler and more powerful interface than the native Fetch API for many production applications.

Axios supports:

- HTTP requests.
- Request configuration.
- Response handling.
- Interceptors.
- Automatic JSON handling.
- Error management.
- Request cancellation.

---

# Why Axios Exists

Frontend applications constantly communicate with external systems.

Examples:

- Authentication servers.
- Backend APIs.
- Payment providers.
- Third-party services.

Without a structured communication layer, applications often develop:

- Duplicate request logic.
- Inconsistent error handling.
- Repeated configuration.
- Difficult debugging.

Axios helps create a centralized API communication system.

---

# HTTP Communication Mental Model

A frontend request follows this flow:

```text
User Action
      |
      ↓
Component
      |
      ↓
Custom Hook
      |
      ↓
Service Layer
      |
      ↓
Axios Client
      |
      ↓
Backend API
      |
      ↓
Response
      |
      ↓
UI Update
```

Components should not directly communicate with APIs.

---

# Core Principle

> **Components should describe user interfaces. Services should handle communication.**

Avoid:

```tsx
function Login() {

    fetch("/api/login");

}
```

Better:

```text
Login Component
        |
        ↓
useLogin Hook
        |
        ↓
authService.login()
        |
        ↓
Axios Client
```

This keeps responsibilities separated.

---

# Axios Architecture

A production application should create a centralized Axios instance.

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
- Request behavior.

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

- One configuration source.
- Easier maintenance.
- Consistent requests.

---

# Request Flow

A typical request:

```text
Component
    |
    ↓
Hook
    |
    ↓
Service Function
    |
    ↓
Axios Instance
    |
    ↓
Backend Endpoint
```

Example:

```ts
export async function getUsers() {
    const response = await api.get("/users");

    return response.data;
}
```

---

# Response Handling

Responses should be handled consistently.

Example:

```ts
const response = await api.get("/profile");

return response.data;
```

Avoid repeating response transformations throughout components.

---

# Error Handling

Errors are expected.

A good application handles:

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

Error handling should provide useful feedback without exposing sensitive details.

---

# Axios Interceptors

Interceptors allow logic to run before requests or responses.

Common uses:

- Adding authentication headers.
- Logging requests.
- Refreshing expired sessions.
- Handling global errors.

Example:

```ts
api.interceptors.request.use(
    (config) => {

        return config;

    }
);
```

---

# Authentication Integration

Authenticated applications often need to attach session information.

Typical flow:

```text
User Login
      |
      ↓
Session Created
      |
      ↓
Request Sent
      |
      ↓
Authentication Included
      |
      ↓
Backend Validates User
```

Authentication logic should remain centralized.

Related:

- BETTER-AUTH.md
- NEXTJS.md

---

# API Service Layer

Do not place API calls throughout the application.

Recommended structure:

```text
services/
│
├── auth.service.ts
├── user.service.ts
├── project.service.ts
└── payment.service.ts
```

Example:

```ts
export const userService = {

    getUsers() {
        return api.get("/users");
    },

    getUser(id: string) {
        return api.get(`/users/${id}`);
    }

};
```

---

# Axios With TanStack Query

Axios and TanStack Query solve different problems.

Axios handles:

- HTTP communication.

TanStack Query handles:

- Server state.
- Caching.
- Synchronization.
- Background updates.

Typical architecture:

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

They work together rather than replacing each other.

---

# Request States

Every API request has states:

```text
Idle

Loading

Success

Error
```

Applications should design for every state.

Users should never experience confusing blank screens.

---

# Data Transformation

API responses should be transformed at appropriate boundaries.

Example:

Backend response:

```json
{
    "first_name": "John"
}
```

Frontend model:

```ts
{
    firstName: "John"
}
```

Do transformations outside UI components.

---

# Security Considerations

Frontend API communication should:

- Never expose secrets.
- Validate user input.
- Handle authentication safely.
- Avoid logging sensitive information.
- Use HTTPS in production.

---

# Common Axios Mistakes

Avoid:

- Creating multiple Axios instances unnecessarily.
- Calling APIs directly inside components.
- Ignoring errors.
- Hardcoding API URLs.
- Duplicating request logic.
- Storing sensitive information incorrectly.

---

# Best Practices

Follow these principles:

- Create one shared Axios client.
- Centralize API communication.
- Separate UI from data fetching.
- Handle errors consistently.
- Use TypeScript types for responses.
- Document important API behavior.

---

# Axios Checklist

Before completing API integration:

- Is communication centralized?
- Are services separated from components?
- Are errors handled?
- Are response types defined?
- Is authentication handled securely?
- Are loading states considered?
- Is unnecessary duplication removed?

---

# Summary

Axios is not just an HTTP library.

It is part of the architecture that connects frontend applications to external systems.

When used correctly, Axios creates predictable communication patterns, cleaner components, easier debugging, and more maintainable applications.

A strong API layer allows frontend engineers to build features faster without sacrificing quality.

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
