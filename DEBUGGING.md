# DEBUGGING

> **A Systematic Approach to Finding and Fixing Software Problems**
>
> Debugging is not guessing. It is the process of understanding systems, collecting evidence, identifying causes, and applying reliable solutions.

---

# Purpose

This document defines the debugging philosophy and workflow used throughout the SENSEI Handbook.

Professional engineers do not debug by randomly changing code until something works.

They use a structured process:

- Observe.
- Investigate.
- Form hypotheses.
- Test assumptions.
- Identify root causes.
- Apply fixes.
- Prevent recurrence.

---

# What Is Debugging?

Debugging is the process of finding and resolving defects in software.

A bug is not only an error message.

A bug can be:

- Incorrect behavior.
- Poor performance.
- Security weakness.
- Unexpected user experience.
- System failure.

---

# Debugging Philosophy

## Understand Before Changing

Never immediately modify code because an error appears.

First understand:

- What failed?
- Where did it fail?
- Why did it fail?
- What changed?

---

## Errors Are Evidence

An error message is information.

Do not treat errors as obstacles.

Treat them as clues.

---

# The Debugging Process

```text
Problem Reported

        ↓

Reproduce Issue

        ↓

Collect Evidence

        ↓

Identify Root Cause

        ↓

Design Solution

        ↓

Implement Fix

        ↓

Verify

        ↓

Document Lesson
```

---

# Step 1: Reproduce The Problem

A bug that cannot be reproduced is difficult to fix.

Record:

- Steps to reproduce.
- Expected behavior.
- Actual behavior.
- Environment details.

Example:

```
Expected:
User should be redirected after login.

Actual:
User remains on login page.

Environment:
Development mode.
Chrome browser.
```

---

# Step 2: Gather Evidence

Collect:

- Error messages.
- Logs.
- Network requests.
- Browser information.
- Recent changes.
- Database state.

Do not rely on assumptions.

---

# Step 3: Locate The Failure

Identify where the problem occurs.

Possible layers:

```text
User Interface

↓

Frontend Logic

↓

API Layer

↓

Backend

↓

Database
```

A frontend error does not always mean the frontend is the cause.

---

# Step 4: Form A Hypothesis

A hypothesis is a possible explanation.

Example:

Problem:

```
Dashboard data is missing.
```

Possible causes:

```
API request failed.
Authentication expired.
Database returned empty data.
Frontend state not updating.
```

Test possibilities one by one.

---

# Common Debugging Areas

## Frontend Debugging

Check:

- Browser console.
- React errors.
- Component state.
- Network requests.
- Rendering behavior.

---

## API Debugging

Check:

- Request URL.
- HTTP method.
- Headers.
- Payload.
- Response status.

Related:

- AXIOS.md

---

## Authentication Debugging

Check:

- Session state.
- Cookies.
- Tokens.
- Permissions.

Related:

- BETTER-AUTH.md

---

## Database Debugging

Check:

- Queries.
- Connections.
- Data integrity.
- Migrations.

---

# Reading Error Messages

Do not only read the last line.

Understand:

- Error type.
- File location.
- Stack trace.
- Context.

The first useful clue is often above the final error message.

---

# Browser DevTools

Essential tools:

## Console

For:

- JavaScript errors.
- Logs.
- Warnings.

---

## Network Tab

For:

- API requests.
- Request payloads.
- Responses.
- Authentication headers.

---

## Application Tab

For:

- Cookies.
- Storage.
- Sessions.

---

# Common Debugging Mistakes

Avoid:

- Random changes.
- Ignoring error messages.
- Debugging without reproduction.
- Fixing symptoms instead of causes.
- Removing code until errors disappear.

---

# Root Cause Analysis

A good fix solves the underlying problem.

Example:

Problem:

```
User gets logged out.
```

Weak fix:

```
Increase timeout everywhere.
```

Better investigation:

```
Session refresh logic was missing.
```

---

# After Fixing A Bug

Always ask:

- Why did this happen?
- Could this happen again?
- Should documentation change?
- Should tests be added?

Every bug is a learning opportunity.

---

# AI-Assisted Debugging

AI can help with:

- Explaining errors.
- Understanding unfamiliar code.
- Suggesting possible causes.
- Reviewing fixes.

Good workflow:

```text
Collect Evidence

↓

Explain Problem Clearly

↓

Ask AI For Analysis

↓

Verify Suggestions

↓

Apply Fix
```

Never blindly copy debugging solutions.

Related:

- AI-WORKFLOW.md

---

# Debugging Checklist

Before fixing:

- [ ] Can the issue be reproduced?
- [ ] Is the error understood?
- [ ] Has evidence been collected?
- [ ] Is the root cause identified?

After fixing:

- [ ] Does the fix work?
- [ ] Are related cases handled?
- [ ] Is documentation updated?
- [ ] Are tests needed?

---

# Summary

Debugging is an engineering skill, not a last resort.

Great engineers are not those who never encounter bugs.

They are engineers who can systematically understand and solve problems.

A disciplined debugging process reduces wasted time and creates more reliable software.

---

# Related Documents

- README.md
- ARCHITECTURE.md
- REVIEW-CHECKLIST.md
- AXIOS.md
- BETTER-AUTH.md
- NEXTJS.md
- AI-WORKFLOW.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | DEBUGGING.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**AI-WORKFLOW.md**
