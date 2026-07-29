# TYPESCRIPT

> **Building Reliable JavaScript Through Static Typing**
>
> TypeScript extends JavaScript with a powerful type system that helps engineers build scalable, maintainable, and predictable software.

---

# Purpose

This document defines the TypeScript standards used throughout the SENSEI Handbook.

TypeScript is not used simply because it is popular.

It is used because it enables engineers to detect mistakes earlier, document intent through types, improve tooling, and build large applications with greater confidence.

Every frontend project documented in this handbook should use TypeScript as the primary programming language.

---

# What Is TypeScript?

TypeScript is a statically typed superset of JavaScript.

Everything that is valid JavaScript is valid TypeScript.

TypeScript adds features such as:

- Static types
- Interfaces
- Type aliases
- Generics
- Enums
- Utility types
- Type inference
- Better IDE support

TypeScript code is compiled into plain JavaScript before it runs in the browser.

---

# Why TypeScript Matters

JavaScript allows developers to write code quickly.

TypeScript helps developers write code correctly.

Benefits include:

- Earlier error detection.
- Better autocomplete.
- Improved documentation.
- Easier refactoring.
- Safer collaboration.
- More maintainable code.

Large codebases become significantly easier to manage with strong typing.

---

# Core Principles

## Types Document Intent

Types explain what data represents.

Well-written types reduce the need for comments.

---

## Let TypeScript Infer When Possible

Avoid unnecessary annotations.

Good:

```ts
const total = price * quantity;
```

Avoid:

```ts
const total: number = price * quantity;
```

Trust inference unless explicit typing improves readability.

---

## Avoid the `any` Type

`any` disables TypeScript's protection.

Use:

- unknown
- generics
- unions
- interfaces

before considering `any`.

Treat `any` as a last resort.

---

## Prefer Interfaces for Object Contracts

Interfaces define the shape of objects.

```ts
interface User {
  id: string;
  name: string;
  email: string;
}
```

Use interfaces for shared models across an application.

---

## Use Type Aliases for Composition

Type aliases work well for:

- unions
- intersections
- primitive aliases
- mapped types

Example:

```ts
type Status = "idle" | "loading" | "success" | "error";
```

---

# Project Organization

Recommended structure:

```text
types/
│
├── api.ts
├── auth.ts
├── user.ts
├── product.ts
└── index.ts
```

Keep shared types centralized.

Avoid redefining identical types.

---

# Strict Mode

Always enable strict mode.

```json
{
  "strict": true
}
```

Strict mode catches bugs before runtime.

Never disable strict mode to silence errors.

Fix the underlying problem.

---

# Generics

Generics allow reusable, type-safe code.

Example:

```ts
function identity<T>(value: T): T {
  return value;
}
```

Use generics whenever the same logic should work with multiple types.

---

# Utility Types

Frequently used utility types include:

- Partial
- Required
- Pick
- Omit
- Record
- Readonly

These reduce duplication and improve maintainability.

---

# Type Narrowing

Always narrow uncertain values before use.

Example:

```ts
if (typeof value === "string") {
    console.log(value.toUpperCase());
}
```

Never assume a type without verification.

---

# Error Handling

Unknown errors should remain `unknown`.

Example:

```ts
try {
    ...
} catch (error: unknown) {
    ...
}
```

Avoid:

```ts
catch (error: any)
```

Unknown forces safer handling.

---

# Naming Conventions

Use descriptive names.

Examples:

```text
User
UserResponse
AuthSession
LoginCredentials
ApiError
```

Names should communicate meaning immediately.

---

# Common Mistakes

Avoid:

- Using `any`
- Ignoring compiler errors
- Duplicating types
- Overusing enums
- Creating unnecessary type aliases
- Disabling strict mode

---

# Best Practices

- Keep types close to the domain.
- Prefer inference.
- Reuse existing types.
- Make impossible states impossible.
- Treat compiler errors as feedback.

---

# Summary

TypeScript improves software quality by making code more predictable, easier to maintain, and safer to refactor.

The goal is not to satisfy the compiler.

The goal is to communicate intent clearly while preventing entire classes of runtime errors.

---

# Related Documents

- README.md
- FRONTEND-STANDARDS.md
- ARCHITECTURE.md
- REACT.md
- NEXTJS.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | TYPESCRIPT.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**REACT.md**
