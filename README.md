# AGENT-ZERO

Operational framework and patterns for high-quality, AI-assisted software development. This repository provides a single canonical guide ([AGENTS.md](./AGENTS.md)) and a lightweight workflow for repeatable, auditable, and architecture-first delivery.

- Version: 2.1 (2025-10-25)
- Compatibility: Claude, Cursor, Copilot, Cline, Aider, and all AGENTS.md-compatible tools
- Status: Canonical single-file guide for AI-assisted development

---

## Why AGENT-ZERO?

AGENT-ZERO gives teams using AI coding tools a shared contract, state machine, and documentation patterns to ship real software safely:
- Reuse over creation (extend, don’t rewrite)
- Approval gates (no changes applied without explicit consent)
- Architecture-aligned changes (follow patterns, cite sources)
- High signal context (Memory Bank + focused state machine)

See the full spec in [AGENTS.md](./AGENTS.md).

---

## Quick Start

Start every session with the compliance banner, then load your Memory Bank and choose a mode:

```text
COMPLIANCE CONFIRMED: Reuse over creation

⚠️  GIGO PREVENTION - User Responsibilities:
📋 Clear task objectives | 🔗 Historical context | 🎯 Success criteria
⚙️  Architectural constraints | 🎖️ You lead - clear input = excellent output

[Continue with Memory Bank loading...]
```

