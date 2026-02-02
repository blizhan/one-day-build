# Phase Details Reference

Detailed role breakdowns, communication patterns, and success metrics. SKILL.md contains the core workflow - read this for deeper context.

## Contents
- [Role Details by Phase](#role-details-by-phase)
- [Communication Patterns](#communication-patterns)
- [Success Metrics](#success-metrics)
- [Example Session](#example-session)

---

## Role Details by Phase

### Phase 1: Intent Clarification

**Human provides:**
- Project vision and goals
- Functional requirements list
- Constraints (tech stack, timeline, team size)
- Reference data or examples

**Agent does:**
- Asks "Which? How often? What format?" questions
- Surfaces implicit requirements ("You'll also need X for Y")
- Challenges flawed assumptions politely
- Proposes alternatives when constraints conflict

### Phase 2: Architecture Design

**Human provides:**
- Technology preferences
- Extensibility vs speed priority
- Future requirement hints

**Agent does:**
- Proposes 2-3 approaches with clear trade-offs
- Creates interface definitions (abstract base classes)
- Documents decisions with rationale in AGENTS.md

**Example decision format:**
```
Decision: Configuration-driven design
- YAML for data source configs
- Per-source defaults + per-indicator overrides
- Rationale: Add new indicator without code change
- Trade-off: More complex initial setup
```

### Phase 3: Foundation Implementation

**Human provides:**
- Sample data files
- Domain-specific edge cases
- Validation of real-world usage

**Agent does:**
- Sets up project structure, deps, git
- Implements core abstractions first
- Builds one complete feature end-to-end
- Creates test infrastructure

**Avoid:**
- Perfectionism - get something working first
- Over-engineering - start simple, refactor in Phase 4
- Ignoring edge cases - real data reveals real problems

### Phase 4: Problem-Driven Refinement

**Human provides:**
- Bug reports with data/context
- Priority decisions (fix vs feature)
- Acceptance of temporary workarounds

**Agent does:**
- Debugs systematically with root cause analysis
- Proposes refactoring plans before implementing
- Preserves existing tests, adds regression tests
- Documents what changed and why

### Phase 5: Testing Architecture

**Human provides:**
- What must be tested (critical paths)
- Test data samples
- Coverage expectations

**Agent does:**
- Creates reusable test utilities
- Implements factory functions for test generation
- Sets up parameterized tests for variants
- Optimizes for speed (<5s full suite)

**Testing layers:**
```
Unit tests     → Utility methods, pure functions
Integration    → Full workflow with mocked I/O
Parsing-only   → Data transformation, no network
```

### Phase 6: Documentation Sync

**Human provides:**
- Domain knowledge for docs
- Validation that examples work
- Clarification requests

**Agent does:**
- Updates AGENTS.md with session decisions
- Writes TODO.md with prioritized backlog
- Ensures README examples actually run
- Adds inline code comments for non-obvious logic

---

## Communication Patterns

### Effective

| Pattern | Example |
|---------|---------|
| Specific questions | "What should missing values be for SOI data?" |
| Context-rich bugs | "Row 1948 shows 2025.00, here's the raw CSV..." |
| Decision-focused | "Template Method vs Strategy - which fits better?" |
| Feedback loops | "This refactor cut 16% code, acceptable trade-off?" |

### Ineffective

| Pattern | Problem |
|---------|---------|
| "Make it better" | No actionable direction |
| Many changes at once | Can't isolate issues |
| No understanding check | Misalignment compounds |
| Ignoring edge cases | Bugs in production |

---

## Success Metrics

### Quantitative

| Metric | Target | Excellent |
|--------|--------|-----------|
| Session duration | 4-8 hrs | <4 hrs |
| Test coverage | >80% | >90% |
| Code reduction (refactor) | >10% | >20% |
| Documentation files | 3 | 5+ |
| Working features | 1 | 2+ |

### Qualitative

| Metric | How to Measure |
|--------|----------------|
| Extensibility | Add new source in <30 min |
| Testability | One-liner creates full test suite |
| Clarity | New contributor groks architecture in 10 min |
| Maintainability | Single change point for shared logic |

---

## Example Session

**Project:** Climate data pipeline (ClimABC)

**Phase 1 outcome:**
- 4 data sources identified (PSL, NCEI, ERA5, CAMS)
- CLI + web visualization required
- 3-day CI refresh cycle

**Phase 2 decisions:**
- Template Method for fetch workflow (saved 60% code later)
- YAML config for indicators (21 added without code changes)
- Async from start (easier than migration)

**Phase 3 deliverables:**
- PSL fetcher complete with tests
- Base class with shared validation
- Makefile with dev commands

**Phase 4 refactors:**
- Bug: Year validation missing → Added `_is_valid_year()`
- Smell: Repeated fetch logic → Template Method pattern
- Result: 16% code reduction

**Phase 5 testing:**
- Factory function: `create_fetcher_tests(Fetcher, data, expected)`
- Coverage: 90%+
- Speed: <3s

**Final metrics:**
- Duration: 8 hours
- 1 fetcher complete, 3 more trivial to add
- 24 tests passing
- Production-ready foundation
