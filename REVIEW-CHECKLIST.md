# REVIEW-CHECKLIST

> **Building Better Software Through Systematic Code Reviews**
>
> Code review is not about finding faults in people. It is an engineering process for improving quality, sharing knowledge, and protecting the long-term health of a codebase.

---

# Purpose

This document defines the code review standards used throughout the SENSEI Handbook.

A professional code review evaluates more than whether code works.

It evaluates:

- Architecture.
- Maintainability.
- Security.
- Performance.
- Readability.
- Consistency.
- Long-term impact.

The goal of review is to improve software quality and help engineers grow.

---

# What Is Code Review?

Code review is the process of examining changes before they become part of the main codebase.

A review answers:

> "Is this implementation the best solution for the problem we are solving?"

---

# Why Code Review Matters

Without review, teams accumulate:

- Hidden bugs.
- Inconsistent patterns.
- Technical debt.
- Security issues.
- Poor architecture decisions.

A good review creates a second layer of engineering judgment.

---

# Review Philosophy

## Review The Code, Not The Person

The purpose of review is improvement.

Avoid:

```
This code is bad.
```

Prefer:

```
This approach may create maintenance issues because...
```

Focus on decisions, not individuals.

---

## Understand Before Criticizing

Before suggesting changes:

- Understand the goal.
- Understand the architecture.
- Understand the trade-offs.

A reviewer should not optimize blindly.

---

## Prefer Questions Over Commands

Weak:

```
Change this.
```

Better:

```
Could we extract this logic into a reusable function to avoid duplication?
```

Questions encourage engineering discussion.

---

# Review Process

A typical workflow:

```text
Developer Creates Change

        ↓

Pull Request Created

        ↓

Automated Checks Run

        ↓

Code Review

        ↓

Feedback Applied

        ↓

Approval

        ↓

Merge
```

---

# Before Reviewing

Understand:

- What problem is being solved.
- What the expected behavior is.
- What files changed.
- What architectural decisions were made.

Do not review code without context.

---

# Architecture Review

Ask:

## Does This Belong Here?

Check:

- Is responsibility placed correctly?
- Is business logic separated?
- Are components doing too much?

---

## Is The Design Scalable?

Consider:

- Future requirements.
- Reusability.
- Maintenance cost.
- Complexity.

---

## Are Boundaries Clear?

Good systems separate:

```text
UI

↓

Business Logic

↓

Data Layer

↓

External Services
```

---

# Code Quality Review

Check:

## Readability

Good code should:

- Be easy to understand.
- Use meaningful names.
- Avoid unnecessary complexity.

---

## Simplicity

Ask:

- Is there a simpler solution?
- Is this abstraction necessary?
- Is complexity justified?

---

## Consistency

The implementation should match existing patterns.

Avoid introducing unnecessary new approaches.

---

# TypeScript Review

Check:

- Are types accurate?
- Is `any` avoided?
- Are interfaces reusable?
- Are errors handled correctly?
- Is inference used appropriately?

Related:

- TYPESCRIPT.md

---

# React Review

Check:

- Are components focused?
- Is state managed correctly?
- Are effects necessary?
- Are props clearly defined?
- Is rendering optimized appropriately?

Related:

- REACT.md

---

# Next.js Review

Check:

- Are Server and Client Components used correctly?
- Is data fetching placed properly?
- Are loading and error states handled?
- Is routing structure clear?

Related:

- NEXTJS.md

---

# API Review

Check:

- Is API logic separated?
- Are errors handled?
- Are response types defined?
- Is authentication secure?

Related:

- AXIOS.md
- BETTER-AUTH.md

---

# Security Review

Check:

- Is sensitive data protected?
- Are permissions validated?
- Are inputs validated?
- Are secrets exposed?
- Are authentication boundaries respected?

---

# Performance Review

Consider:

- Unnecessary renders.
- Large dependencies.
- Expensive operations.
- Network requests.
- Bundle size.

Do not optimize without reason.

---

# Testing Review

Check:

- Are important behaviors tested?
- Are edge cases considered?
- Are tests readable?
- Do tests verify real behavior?

---

# Documentation Review

Ask:

- Does this change require documentation?
- Are architectural decisions explained?
- Will future engineers understand this?

---

# Pull Request Checklist

Before approving:

## Functionality

- [ ] Solves the intended problem.
- [ ] Requirements are satisfied.
- [ ] Edge cases are handled.

## Architecture

- [ ] Code belongs in the correct location.
- [ ] Responsibilities are separated.
- [ ] Design matches project standards.

## Quality

- [ ] Code is readable.
- [ ] Naming is clear.
- [ ] Duplication is minimized.

## Security

- [ ] Sensitive data is protected.
- [ ] Validation exists.
- [ ] Permissions are correct.

## Documentation

- [ ] Necessary documentation is updated.
- [ ] Important decisions are recorded.

---

# Common Review Mistakes

Avoid:

- Reviewing only formatting.
- Focusing on personal preferences.
- Suggesting unnecessary rewrites.
- Ignoring architecture.
- Approving without understanding.

---

# AI-Assisted Reviews

AI can assist with:

- Finding possible bugs.
- Explaining unfamiliar code.
- Suggesting improvements.
- Checking consistency.

However:

AI does not replace engineering judgment.

A human must understand the final decision.

Related:

- AI-WORKFLOW.md

---

# Summary

Code review is one of the most important engineering practices.

A strong review protects the codebase, improves knowledge sharing, and helps teams build better systems.

The goal is not perfect code.

The goal is continuous improvement through thoughtful engineering decisions.

---

# Related Documents

- README.md
- FRONTEND-STANDARDS.md
- ARCHITECTURE.md
- TYPESCRIPT.md
- REACT.md
- NEXTJS.md
- DEBUGGING.md
- AI-WORKFLOW.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | REVIEW-CHECKLIST.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**DEBUGGING.md**
