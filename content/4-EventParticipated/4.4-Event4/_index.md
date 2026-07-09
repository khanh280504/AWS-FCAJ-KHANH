---
title: "Event 4"
date: 2026-06-06
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# REFLECTION: AWS STUDENT BUILDER GROUP - KIRO SPEC DRIVEN DEVELOPMENT

---

> [!IMPORTANT]
>
> ### 🎯 Event Overview and Goal
>
> The **AWS Student Builder Group - Kiro Spec Driven Development** session introduced a specification-first approach to software development, where requirements, design, and implementation tasks are clarified before code is written. The session focused on **Kiro**, an AI-assisted development environment that helps turn an initial idea into structured requirements, a technical design, and actionable development tasks.

## 1. What are Kiro and Spec Driven Development?

### Event participation information

* **Format:** Online.
* **Participation platform:** Google Meet.
* **Attendance time:** 8:00 PM.

### Kiro

Kiro is an AI-assisted development environment that helps developers transform natural-language ideas into structured engineering artifacts. Instead of asking AI to generate code immediately, Kiro encourages developers to clarify the problem first and then move into implementation.

### Spec Driven Development

Spec Driven Development is a software development approach that treats the **specification** as the center of the workflow. The specification acts as the main source of truth and helps the development team understand:

* What problem the system needs to solve.
* What behavior users expect.
* What acceptance criteria each feature must satisfy.
* What technical design should be followed.
* How implementation work should be broken down.

The key difference in this approach is that code is no longer treated as the only starting point. In many projects, developers begin implementing as soon as they have a rough idea. That may feel fast at the beginning, but when requirements change or more people join the project, the team can easily lose track of why certain technical decisions were made. Spec Driven Development addresses this by turning requirements, design, and implementation plans into artifacts that can be read, revised, and verified.

With AI assistance, specifications also become high-quality context for coding tools. When AI understands the goal, data flow, constraints, user behavior, and completion criteria, its output is less likely to drift. This is especially important in projects with business logic, where one vague requirement can lead to the wrong design or difficult-to-maintain code.

---

## 2. The Problem with "Vibe Coding" and Why Specifications Matter

"Vibe coding" can be understood as building software mainly through free-form prompts: describing an idea briefly, receiving generated code, trying it, and continuing to patch it with more prompts. This can be useful for quick experiments, but it has several limitations:

* Initial requirements often miss edge cases and error scenarios.
* AI may assume an architecture, library, or code organization that does not fit the project.
* Generated code may run, but still fail to match the product goal.
* As the project grows, it becomes difficult to trace why a feature was implemented in a certain way.
* Documentation, tests, and code can drift apart.

From the session, I understood that Kiro does not reject AI-assisted speed. Instead, it helps developers use AI in a more controlled way. Rather than treating AI as a tool that simply writes code, learners should treat it as a technical collaborator that can support requirement analysis, design suggestions, task breakdown, and consistency checks.

---

## 3. Specification-Driven Workflow

### Step 1: Define requirements

At the beginning, an idea is converted into clear requirements. Each requirement should describe the user role, the usage goal, and the acceptance criteria. This reduces vague prompting and prevents AI from making incorrect assumptions.

A good requirement does not simply say "I want a login feature." It should clarify who the user is, which login method is used, how the system responds to an incorrect password, what happens when an account is locked, and what conditions prove the feature is complete. When requirements are clear, both humans and AI share the same reference point.

### Step 2: Design the solution

From the clarified requirements, the system can help generate or refine a technical design. This design may include the overall architecture, process flow, data requirements, interface components, and integration points.

At this step, Kiro helps transform the question "what needs to be built" into "how it should be built." The design can describe main modules, frontend-backend relationships, APIs, data structures, UI states, and security considerations. With design prepared first, coding becomes less fragmented.

### Step 3: Break work into tasks

After the design is established, the work is divided into smaller implementation tasks. Each task has a specific scope, making development, testing, and progress tracking easier to manage.

Breaking work into tasks also helps learners avoid being overwhelmed by a large project. Instead of implementing the whole system at once, the team can move step by step: create data models, write APIs, build the interface, add validation, write tests, and then verify integration.

### Step 4: Implement and verify

Code is written based on the agreed requirements and design. When changes occur, the specification should also be updated so that the documentation and code do not drift apart over time.

Verification is not only about checking whether the application runs. It also means comparing the code against the original requirements, validating acceptance criteria, reviewing error scenarios, and ensuring new changes do not break existing functionality. This habit helps reduce technical debt.

---

## 4. Document Structure in Kiro's Workflow

