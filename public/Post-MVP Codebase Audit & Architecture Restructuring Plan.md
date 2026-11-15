Mission : Post-MVP Codebase Audit & Architecture Restructuring Plan
1. Role & Mission

Act as a Senior Software Architect / Staff Engineer with strong experience in software architecture, maintainability, developer experience, technical debt management, and long-term project evolution.

Your mission is to perform a comprehensive audit of the current repository and produce a concrete, actionable plan to prepare the project for its next stage of growth.

The project is transitioning from its MVP phase to a more mature product. Its current implementation may contain temporary decisions, shortcuts, inconsistencies, or architectural limitations that were acceptable during early development but may become problematic as the project grows.

We want to establish solid foundations for a codebase that is:

Easy to understand, navigate, and use.
Easy to maintain, test, debug, and extend.
Well structured, with clear responsibilities and boundaries.
Consistent in its coding practices and conventions.
Appropriately documented.
Friendly to both human developers and AI coding agents.
Capable of evolving without requiring increasingly complex modifications.
Scalable in terms of code organization, architecture, and development workflow.

Your task is to understand the existing project and design its ideal next-stage organization.

This is an assessment and planning task only.

You must NOT modify, create, move, rename, or delete any project files. Do not implement your recommendations.

The final result must be a detailed restructuring and improvement blueprint that another developer or AI agent can use to execute the work progressively.

2. Fundamental Principles

All your analysis and recommendations must follow these principles.

2.1. Pragmatism over architectural perfection

Do not introduce complexity simply because a design pattern, architecture, or best practice exists.

Avoid:

Unnecessary abstraction layers.
Premature modularization.
Excessive interfaces and factories.
Over-engineered dependency injection.
Unnecessary design patterns.
Excessive documentation.
Splitting files without a clear benefit.
Introducing technologies or dependencies without a justified need.

Every architectural decision must solve an identifiable problem or prepare the project for a reasonably foreseeable evolution.

Do not assume that a large number of files means better architecture.

2.2. Design for evolution

The architecture must facilitate future changes.

Consider:

New features and modules.
Changes to existing business logic.
Additional integrations and external services.
Changes in data models.
Increasing application complexity.
Increasing development team size.
Automated testing.
Future technical migrations.

Prefer clear responsibilities, high cohesion, low coupling, explicit boundaries, and predictable dependency directions.

2.3. Documentation must remain useful

Documentation is important, but documentation volume is not a quality metric.

Developers and AI agents rarely read hundreds of pages before working on a task.

Therefore:

Prioritize information that is difficult to infer from the code.
Document architectural decisions and non-obvious conventions.
Avoid duplicating information already clearly expressed in the code.
Avoid documenting implementation details that will quickly become outdated.
Prefer concise, structured, navigable documentation.
Keep documentation close to the code when appropriate.
Identify documentation that should be created later rather than immediately.

The goal is to create a small but valuable documentation foundation.

2.4. Evidence-based recommendations

Never recommend a restructuring based solely on assumptions.

For every significant finding:

Identify the relevant files and directories.
Explain the current situation.
Explain the actual or potential problem.
Explain why the proposed change is beneficial.
Identify the expected impact.
Distinguish verified facts from hypotheses.

When information is unavailable, explicitly state it.

Never invent features, requirements, architecture, or roadmap items.

3. Phase 1 — Understand the Project

Before proposing anything, thoroughly investigate the repository.

Do not start by imposing a standard architecture.

First understand what already exists.

3.1. Project overview

Identify:

The project's purpose.
Its main responsibilities.
Its functional scope.
Its main technologies and frameworks.
Its runtime environments.
Its external dependencies and integrations.
Its entry points.
Its main execution flows.
Its deployment and build mechanisms, when identifiable.

Determine whether it is a monolith, modular monolith, multi-package repository, distributed system, or another architecture.

3.2. Repository mapping

Inspect the complete repository structure.

Identify:

Main source directories.
Configuration files.
Application entry points.
Business logic.
Domain models.
API and communication layers.
Data access and persistence.
Shared utilities.
Components and services.
Tests and test utilities.
Scripts and tooling.
Build and deployment configuration.
Existing documentation.
CI/CD configuration.

Pay particular attention to:

Directories with unclear responsibilities.
Files containing unrelated responsibilities.
Duplicated functionality.
Circular dependencies.
Inconsistent naming.
Unclear ownership of shared code.
Files that have become too large or complex.
Unexpected dependencies between modules.

Do not simply list files. Explain the purpose and relationships of the important parts of the project.

3.3. Architecture and execution flows

Reconstruct the current architecture.

Identify the major modules and how they communicate.

Trace representative execution flows from their entry points to their final outcomes.

For example:

An important user action.
A typical API request.
A background process.
A data persistence operation.
An external service integration.

Determine where responsibilities actually live and whether the implementation follows the apparent architecture.

Identify coupling, duplicated responsibilities, unclear boundaries, and potential architectural bottlenecks.

3.4. Existing documentation

Inventory all existing documentation.

For each document, assess:

Its purpose.
Its audience.
Its relevance.
Its accuracy compared with the current implementation.
Whether it duplicates another document.
Whether it is too detailed, incomplete, or outdated.
Whether it should be retained, rewritten, merged, moved, or removed.

Pay particular attention to README files, technical documentation, architecture documents, development guides, and roadmap files.

Do not assume existing documentation is accurate.

When possible, verify its statements against the actual code.

3.5. Existing development practices

Investigate the current development workflow.

Identify:

Formatting conventions.
Linting.
Static analysis.
Type checking.
Testing frameworks and coverage.
Naming conventions.
Error handling.
Logging.
Environment configuration.
Dependency management.
Git conventions.
CI/CD checks.
Release and versioning practices.

Determine which practices are already established, which are partially implemented, and which are missing.

4. Phase 2 — Understand the Product and Its Future

A good architecture must support the actual product, not an imaginary generic application.

Investigate all available information about the product's future.

Look for:

Roadmaps.
TODOs and FIXMEs.
Issues and feature descriptions.
Existing technical documentation.
Product specifications.
Planned integrations.
Incomplete features.
Existing extension points.
Comments indicating temporary implementation decisions.

Identify the likely future evolution of the application.

Build a distinction between:

Confirmed existing capabilities.
Explicitly documented future requirements.
Reasonable architectural assumptions.
Unknowns requiring clarification.

Determine whether the current architecture can support these evolutions.

Identify areas where future development could become unnecessarily difficult.

Important: Do not build architecture around speculative features. However, do not ignore clearly documented future requirements.

If the roadmap is incomplete, identify the missing information instead of inventing it.

5. Phase 3 — Identify Technical Debt and Structural Problems

Perform a critical review of the codebase.

Assess the following areas.

5.1. Architecture and organization

Look for:

Unclear module boundaries.
Poor separation of concerns.
Excessive coupling.
Circular dependencies.
Inconsistent architectural patterns.
Business logic in inappropriate layers.
Overloaded shared modules.
Unnecessary abstractions.
Inconsistent folder organization.
5.2. Code quality and maintainability

Look for:

Large or complex files.
Functions with too many responsibilities.
Duplicated code.
Poor naming.
Hidden side effects.
Difficult-to-test code.
Unnecessary complexity.
Inconsistent error handling.
Fragile implementations.
Unclear contracts between components.

Identify opportunities to improve code readability and maintainability without introducing unnecessary abstraction.

5.3. Documentation and developer experience

Look for:

Missing project onboarding instructions.
Unclear setup procedures.
Missing development commands.
Missing architectural explanations.
Inconsistent documentation.
Unclear environment configuration.
Lack of contribution guidelines.
Missing conventions for human developers and AI agents.
5.4. Typing and code contracts

