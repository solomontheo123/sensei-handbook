# ENGINEERING LAWS

> **The Timeless Principles That Govern Every Engineering Decision**
>
> These laws define the standards that guide how software is designed, built, reviewed, deployed, and maintained throughout the SENSEI Handbook.

---

# Purpose

Frameworks change.

Programming languages evolve.

Libraries become obsolete.

Engineering principles endure.

This document defines the fundamental laws that should influence every technical decision, regardless of technology, company, or project.

These are not strict rules that must be followed blindly.

Instead, they are guiding principles developed from industry best practices and practical software engineering experience.

Whenever faced with uncertainty, return to these laws before making a decision.

---

# Why Engineering Laws Exist

Most software problems are not caused by a lack of programming knowledge.

They are caused by poor engineering decisions.

Examples include:

- Writing code before understanding the problem.
- Optimizing too early.
- Ignoring documentation.
- Overengineering simple solutions.
- Copying code without understanding it.
- Prioritizing speed over maintainability.

Engineering laws exist to reduce these mistakes.

They encourage thoughtful decision-making rather than reactive programming.

---

# Law 1 — Solve the Right Problem

> **Never optimize a solution to the wrong problem.**

Before writing a single line of code, understand:

- What problem exists?
- Who experiences the problem?
- Why does it matter?
- What outcome defines success?

Many failed projects result from solving symptoms instead of root causes.

Always define the problem before designing the solution.

---

## Best Practices

- Ask questions before proposing solutions.
- Gather requirements.
- Clarify assumptions.
- Define success criteria.

---

## Anti-Patterns

- Building features because they seem interesting.
- Assuming requirements.
- Copying another application's behavior without understanding why.

---

# Law 2 — Understand Before Implementing

> **If you cannot explain it, you do not understand it well enough to build it.**

Understanding should always precede implementation.

Before using a library, framework, or design pattern, understand:

- Why it exists.
- Which problem it solves.
- Its limitations.
- Available alternatives.

Avoid copying code from tutorials without understanding the underlying concepts.

---

## Best Practices

- Read documentation.
- Experiment with small examples.
- Ask "Why?" repeatedly.
- Explain concepts in your own words.

---

## Anti-Patterns

- Blindly following tutorials.
- Copy-pasting Stack Overflow solutions.
- Depending on AI without verification.

---

# Law 3 — Architecture Before Code

> **Good architecture reduces future complexity.**

Architecture defines the structure of a system before implementation begins.

Good architecture:

- separates responsibilities,
- minimizes coupling,
- encourages reuse,
- supports future growth.

Code should follow architecture.

Architecture should not emerge accidentally.

---

## Best Practices

- Design first.
- Identify responsibilities.
- Define boundaries.
- Document architectural decisions.

---

## Anti-Patterns

- Designing while coding.
- Mixing unrelated concerns.
- Allowing features to dictate structure.

---

# Law 4 — Simplicity Wins

> **Simple software is easier to build, understand, test, and maintain.**

Complexity should only exist when it provides measurable value.

When choosing between two correct solutions, prefer the simpler one.

Simple solutions reduce bugs, onboarding time, and maintenance costs.

---

## Best Practices

- Use descriptive names.
- Remove unnecessary abstractions.
- Prefer readability.
- Keep functions focused.

---

## Anti-Patterns

- Clever code.
- Deep inheritance.
- Premature abstraction.
- Unnecessary design patterns.

---

# Law 5 — Every Piece of Code Has a Cost

Writing code is easy.

Maintaining code is expensive.

Every new function, component, dependency, and abstraction increases long-term maintenance.

Before adding something new, ask:

- Does this simplify the project?
- Will it still be useful next year?
- Can an existing solution solve this?

The best code is often the code that never needed to be written.

---

# Law 6 — Consistency Creates Quality

Consistency reduces cognitive load.

When projects follow predictable conventions, engineers spend less time understanding structure and more time solving problems.

Maintain consistency in:

- Naming
- Folder structure
- Components
- APIs
- Documentation
- Styling
- Commit messages

---

# Law 7 — Documentation Preserves Knowledge

Memory fades.

Documentation scales.

Every significant engineering decision should answer:

- Why was this chosen?
- What alternatives were considered?
- What trade-offs exist?
- When should this change?

Good documentation saves future engineering time.

---

# Law 8 — Optimize Last, Measure First

Premature optimization often wastes engineering effort.

Do not optimize because something "might" be slow.

Measure.

Profile.

Identify bottlenecks.

Then optimize based on evidence.

Performance decisions should be data-driven.

---

# Law 9 — Build for Humans

Software is written for people first.

Computers only execute it.

Prioritize:

- Readability
- Maintainability
- Clear naming
- Logical organization
- Helpful documentation

Future maintainers should understand the project without needing its original author.

---

# Law 10 — Fail Early

Discover problems as soon as possible.

Examples include:

- Type checking.
- Validation.
- Automated testing.
- Linting.
- Code reviews.
- Continuous Integration.

Finding bugs earlier is significantly cheaper than fixing them in production.

---

# Law 11 — Security Is a Design Responsibility

Security is not a final checklist.

It begins during architecture.

Assume:

- User input is untrusted.
- Networks are unreliable.
- Systems fail.
- Attackers exist.

Design accordingly.

---

# Law 12 — Accessibility Is Not Optional

Every user deserves access to software.

Accessibility should be considered throughout development rather than added later.

Accessible software benefits everyone.

---

# Law 13 — Learn Continuously

Technology changes constantly.

Professional engineers remain valuable because they know how to learn.

Invest in:

- Reading documentation.
- Building projects.
- Reviewing code.
- Teaching others.
- Reflecting on mistakes.

Growth is a continuous process.

---

# Law 14 — Review Your Own Work First

Before requesting a code review:

- Read your code.
- Test your feature.
- Remove unnecessary complexity.
- Update documentation.
- Verify naming consistency.

Self-review improves review quality.

---

# Law 15 — Every Project Should Improve the Next

No project is perfect.

After every project, identify:

- What succeeded?
- What failed?
- What should change?
- Which standards should be updated?

Experience becomes wisdom only when reflected upon.

---

# Decision Framework

Whenever making an engineering decision, ask:

1. What problem am I solving?
2. Is this the simplest correct solution?
3. What trade-offs exist?
4. Will this remain maintainable?
5. Is it secure?
6. Is it accessible?
7. Is it documented?
8. Can another engineer understand it?
9. Would I build it this way again?

If you cannot confidently answer these questions, reconsider the implementation.

---

# Engineering Checklist

Before considering work complete:

- Problem clearly understood.
- Architecture defined.
- Solution remains simple.
- Code is maintainable.
- Performance considered.
- Accessibility reviewed.
- Security addressed.
- Documentation updated.
- Tests completed.
- Self-review finished.

---

# Summary

Engineering excellence is not achieved through clever code or the latest framework.

It is achieved through consistently making thoughtful, well-informed decisions.

These engineering laws provide the foundation for every standard, workflow, architecture, and project documented throughout the SENSEI Handbook.

Whenever uncertainty arises, return to these laws.

They are the principles upon which every future engineering decision should be built.

---

# Related Documents

- README.md
- SENSEI.md
- FRONTEND-STANDARDS.md
- ARCHITECTURE.md
- REVIEW-CHECKLIST.md
- DEBUGGING.md

---

# Document Metadata

| Property | Value |
|----------|-------|
| Document | ENGINEERING-LAWS.md |
| Version | v1.0 |
| Status | Production |
| Last Updated | 2026-07-29 |

---

# Next Recommended Reading

**ARCHITECTURE.md**