- Attach MCP servers if present: `.brain/mcp.config.json` or `.mcp.json` (see [AGENTS.md §2. Session Startup](./AGENTS.md#2-session-startup))
- Choose a mode and load context:
  - Fast Track: monthly tasks README + quick-start
  - Standard: core project docs + recent updates
  - Deep Dive: architecture, ADRs, legacy cross-reference

Mode checklists and logging format are defined in [AGENTS.md §2](./AGENTS.md#2-session-startup).

---

## Core Principles

The Four Sacred Rules (summarized):
1. No new files without exhaustive reuse analysis
2. No rewrites when refactoring is possible
3. No generic advice — cite file:line and MB sections
4. No ignoring existing architecture/patterns

Details and validation checklists in [AGENTS.md §1](./AGENTS.md#1-compliance--core-rules).

---

## The Workflow (State Machine)

States: PLAN → BUILD → DIFF → QA → APPROVAL → APPLY → DOCS

- PLAN: Produce an implementation plan that cites current code and Memory Bank patterns. Exit only with explicit user approval.
- BUILD: Implement minimally in a sandbox branch, follow patterns, write tests, generate diff. Do not apply changes.
- DIFF: Present unified diff, rationale, integration points, and MB references.
- QA: Run tests, linters, coverage, build. Report structured results.
- APPROVAL: Human gate. Proceed only on explicit approval (“approved” / “looks good”).
- APPLY: Apply changes to the sandbox branch and verify.
- DOCS: Create task docs and update the Memory Bank.

Full details and formats (including report templates) in [AGENTS.md §4](./AGENTS.md#4-state-machine).

---

## Memory Bank (Your Operational Brain)

A small, curated set of docs that persist across sessions:

```
memory-bank/
├── toc.md
├── projectbrief.md
├── productContext.md
├── systemPatterns.md
├── techContext.md
├── activeContext.md
├── progress.md
├── projectRules.md
├── decisions.md
├── quick-start.md
├── database-schema.md
├── build-deployment.md
├── testing-patterns.md
└── tasks/
    ├── YYYY-MM/
    │   ├── README.md
    │   └── DDMMDD_*.md
    └── YYYY-MM/README.md
```

- Read frequently; write sparingly, and only with approval (see [AGENTS.md §3](./AGENTS.md#3-memory-bank))
- Cite MB sections in plans and diffs (e.g., `systemPatterns.md#Service Extension Pattern`)

---

## Task Contract and Budgets

Before building, define a task contract with:
- Context (repo, related work, constraints)
- Expected outcomes and acceptance criteria
- Architectural constraints and security notes
- Instructions (outline → approval → implement)

Budgets: cycles (retry loops), tokens (context), minutes (wall-clock). Track and request extensions when exceeded. See [AGENTS.md §5](./AGENTS.md#5-task-contract--budgets).

---

## Quality Gates

Do not proceed past APPROVAL without:
- Tests passing (unit + integration for new workflows)
- Linter clean (warnings allowed with justification)
- Coverage thresholds met (higher for new code)
- Security review completed

Checklists and standards in [AGENTS.md §6](./AGENTS.md#6-quality--documentation).

---

## Contribution Guidelines

- Sandbox first: never commit directly to `main`
- Approval gates: do not apply changes without explicit user approval
- Reuse analysis: document why extension is impossible before creating new files
- Citations:
  - Code: `path/file.ext:42-58`
  - Memory Bank: `memory-bank/systemPatterns.md#Section`
- Documentation:
  - Only after code approval (DOCS state)
  - Use task doc and monthly README templates in [AGENTS.md §6](./AGENTS.md#documentation-standards)

---

## Practical Boot Sequence (Abstracted from the field)

A field-tested, cross-agent routine for flawless execution:

1. Back up your agent configs and guides (e.g., AGENTS.md, CLAUDE.md, WARP.md, CURSOR.md).
2. Create symlinks (ln -s) to [AGENTS.md](./AGENTS.md) so tools share the same canonical files where possible.
3. Reboot your agent of choice (e.g., Claude Code). First command:
   ```
   Examine the code base to create the memory bank according to the AGENTS 2.1 spec. Do not use readme files or other documentation, examine the code and logic.
   ```
4. Clear the session memory to prevent context pollution: `/compact` or `/clear`.
5. On every subsequent boot, type: `startup`.
6. Provide a specific task (see Sample Task below) and ensure the agent starts in PLAN. Approve or edit the plan.
7. Type: `BUILD` to implement in a sandbox.
8. Review the presented diff and rationale. Then type: `QA` to run tests, linters, coverage, and build.
9. When QA passes, type: `Document it. Update the memory bank.`
10. Clear again (`/compact` or `/clear`) and repeat with the next task.

Advanced: Ask your chat agent to create a release plan with milestones and individual task files (YAML), using AGENTS.md as the format source.

This routine has been validated across Claude Code (Sonnet 4.5 1M), Copilot/Codex, Gemini, and others.

---

## Sample Task (End-to-end)

A minimal, high-signal task prompt that aligns with AGENTS.md PLAN → BUILD → QA:

```text
Task name: Add a modal to show store details
Context: Users currently see a list of stores, but many need more detail. When the user clicks the store name, they should see a modal with all store details, including a map, contact information, hours, and manager email address.
Desired outcome: User clicks the store name, a detailed modal appears.
Historical context: See the last task that built the list of stores.
Constraints (do/don't): Do not use fake data or stubs, etc. This request is mostly UX, focus specifically on the store detail modal.
Instructions: This is the PLAN process. Create a plan that addresses the user's specific request. Do not write code until the user has approved your plan.
```

Expected flow:
- PLAN: Agent proposes a structured plan with code citations and reuse strategy.
- BUILD: After explicit approval, implement minimally and generate diff.
- QA: Run tests, linters, coverage, build; report results.
- APPROVAL → APPLY → DOCS: Approve, apply to sandbox branch, then document updates in the Memory Bank.

Optional “Task Contract” expansion (adds acceptance criteria for QA alignment):
```markdown
## Task: Add a modal to show store details

### Context
- Repository: [path/area]
- Related Work: Last task that built the list of stores
- Constraints: No fake data or stubs; focus on UX for the store detail modal

### Expected Outcomes
- Acceptance Criteria:
  1. Clicking a store name opens a modal
  2. Modal displays map, contact info, hours, and manager email
  3. No regressions to the store list interaction
- Success Metrics: All criteria verified in tests; no UI regressions
- Definition of Done: PLAN approved; BUILD diff presented; QA passed; docs updated

### Instructions
Create a PLAN for approval. Do not write code until the plan is approved.
```

Ready-to-paste prompts for sessions:
```
startup
BUILD
QA
Document it. Update the memory bank.
/compact
```

---

## Troubleshooting

- Detect stalls: two identical diffs in a row
- Protocol: log → halt → diagnose → request direction or agent swap
- Common issues and decision tree in [AGENTS.md §8](./AGENTS.md#8-troubleshooting)

---

## FAQ

- Is this tool-specific? No. It works with Claude, Cursor, Copilot, Cline, Aider, and any tool that can follow [AGENTS.md](./AGENTS.md).
- Where do I start on a new feature? Begin at PLAN with a Task Contract, load the Memory Bank, propose a reuse-first plan.
- When do I update the Memory Bank? After major features, pattern discovery, or architectural decisions (see “When to Update MB” in [AGENTS.md §6](./AGENTS.md#6-quality--documentation)).

---

## Roadmap

- Enrich examples for multiple stacks (Node, Python, Go)
- Add reference CI workflows aligned with QA gates
- Optional MCP recipes for common operations

Contributions welcome—follow the state machine and approval gates.

---

## References

- Canonical spec: [AGENTS.md](./AGENTS.md)
- State machine and templates: [AGENTS.md §4](./AGENTS.md#4-state-machine)
- Memory Bank structure: [AGENTS.md §3](./AGENTS.md#3-memory-bank)
- Quality & Security: [AGENTS.md §6](./AGENTS.md#6-quality--documentation)
- Field-tested guide (reference): [openstudio/AGENTS.md](https://github.com/msitarzewski/openstudio/blob/main/AGENTS.md)
