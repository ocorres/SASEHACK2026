# SASEHACK2026 — Solo Hackathon Runbook

This document is the handoff/checkpoint system for the entire hackathon. The goal is to make it possible to stop at any point, return later, and know exactly what is working, what is broken, and what happens next.

## Operating Loop

Every milestone follows the same loop:

1. **Define** — state the outcome and acceptance criteria.
2. **Build** — implement only what is needed for that outcome.
3. **Run** — execute the current vertical slice locally.
4. **Test** — verify the acceptance criteria and demo path.
5. **Commit** — preserve the known-good checkpoint in GitHub.
6. **Handoff** — record current state, blockers, and the single next action.

Do not start the next milestone until the current milestone has a known state.

---

## Milestone 0 — Event Intake

**Objective:** Understand what can actually win before choosing what to build.

### Inputs to capture
- Official challenge statement
- Judging rubric and weights
- Submission deadline
- Required sponsor technologies/APIs
- Available datasets/resources
- Team/eligibility rules
- Submission format
- Demo/presentation duration
- Prize tracks
- Prohibited/pre-existing work rules

### Exit criteria
- Requirements are written in `REQUIREMENTS.md`.
- Hard constraints are separated from optional opportunities.
- Judging criteria are explicit.
- Unknowns that could invalidate a concept are identified.

### Handoff
**Next:** Concept selection.

---

## Milestone 1 — Concept Selection

**Objective:** Choose one project that is impressive enough to matter and small enough to finish.

### Evaluate each concept on
- Direct fit to challenge
- AI necessity
- Demo clarity
- Technical feasibility
- Dependency/API risk
- Differentiation
- Time to first vertical slice
- Stretch potential

### Exit criteria
- One concept selected by the Tech Lead.
- One-sentence problem statement exists.
- One-sentence solution exists.
- Primary user is identified.
- MVP has no more than 3 core capabilities.
- Non-goals are recorded.

### Handoff
**Next:** Architecture + build plan.

---

## Milestone 2 — Architecture Freeze v0

**Objective:** Define the minimum architecture needed for the MVP.

### Required decisions
- Language/framework
- UI
- Model/provider
- Agent/tool pattern, if needed
- Storage, if needed
- External APIs
- Deployment target
- Main data flow

### Exit criteria
- Architecture is documented in `ARCHITECTURE.md`.
- Critical external services have been sanity-checked.
- Secrets strategy is defined through `.env`.
- Build tasks are ordered by dependency.
- No speculative infrastructure is included.

### Handoff
**Next:** Build the first end-to-end vertical slice.

---

## Milestone 3 — Vertical Slice

**Objective:** Produce the earliest demonstrable system.

### Required path
```
USER INPUT
    ↓
AI / AGENT
    ↓
MEANINGFUL PROCESSING OR ACTION
    ↓
VISIBLE RESULT
```

### Exit criteria
- App launches locally.
- One representative input works end-to-end.
- AI contributes materially to the result.
- Output is visible to the user.
- Happy-path smoke test passes.
- Known-good code is committed.

### Handoff
**Next:** Make the core capability useful rather than merely functional.

---

## Milestone 4 — Core Intelligence

**Objective:** Implement the capability that makes the project worth using.

Examples may include reasoning, retrieval, tool use, multimodal analysis, structured extraction, planning, or multi-step execution depending on the challenge.

### Exit criteria
- Core AI behavior works on multiple representative inputs.
- Outputs use a predictable structure where appropriate.
- Major hallucination/failure modes are understood.
- At least one technically meaningful differentiator exists.
- Core behavior is testable.

### Handoff
**Next:** Reliability and failure handling.

---

## Milestone 5 — Reliability

**Objective:** Make the demo difficult to break.

### Test
- Normal input
- Empty input
- Malformed input
- Large/unusual input
- API timeout/failure
- Missing configuration
- Repeated execution
- Exact demo input

### Exit criteria
- Critical failures are handled visibly.
- App does not expose secrets.
- Exact demo path passes repeatedly.
- `TEST_LOG.md` contains results.
- A known-good checkpoint is committed.

### Handoff
**Next:** UX and judge comprehension.

---

## Milestone 6 — Demo UX

**Objective:** Make the value understandable within roughly 30 seconds.

### Priorities
- Clear first screen
- Obvious input/action
- Visible AI activity only when useful
- Legible result
- Minimal clicks
- No dead controls
- No unfinished screens in the demo path

### Exit criteria
- A new user can understand the purpose without explanation.
- Demo path is short and deterministic.
- UI supports the pitch rather than distracting from it.
- Working functionality remains intact after polish.

### Handoff
**Next:** Submission and pitch.

---

## Milestone 7 — Submission Package

**Objective:** Make the project understandable without access to the developer.

### Deliverables
- Final README
- Problem and solution
- Architecture explanation
- Setup/run instructions
- Sponsor technology usage
- Screenshots/video if required
- Repository cleanup
- Submission form content

### Exit criteria
- Another developer could run the project from the README.
- Required submission fields are complete.
- Repository contains no secrets.
- Required links work.

### Handoff
**Next:** Pitch rehearsal and freeze.

---

## Milestone 8 — Pitch + Demo Freeze

**Objective:** Protect a working submission.

### Pitch structure
1. Problem
2. User
3. Solution
4. Live demo
5. What the AI is doing
6. Technical architecture/differentiator
7. Impact / next step

### Exit criteria
- Pitch fits the official time limit.
- Demo has been rehearsed end-to-end.
- Backup screenshots/video exist if appropriate.
- No nonessential feature development remains.
- Final known-good commit is identified.

### Handoff
**Next:** Submit.

---

# Checkpoint / Handoff Template

Complete this whenever we pause, change milestones, hit a blocker, or finish a significant implementation.

```text
PROJECT:
CURRENT MILESTONE:
STATUS: GREEN / YELLOW / RED

WORKING NOW:
-

JUST COMPLETED:
-

FILES / COMPONENTS CHANGED:
-

TESTS PASSED:
-

KNOWN ISSUES:
-

BLOCKERS:
-

DECISIONS MADE:
-

DO NOT BREAK:
-

CURRENT COMMIT:
-

SINGLE NEXT ACTION:
-
```

## Status definitions

- **GREEN** — milestone is on track and current build works.
- **YELLOW** — usable progress exists, but a risk/blocker needs attention.
- **RED** — critical path is broken or a constraint threatens completion.

---

# Scope Control

Every proposed feature must be classified:

- **MUST** — required for the core demo or judging criteria.
- **SHOULD** — meaningful improvement after the MVP works.
- **STRETCH** — only if the submission is already safe.
- **CUT** — explicitly not being built.

When time pressure increases, cut from the bottom upward. Never sacrifice a working demo to implement a stretch feature.

---

# Recovery Rule

If the project becomes unstable:

1. Stop adding features.
2. Identify the last known-good commit.
3. Reproduce the failure.
4. Restore the smallest working vertical slice.
5. Fix only the critical path.
6. Re-run the demo test.
7. Commit the recovered state.
8. Resume from the handoff template.
