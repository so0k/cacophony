<!--
Sync Impact Report:
Version: 0.0.0 → 1.0.0
Modified principles: N/A (initial creation)
Added sections:
  - Core Principles (5 principles focused on MVP, iteration, collaboration, component independence, UX consistency)
  - Development Workflow
  - Quality Gates
  - Governance
Removed sections: N/A
Templates requiring updates:
  ✅ plan-template.md - Constitution Check section references this file
  ✅ spec-template.md - User story priorities align with MVP-first principle
  ✅ tasks-template.md - Task organization by user story aligns with component independence principle
Follow-up TODOs: None
-->

# Cacophony Constitution

## Core Principles

### I. MVP-First Development

**MUST** build the smallest viable increment of value first, then iterate. **MUST** prioritize user stories (P1, P2, P3...) and deliver P1 stories completely before starting P2 work. Each priority level **MUST** be independently deployable and demonstrable to users.

**Rationale**: MVP-first development reduces risk, enables faster feedback loops, and ensures the team is always working on the highest-value features. Users see value sooner, and teams can pivot based on real feedback rather than assumptions.

### II. Fast Iteration Cycles

**MUST** complete work in small, verifiable increments. Each task **MUST** be completable within a single session when possible. **MUST** commit after each logical task or task group. **MUST** validate at checkpoints before proceeding to next phase.

**Rationale**: Small batches reduce integration risk, make debugging easier, enable rapid course correction, and maintain team momentum. Long-running branches and large changesets increase merge conflicts and delay feedback.

### III. Component Independence for Team Collaboration

**MUST** design components, modules, and tasks to be independently developable and testable. Different team members **MUST** be able to work on different user stories in parallel without blocking each other. Tasks marked [P] **MUST** be parallelizable (different files, no shared dependencies). Each user story **MUST** be independently completable.

**Rationale**: Independent components enable parallel work streams, reduce coordination overhead, prevent bottlenecks, and allow teams to scale efficiently. Components that can't be tested independently create cascading delays and integration nightmares.

### IV. Shared Foundations, Isolated Stories

**MUST** complete all foundational infrastructure (Phase 2: authentication, database, core models, error handling, routing) before starting user story implementation. Once foundations are complete, user stories **MUST** be implementable in parallel by different team members without conflicts.

**Rationale**: Shared foundations prevent duplicated effort and ensure consistency, while isolated story implementations enable team parallelization. Attempting story work before foundations are ready causes rework and architectural conflicts.

### V. User Experience Consistency

**MUST** maintain consistent interaction patterns, visual design, error messaging, and terminology across all components and user stories. **MUST** define UX patterns once and reuse them. **MUST** document UX decisions in design artifacts (contracts/, quickstart.md) for team alignment.

**Rationale**: Consistent UX reduces user cognitive load, builds trust, and makes features feel cohesive rather than bolted together. Inconsistent UX signals poor quality and creates training and support costs.

## Development Workflow

**MUST** follow this workflow for all features:

1. **Specification** (`/speckit.specify`): Define user stories with priorities, acceptance criteria, and independent test descriptions
2. **Planning** (`/speckit.plan`): Research, design data models, define contracts, create quickstart guide
3. **Task Generation** (`/speckit.tasks`): Break plan into dependency-ordered tasks organized by user story
4. **Implementation** (`/speckit.implement`): Execute tasks in priority order, validating at checkpoints
5. **Validation**: Each user story **MUST** be independently testable and demonstrable

**Parallel work**: Once foundational phase completes, multiple team members **MAY** work on different user stories simultaneously.

## Quality Gates

**MUST** pass these gates before proceeding:

### Constitution Check (before Phase 0 research, re-check after Phase 1 design)

- ✅ Feature broken into prioritized, independently testable user stories
- ✅ Foundational infrastructure identified and separated from story work
- ✅ Task organization enables parallel team collaboration
- ✅ UX patterns documented for consistency

### Checkpoint: Foundation Ready (after Phase 2)

- ✅ All foundational tasks complete
- ✅ Core infrastructure tested
- ✅ User story work can now proceed in parallel

### Checkpoint: Story Complete (after each user story phase)

- ✅ Story independently testable
- ✅ Story independently demonstrable
- ✅ UX consistent with documented patterns
- ✅ No regressions to previous stories

## Governance

This constitution supersedes all other development practices. All planning, implementation, and review **MUST** verify compliance with these principles.

**Amendment Process**: Amendments require:
1. Documented justification for the change
2. Impact analysis on existing templates and workflows
3. Version bump following semantic versioning (MAJOR.MINOR.PATCH)
4. Update to all dependent templates in `.specify/templates/`

**Versioning Policy**:
- **MAJOR**: Backward-incompatible changes (principle removals or redefinitions)
- **MINOR**: New principles added or material expansions to existing principles
- **PATCH**: Clarifications, wording improvements, non-semantic refinements

**Complexity Justification**: Any violation of these principles **MUST** be documented in the plan.md Complexity Tracking table with justification for why the violation is necessary and why simpler alternatives were rejected.

**Compliance Review**: All PRs, design reviews, and task execution **MUST** reference this constitution to verify alignment. Use `.specify/memory/constitution.md` for runtime development guidance.

**Version**: 1.0.0 | **Ratified**: 2025-11-27 | **Last Amended**: 2025-11-27