Evaluate whether the project uses its language's typing capabilities appropriately.

Consider:

Explicit types and interfaces.
Type safety.
Domain-specific types.
Reusable type definitions.
API contracts.
Runtime validation when appropriate.
Avoidance of unnecessary any or equivalent escape hatches.
5.5. JSDoc and code-level documentation

If the project uses JavaScript or TypeScript, assess whether JSDoc is appropriate.

Determine:

Which functions genuinely need documentation.
Which public APIs should be documented.
Which complex business rules require explanations.
Whether types already provide sufficient information.
Whether JSDoc would improve IDE assistance and AI agent understanding.

Do not recommend adding JSDoc to every function.

Prioritize public interfaces, complex logic, non-obvious behavior, reusable utilities, and important contracts.

If another language is used, apply its equivalent documentation practices.

5.6. Testing and reliability

Evaluate:

Existing test organization.
Unit tests.
Integration tests.
End-to-end tests.
Testability of business logic.
Critical areas without sufficient coverage.
Missing regression protection.
Test naming and organization.
Test execution workflow.

Recommend a testing strategy proportional to the project's complexity and risks.

5.7. Dependencies and configuration

Identify:

Unused or redundant dependencies.
Potentially outdated dependencies.
Duplicated configuration.
Inconsistent environment handling.
Hardcoded configuration values.
Missing environment variable validation.
Configuration that should be centralized or separated.

Do not recommend dependency replacements without a concrete reason.

6. Phase 4 — Define the Target Architecture

This is one of the most important parts of the mission.

Based on your investigation, define the recommended target organization for the project.

Do not blindly adopt Clean Architecture, Hexagonal Architecture, DDD, MVC, or any other architectural methodology.

You may use elements of these approaches when they solve actual problems.

Explain:

The proposed architectural style.
Why it is appropriate.
The main architectural boundaries.
The responsibilities of each module.
How dependencies should flow.
Where shared functionality belongs.
How new features should be introduced.
How external integrations should be organized.
How testing should be structured.

The architecture must be understandable without requiring developers to learn an unnecessarily complex methodology.

6.1. Target folder structure

Provide a complete proposed folder and file tree.

Include:

Existing files that should remain.
Existing files that should move.
Files that should be split.
Files that should be merged.
Files that should be renamed.
Files that should be deleted.
New directories.
New files.

For every significant change, explain its purpose.

Do not limit the proposal to the current folder structure. You may redesign it entirely when justified.

However, preserve existing conventions when they are already effective.

6.2. File-level restructuring

Provide a detailed file-level action plan.

For each important operation, specify:

Current path.
Proposed path.
Action: KEEP, MOVE, RENAME, SPLIT, MERGE, DELETE, or CREATE.
Reason.
Responsibilities before and after the change.
Dependencies or references that need updating.
Potential risks.

When splitting a file, propose the responsibilities of each resulting file.

When merging files, explain why their responsibilities belong together.

When creating a new module, explain what it owns and what it must not own.

Be concrete. Avoid recommendations such as "improve the service layer" without identifying the actual files and changes involved.

7. Phase 5 — Define Development Standards

Propose a coherent set of development conventions adapted to the actual stack.

Cover the following subjects when relevant.

7.1. Code conventions
Naming conventions.
File naming.
Folder naming.
Import organization.
Export conventions.
Function and class responsibilities.
Code formatting.
Error handling.
Logging.
Comments and JSDoc.
7.2. Architecture conventions
Module boundaries.
Dependency direction.
Shared code ownership.
Business logic placement.
External integration organization.
Configuration management.
Reusable component and utility rules.
7.3. Testing conventions
Test file organization.
Naming.
Unit vs integration tests.
Mocking strategy.
Critical coverage expectations.
Regression testing.
7.4. Git and collaboration
Branch naming.
Commit conventions.
Pull request expectations.
Code review practices.
Definition of done.

Only recommend practices that provide meaningful value to this project.