### Requirements

The requirements document describes users, goals, usage flows, and acceptance criteria. It is the most important artifact because it determines the direction of the entire project. If the requirements are wrong or incomplete, the design and code are likely to drift as well.

### Design

The design document explains the technical solution at a level higher than code. It answers questions such as what components the system has, how data moves through the system, which features depend on each other, and what risks must be considered during implementation.

### Tasks

The tasks document turns the design into an actionable implementation list. A good task should be small enough to complete within a short time, have a clear output, and be verifiable. Looking at the task list, the team should know what to do first and what to do next.

### Connection between the documents

The strength of this workflow is that the three documents are not isolated. Requirements explain "why" and "what"; Design explains "how"; Tasks explain "how to execute step by step." When these parts are aligned, the project becomes easier to understand and AI assistance becomes more effective.

---

## 5. Practical Value of Kiro

### Reducing ambiguity when working with AI

A common issue in AI-assisted programming is that the user gives requirements that are too vague, which leads to inaccurate output. Kiro helps turn requirements into a clearer structure, giving AI better context.

### Supporting product thinking

Spec Driven Development encourages learners to think beyond code. They must consider users, system behavior, possible errors, and completion criteria. This mindset is important when building real products.

### Improving testability

When requirements include clear acceptance criteria, the team can write test cases more easily and evaluate whether a feature is complete. This is especially useful for larger projects or team-based work.

### Reducing risk as projects grow

For small projects, writing code immediately may feel fast. However, as a project grows, missing specifications can make the system difficult to maintain. Kiro's workflow helps preserve technical decisions and break work into manageable pieces.

### Improving team communication

In team projects, different members may understand the same requirement differently. With a clear specification, the team can discuss based on shared documents instead of memory or assumptions. This reduces vague disagreement and improves transparency.

### Supporting learning environments

For students, Kiro helps practice a project workflow that is closer to real engineering environments. Learners do not only submit code; they can also explain requirements, design, implementation plans, and the reasoning behind their choices. This is valuable for coursework, capstone projects, and hackathons.

---

## 6. Example Application in a Student Project

If Kiro is applied to a student event management project, the workflow could look like this:

1. **Requirement:** Students can view event lists, register for events, receive notifications, and check registration status.
2. **Acceptance criteria:** When an event is full, the system prevents new registration; when registration succeeds, the status changes to "Registered"; when a student cancels, the available slot count is updated.
3. **Design:** The system includes an event list UI, event detail page, registration API, and database tables for users and events.
4. **Tasks:** Create data models, build event retrieval APIs, build the registration API, design the interface, add validation, and write tests for full-event and cancellation cases.

This example shows how a vague idea can become a clear implementation plan. AI can support each step, but the developer still needs to review the logic and adjust it according to the real goal.

---

## 7. Risks and Notes When Using Kiro

Kiro and Spec Driven Development offer many benefits, but they do not mean developers can fully depend on the tool. Some important notes include:

* AI-generated specifications still need human review and confirmation.
* If the input requirement is wrong, the generated documents can also be wrong.
* Teams should avoid creating too much formal documentation that is never used during implementation.
* Specifications should be updated when code changes to avoid spec-code drift.
* For small problems, the workflow should stay lightweight and practical.

The key is to use Kiro as a tool that supports engineering thinking, not as a replacement for developer responsibility.

---

## 8. Lessons Learned

1. **AI does not replace a developer's analytical thinking.** To get useful AI support, users still need clear goals, constraints, and requirements.
2. **Good specifications lead to better code.** When requirements, design, and tasks are clear, implementation is less likely to drift from the original goal.
3. **Developers should avoid pure "vibe coding".** Letting AI generate code from vague ideas may be fast at first, but it can create technical debt later.
4. **Documentation is not secondary.** In Spec Driven Development, documentation coordinates the relationship between ideas, design, code, and testing.
5. **Kiro is useful for students learning structured project development.** It helps learners practice problem decomposition, requirement writing, architecture thinking, and result verification.
6. **Documentation and code must stay consistent.** When a feature changes, the specification should be updated so that others can understand the current state of the project.
7. **Problem framing remains essential.** AI can only support effectively when users can describe goals, constraints, and expected outcomes clearly.

---

> [!TIP]
>
> ### 💡 Overall Reflection
>
> Through this session, I realized that AI-assisted software development is shifting from simply "asking AI to write code" toward using AI to support the full engineering workflow. Kiro and Spec Driven Development show that the greatest value of AI is not only code generation speed, but also its ability to clarify requirements, support design decisions, and guide implementation in a systematic way.
