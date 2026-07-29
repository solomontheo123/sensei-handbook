# TICKETS

> **Turning Engineering Work Into Clear, Trackable, and Valuable Units**
>
> A professional ticket system transforms ideas, bugs, and improvements into structured engineering work that can be understood, prioritized, implemented, and reviewed.

---

# Purpose

This document defines the ticket workflow and standards used throughout the SENSEI Handbook.

Tickets are not simply task lists.

A good ticket represents:

- A clear problem.
- A defined goal.
- Expected behavior.
- Technical context.
- Acceptance criteria.
- A path toward completion.

Professional engineering teams use tickets to create alignment between:

- Product decisions.
- Engineering implementation.
- Code reviews.
- Documentation.
- Project history.

---

# What Is an Engineering Ticket?

An engineering ticket is a written description of a piece of work that needs to be completed.

A ticket can represent:

- A new feature.
- A bug fix.
- A technical improvement.
- A refactor.
- Documentation work.
- Infrastructure changes.

A ticket answers:

> "What needs to change, why does it matter, and how will we know it is complete?"

---

# Why Tickets Matter

Without a ticket system, engineering work becomes:

- Difficult to track.
- Easy to misunderstand.
- Hard to prioritize.
- Difficult to review.
- Impossible to measure historically.

Tickets create a shared understanding.

---

# Ticket Philosophy

## A Ticket Is a Contract

A ticket creates an agreement between:

- The person requesting the work.
- The engineer implementing it.
- The reviewer validating it.

Everyone should understand the expected outcome.

---

## Focus on Problems, Not Just Solutions

Weak ticket:

```
Add a button.
```

Better ticket:

```
Users cannot submit profile changes because there is no clear action available.

Add a save action that allows users to submit updated profile information.
```

The second describes the problem.

---

## Small, Focused Work

A ticket should represent a manageable unit of work.

Avoid:

```
Build the entire dashboard.
```

Prefer:

```
Create dashboard layout structure.
Implement dashboard navigation.
Add user analytics widget.
Connect dashboard data API.
```

Small tickets improve:

- Estimation.
- Review quality.
- Debugging.
- Delivery speed.

---

# Ticket Structure

Every professional ticket should contain:

```text
Title

Description

Problem

Goal

Technical Context

Requirements

Acceptance Criteria

Implementation Notes

Testing Requirements

Related Documents
```

---

# Title

A good title is:

- Specific.
- Short.
- Action-oriented.

Examples:

Good:

```
Add authentication loading state
```

Bad:

```
Fix login
```

The title should immediately communicate the work.

---

# Description

The description explains the context.

Example:

```
Users currently see a blank screen while authentication status is loading.

The application needs a loading state to communicate that authentication is being checked.
```

---

# Problem Statement

Explain why the work exists.

Questions:

- What problem exists?
- Who experiences it?
- Why does it matter?

Example:

```
Users are confused because there is no feedback during login verification.
```

---

# Goal

Define the desired outcome.

Example:

```
Provide a clear loading experience during authentication checks.
```

---

# Requirements

Requirements describe what must exist after completion.

Example:

```
The authentication flow should:

- Display loading state.
- Prevent duplicate submissions.
- Handle errors.
- Maintain accessibility.
```

---

# Acceptance Criteria

Acceptance criteria define completion.

A ticket is complete when all criteria are satisfied.

Example:

```
Given a user submits login credentials:

✓ Loading indicator appears.
✓ Submit button becomes disabled.
✓ Successful login redirects user.
✓ Failed login displays an error message.
```

---

# Technical Context

Include information engineers need.

Examples:

- Existing architecture.
- Related files.
- APIs.
- Dependencies.
- Design decisions.

Example:

```
Authentication uses:

- Next.js App Router.
- Better Auth.
- Axios API layer.
- TanStack Query mutations.
```

---

# Ticket Types

## Feature Tickets

Used for new functionality.

Example:

```
Create user profile settings page.
```

---

## Bug Tickets

Used for fixing incorrect behavior.

Example:

```
Fix dashboard data not refreshing after update.
```

---

## Refactoring Tickets

Used for improving existing code.

Example:

```
Extract authentication logic into reusable hooks.
```

---

## Documentation Tickets

Used for knowledge preservation.

Example:

```
Document API authentication flow.
```

---

## Technical Debt Tickets

Used for improving system health.

Example:

```
Upgrade outdated dependencies.
```

---

# Ticket Workflow

A professional workflow:

```text
Backlog

↓

Ready

↓

In Progress

↓

Review

↓

Testing

↓

Completed
```

---

# Before Starting a Ticket

An engineer should understand:

- Why this work exists.
- What problem it solves.
- Existing architecture.
- Dependencies.
- Expected outcome.

Never start coding from an unclear ticket.

---

# During Implementation

The engineer should:

- Follow architecture standards.
- Keep changes focused.
- Update documentation if needed.
- Write tests when appropriate.
- Avoid unrelated changes.

---

# During Review

The reviewer checks:

- Does it solve the intended problem?
- Is the implementation maintainable?
- Does it follow project standards?
- Are edge cases handled?
- Is documentation updated?

Related:

- REVIEW-CHECKLIST.md

---

# AI and Tickets

AI can help create:

- Ticket descriptions.
- Acceptance criteria.
- Technical breakdowns.
- Implementation plans.

However:

AI should not decide product requirements without human understanding.

The engineer remains responsible for the final decision.

Related:

- AI-WORKFLOW.md

---

# Common Ticket Mistakes

Avoid:

- Writing vague tickets.
- Combining unrelated work.
- Missing acceptance criteria.
- Describing only implementation.
- Ignoring technical context.
- Creating massive tickets.

---

# Professional Ticket Example

```text
Title:

Add user profile update flow


Problem:

Users cannot update their personal information after account creation.


Goal:

Allow authenticated users to modify profile information.


Requirements:

- Create profile form.
- Validate input.
- Submit changes.
- Display success and error states.


Acceptance Criteria:

✓ User can update profile.
✓ Invalid input is rejected.
✓ Changes persist after refresh.
```

---

# Ticket Checklist

Before creating a ticket:

- Is the problem clear?
- Is the goal defined?
- Is the scope reasonable?
- Are acceptance criteria included?
- Are related documents referenced?

Before completing a ticket:

- Does the implementation solve the problem?
- Has it been reviewed?
- Has it been tested?
- Has documentation been updated?

---

# Summary

A ticket is more than a task description.

It is a communication tool that connects ideas, engineering decisions, implementation, and review.

Strong tickets create strong engineering teams because they reduce confusion and improve decision-making.

The quality of engineering work often begins with the quality of the ticket.

---

# Related Documents

- README.md
- FRONTEND-STANDARDS.md
- ARCHITECTURE.md
- REVIEW-CHECKLIST.md
- DEBUGGING.md
- AI-WORKFLOW.md
- TM-MANAGEMENT.md
- GP-AUTOS.md
- OCTOHUB.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | TICKETS.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**REVIEW-CHECKLIST.md**