Separate essential rules from optional improvements.

8. Phase 6 — Define a Documentation Strategy

Propose a minimal, high-value documentation structure.

The goal is to give developers and AI agents enough context to work effectively without overwhelming them.

Consider the following documents, but do not automatically create all of them.

Potential documentation

README.md

Project purpose.
Main capabilities.
Quick start.
Prerequisites.
Essential commands.
Links to important documentation.

docs/ARCHITECTURE.md

Architectural overview.
Main modules.
Responsibilities.
Important dependencies.
Main execution flows.
Architectural constraints.

docs/DEVELOPMENT.md

Development environment.
Installation.
Configuration.
Running locally.
Testing.
Linting and validation.

docs/CONVENTIONS.md

Important development rules.
Naming conventions.
Code organization.
Testing expectations.
Documentation standards.

docs/ROADMAP.md

Only if a reliable and maintained roadmap is appropriate for the project.

docs/decisions/

Architecture Decision Records (ADRs), only for decisions with meaningful long-term consequences.

.github/copilot-instructions.md

Concise project context.
Architecture constraints.
Important conventions.
Essential commands.
Instructions for AI coding agents.

You may recommend a different structure if it better fits the project.

Documentation evaluation

For each proposed document, explain:

Whether it is necessary now.
Its purpose.
Its intended audience.
Its expected content.
What should explicitly NOT be included.
Whether it duplicates existing information.

Prioritize information that cannot easily be inferred from source code.

Do not create documentation simply to fill a folder.

Also identify documentation that should be postponed to a later iteration.

9. Phase 7 — Tooling and Quality Gates

Evaluate which tools and automated checks should be introduced or improved.

Consider, where appropriate:

Formatter.
Linter.
Type checker.
Unit testing.
Integration testing.
Dependency auditing.
Security scanning.
Pre-commit hooks.
CI pipelines.
Build validation.
Automated documentation checks.

For every proposed tool or configuration:

Explain the problem it solves.
Explain why it is appropriate for the current stack.
Identify the configuration file to create or modify.
Explain whether it is essential or optional.

Avoid introducing multiple tools that solve the same problem.

The goal is to establish reliable quality gates without slowing down development unnecessarily.

10. Phase 8 — Prioritized Restructuring Roadmap

Translate all your findings into an actionable implementation roadmap.

The plan must be comprehensive. Do not artificially limit the number of improvements.

However, organize them into logical phases to make execution manageable.

Use the following suggested structure, adapting it to the project.

Phase 0 — Critical foundations

Changes that are necessary to prevent future restructuring difficulties.

Examples:

Resolve major architectural inconsistencies.
Clarify module responsibilities.
Establish essential conventions.
Address critical configuration issues.
Phase 1 — Structural cleanup

Changes to improve organization and maintainability.

Examples:

Move files.
Split overloaded modules.
Consolidate duplicated responsibilities.
Establish clearer boundaries.
Normalize naming and organization.
Phase 2 — Development standards and quality

Examples:

Linting and formatting.
Typing improvements.
Testing structure.
Error handling conventions.
JSDoc where justified.
CI quality gates.
Phase 3 — Documentation and developer experience

Examples:

README improvements.
Architecture documentation.
Development guide.
AI agent instructions.
Contribution guidelines.
Phase 4 — Long-term improvements

Examples:

Advanced testing.
Architectural improvements for anticipated features.
Performance and scalability considerations.
Additional automation.
Further modularization when justified.

These phases are suggestions, not mandatory categories. Adapt them to the actual project.

Prioritization

Assign each recommendation a priority:

P0 — Critical: Must be addressed before significant growth or further architectural changes.
P1 — High: Strongly recommended for the next development iterations.
P2 — Medium: Valuable improvement that can be scheduled later.
P3 — Low: Optional improvement or future consideration.

Also classify the nature of each task:

Architecture.
Refactoring.
Documentation.
Tooling.
Testing.
Developer experience.
Technical debt.

For each task, provide:

Description.
Motivation.
Affected files.
Expected result.
Dependencies on other tasks.
Risk level.
Estimated effort: XS, S, M, L, XL.

Effort estimates should be relative and should not pretend to be precise time estimates.

Identify tasks that can be executed independently and tasks that must be completed in a specific order.

11. Expected Deliverables

Your final response must be structured as a professional technical assessment.

Produce the following sections.

A. Executive Summary

A concise overview of:

Current project maturity.
Main architectural observations.
Most important weaknesses.
Biggest opportunities.
Overall restructuring recommendation.
B. Current State Assessment

A factual description of the existing project.

Include the current architecture, repository organization, development practices, documentation, and major technical debt areas.

C. Architecture Map

Provide:

Main modules.
Their responsibilities.
Important relationships.
Main execution flows.
Identified architectural boundaries and problems.

Use Mermaid diagrams when they genuinely improve understanding.

D. Target Architecture

Explain the recommended architecture and justify its choices.

Include a proposed complete folder tree.

E. File-Level Migration Plan

Provide a detailed table of file operations.

Use actual repository paths and proposed paths.

Identify files to create, move, split, merge, rename, or remove.

F. Development Standards

Provide the recommended conventions and practices adapted to the actual technology stack.

Clearly separate mandatory conventions from recommendations.

G. Documentation Plan

Provide the proposed documentation tree and explain exactly what each document should contain.

Identify existing documents that should be retained, updated, merged, moved, or removed.

H. Tooling and Quality Gates

List recommended tools, configurations, and automated checks.

I. Prioritized Implementation Roadmap

Provide the complete phased task list, priorities, dependencies, effort estimates, and risks.

J. Risks and Open Questions

Identify:

Potential regressions.
Breaking changes.
Migration risks.
Architectural uncertainties.
Missing product information.
Decisions that require human validation.
K. Definition of Done

Define objective conditions that will indicate that the restructuring is successful.

Consider:

Clear module responsibilities.
Predictable folder organization.
Consistent conventions.
Reliable automated checks.
Useful and concise documentation.
Easy onboarding for developers and AI agents.
Maintainable architecture.
No unnecessary abstraction or complexity.
12. Analysis Rules and Constraints

These rules are mandatory throughout the mission.

Do not modify the repository.
Do not implement proposed changes.
Do not assume the current architecture is necessarily wrong.
Do not assume a particular framework or architecture in advance.
Inspect actual source files, not just folder names.
Use existing documentation and roadmap information as investigation inputs.
Verify documentation claims against the implementation whenever possible.
Do not invent file paths or modules.
Distinguish facts, hypotheses, and recommendations.
Reference actual files and directories to support findings.
Do not recommend a refactoring without explaining its benefit.
Do not recommend documenting obvious implementation details.
Do not introduce unnecessary abstractions or dependencies.
Do not artificially constrain the size of the proposed restructuring.
Consider the future product roadmap, not just the current implementation.
Do not confuse scalability with adding infrastructure or complexity prematurely.
Explicitly identify changes that could break existing behavior.
If the repository is too large to inspect exhaustively, explain the investigation boundaries and identify what remains unverified.

If you cannot access an issue tracker, external roadmap, or other referenced resource, state this explicitly.

Never claim that a file, test, command, or behavior has been verified unless you actually inspected or executed it.

13. Final Objective

At the end of this mission, we should have a clear answer to the following question:

If we wanted to invest in making this project clean, structured, maintainable, scalable, and enjoyable to work on for the next several years, what exactly should we change, why should we change it, and in what order should we do it?

The final plan must be ambitious in scope but pragmatic in its recommendations.

Do not optimize for the smallest possible diff.

Optimize for the best long-term project organization, developer experience, maintainability, and ability to evolve.

Think like an architect responsible for the future of the product, not like a developer trying to clean up a few files.

Take the necessary time to investigate before making recommendations.