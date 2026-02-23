# 🤖 Claude Code Agent Prompts

**A reusable library of specialized AI agent prompts for multi-agent software development with Claude Code.**

Drop these into any project's `agents/` directory, point your `CLAUDE.md` at them, and get consistent, expert-level output across architecture, implementation, testing, deployment, and documentation phases.

---

## Why Agent Prompts?

Large development projects benefit from specialized perspectives. Instead of asking one generalist to handle everything — architecture, database logic, Excel formatting, deployment scripting, testing — you assign focused roles that carry deep domain knowledge and enforce specific standards.

These prompts are designed to:

- **Eliminate context-setting repetition.** Each agent already knows its domain patterns, anti-patterns, and gotchas.
- **Enforce consistency.** The QA agent always checks the same 15 edge cases. The Architect always enforces the same design patterns. Standards don't drift.
- **Work across projects.** Every agent starts with "Read `CLAUDE.md` for project context" — swap the project, keep the expertise.
- **Compose naturally.** Use the Architect for design, Python Expert for implementation, QA Reviewer before merging. They're built to hand off work to each other.

---

## Agents

### 🏗️ Solutions Architect — `architect.md`

System design, module boundaries, and structural code review.

**Owns:** Component interfaces, data flow design, configuration schemas, dependency management.

**Enforces:** Dependency injection, strategy pattern, separation of concerns, context managers for resource lifecycle, configuration over hardcoded values.

**Use when:** Starting a new module, deciding how components interact, reviewing PRs for structural consistency, resolving conflicting approaches, planning development phases.

**Key behaviors:**
- Proposes interfaces and function signatures, not just descriptions
- Flags coupling risks and design debt proactively
- Reviews against a concrete checklist (type hints, pathlib, logging, error handling, config-driven values)

---

### 🐍 Python Expert — `python_expert.md`

Core business logic, idiomatic Python, and data processing pipelines.

**Owns:** Module implementation, data transformations, external system integrations, performance optimization.

**Enforces:** Type hints everywhere, dataclasses for structured data, pathlib for paths, logging over print, context managers, f-strings, Google/NumPy-style docstrings.

**Use when:** Writing core logic modules, building data pipelines, debugging Python-specific issues, reviewing code for Pythonic patterns, optimizing performance.

**Key behaviors:**
- Shows working code examples for every pattern
- Prefers standard library before third-party packages
- Writes code that's testable by design (dependency injection, pure functions)
- Includes error handling philosophy with specific do/don't examples

---

### 🗄️ Data & Database Expert — `data_expert.md`

SQL, ETL pipelines, data modeling, and data quality.

**Owns:** Database schemas, query design, extract-transform-load pipelines, data validation rules, connection management.

**Enforces:** Parameterized queries (never string interpolation), batch operations, connection context managers, idempotent ETL, record count verification at every stage.

**Use when:** Designing schemas, writing SQL or database interaction code, building ETL pipelines, debugging data quality issues, optimizing queries.

**Key behaviors:**
- Always considers null handling explicitly
- Includes data quality checks as standard practice (null counts, duplicates, range validation, referential integrity)
- Thinks about data lineage — where did this value come from?
- Quantifies everything: record counts, cardinality, expected vs. actual

---

### ✅ QA Reviewer — `qa_reviewer.md`

Testing strategy, edge cases, failure modes, and data integrity.

**Owns:** Test suite design, pytest fixtures, mock strategies, edge case identification, pre-deployment verification.

**Enforces:** Tests for failure cases (not just happy path), boundary condition coverage, parametrized tests, realistic fixtures, isolated test execution.

**Use when:** Writing tests, identifying edge cases in proposed implementations, validating error handling, running pre-deployment checks, reviewing outputs for data integrity.

**Standard edge case checklist (always checked):**
1. Empty input
2. Single record
3. Null/None values in every nullable field
4. Boundary values (min, max, exactly at thresholds)
5. Duplicate data
6. Unexpected types
7. Large volumes
8. Permission denied
9. Network failure
10. Corrupted input
11. Unicode / special characters
12. Concurrent access / file locks
13. Missing configuration
14. Future dates
15. Disk full

**Key behaviors:**
- Thinks like a pessimist — what will break?
- Proposes specific test cases with inputs and expected outputs
- Flags untested code paths explicitly
- When finding a bug, suggests both the fix and the test that would have caught it

---

### 🚀 DevOps Expert — `devops_expert.md`

Deployment, scheduling, logging, and production operations.

**Owns:** Entry point scripts (batch/shell), Task Scheduler and cron configuration, logging architecture, email notifications, deployment checklists.

**Enforces:** UNC paths over mapped drives (Windows), proper Python environment invocation, non-interactive compatibility, structured logging with timestamps, exit codes for scheduler integration.

**Use when:** Setting up scheduling, debugging "works manually but fails when scheduled," handling paths and permissions, implementing logging/notifications, creating deployment runbooks.

**Includes ready-to-use templates for:**
- Windows `.bat` wrapper for Task Scheduler
- Linux shell wrapper for cron
- CLI argument parser with `--mode`, `--validate`, `--dry-run`
- Structured logging setup (file + optional console)
- Email failure notification via smtplib
- Deployment checklist
- Troubleshooting table (symptom → likely cause → fix)

---

### 📊 Excel & Report Expert — `excel_expert.md`

Automated spreadsheet generation with openpyxl.

**Owns:** Exporter modules, conditional formatting, data validation dropdowns, multi-sheet workbooks, dashboard formulas, archive-before-overwrite logic.

**Enforces:** Explicit `number_format` on every date/number cell, `PatternFill` with `fgColor`, cell-by-cell writing (not `ws.append()`) for formatted rows, consistent color palette, frozen panes and auto-filters.

**Use when:** Building Excel output modules, designing spreadsheet layouts, implementing conditional formatting or validation, debugging openpyxl rendering.

**Includes ready-to-use patterns for:**
- Professional header formatting (dark fill, white font, centered, frozen)
- Alternating row colors
- Status column conditional formatting (green/yellow/red/gray)
- Dropdown data validation
- Dashboard summary sheets with COUNTIF formulas
- File archiving before overwrite

---

### 📝 Technical Writer — `technical_writer.md`

Documentation that people actually read.

**Owns:** README.md, CLAUDE.md, SOPs, API documentation, runbooks, inline code comments.

**Enforces:** Progressive disclosure (Quick Start → Usage → Advanced → Troubleshooting), tested instructions, consistent voice, scannable headers, code blocks for all commands and paths.

**Use when:** Writing or updating project documentation, creating user-facing guides, documenting APIs or configuration, creating operations runbooks.

**Key principles:**
- Concise over complete — a short doc that gets read beats a long one that doesn't
- Action-oriented — lead with what to do, not theory
- Tested instructions — if you write "run this command," verify it works
- One idea per paragraph, paragraphs under 4 sentences

---

### 🎨 Frontend & UI Expert — `frontend_expert.md`

Web interfaces, React components, and data visualization.

**Owns:** UI components, responsive layouts, data visualizations, accessibility compliance, frontend performance.

**Enforces:** Semantic HTML, ARIA labels, keyboard navigation, WCAG AA contrast, mobile-first responsive design, React hooks best practices, Tailwind utility patterns.

**Use when:** Building web interfaces, implementing dashboards or visualizations, reviewing for accessibility, designing React component architecture, creating HTML/CSS prototypes.

**Includes:**
- React component structure convention (state → effects → handlers → computed → render)
- Accessibility checklist (7 items)
- Library recommendations by complexity (Recharts vs. D3 vs. Chart.js)
- CSS/Tailwind patterns

---

## Usage

### Adding to a Project

```bash
# Copy the agents you need into your project
mkdir -p your-project/agents
cp generic-agents/architect.md your-project/agents/
cp generic-agents/python_expert.md your-project/agents/
cp generic-agents/qa_reviewer.md your-project/agents/
```

### Referencing from CLAUDE.md

Add a section to your project's `CLAUDE.md`:

```markdown
## Multi-Agent Development

Specialized agent prompts live in `agents/`. Reference the appropriate agent
when working on specific areas:

- **Architecture decisions** → Read `agents/architect.md`
- **Core implementation** → Read `agents/python_expert.md`
- **Before merging** → Read `agents/qa_reviewer.md`
```

### In Claude Code

When working in Claude Code, reference agents by telling the model to read the relevant file before starting work:

```
Read agents/architect.md and then review the proposed module structure for the new ETL pipeline.
```

```
Read agents/qa_reviewer.md and write tests for src/scanner.py, focusing on edge cases around null date handling.
```

### In Claude Chat

Copy-paste the relevant agent prompt at the start of a conversation to set the expertise context, or include it as part of a project-level system prompt.

---

## Agent Combinations

Most tasks benefit from multiple agents. Here's how they work together across typical development phases:

| Phase | Primary Agent | Supporting Agent(s) |
|-------|--------------|---------------------|
| **Design & Planning** | Architect | Data Expert, Technical Writer |
| **Core Implementation** | Python Expert | Data Expert |
| **Report/Output Building** | Excel Expert | Architect (for interfaces) |
| **UI Development** | Frontend Expert | Python Expert (for API contracts) |
| **Testing** | QA Reviewer | Python Expert, Data Expert |
| **Deployment** | DevOps Expert | Technical Writer (for runbooks) |
| **Documentation** | Technical Writer | All (for accuracy review) |
| **Code Review** | Architect + QA Reviewer | Domain expert for the area changed |

### Example: Building an ETL Pipeline

1. **Architect** designs the module structure and data flow
2. **Data Expert** implements the extraction and transformation logic
3. **Python Expert** reviews for idiomatic patterns and error handling
4. **Excel Expert** builds the output spreadsheet exporter
5. **QA Reviewer** writes tests covering edge cases and data integrity
6. **DevOps Expert** creates the scheduling wrapper and deployment checklist
7. **Technical Writer** documents setup, configuration, and troubleshooting

---

## Customization Guide

These agents are intentionally generic. To get the most out of them for your specific environment:

### 1. Add Domain Context

Fork an agent and add your tech stack specifics:

```markdown
### Environment-Specific Patterns
- All scripts run inside ArcGIS Pro's Python (propy.bat) — no standalone Python
- Enterprise geodatabases use Oracle on kysdewan
- All paths must work on Windows 10 state government workstations
```

### 2. Add Real Examples

The most effective customization is adding 2-3 real code examples from your codebase:

```markdown
### Our Patterns
Here's how we handle SDE connections in this project:
```python
# [paste actual working code from your project]
```
```

### 3. Narrow the Scope

If you only need Excel output (not PDF/HTML/CSV), trim the Excel Expert to just openpyxl. If you're only on Windows, remove the cron templates from DevOps Expert.

### 4. Add Review Checklists

Each agent has a review checklist. Add project-specific items:

```markdown
### Additional Review Items
- [ ] Does it handle the SMIS Oracle connection timeout?
- [ ] Are permit numbers validated against the expected format?
```

### 5. Cross-Reference CLAUDE.md

Every agent starts with "Read `CLAUDE.md`" — the richer your CLAUDE.md, the better every agent performs. At minimum, your CLAUDE.md should include:

- Project directory structure
- Tech stack and environment constraints
- Data models / key data structures
- Code standards (naming, formatting, error handling)
- Configuration file schemas

---

## CLAUDE.md Starter Template

Every agent reads `CLAUDE.md` for context. Here's a minimal template to get started:

```markdown
# CLAUDE.md — [Project Name]

## Project Identity
**Name:** [Project name]
**Author:** [Your name and role]
**Purpose:** [One paragraph describing what this project does]

## Architecture Overview
[Directory tree with brief descriptions]

## Technical Context
- **Python:** [version]
- **OS:** [target platform]
- **Key Libraries:** [list]
- **External Systems:** [databases, APIs, services]

## Data Model
[Key dataclasses or schemas]

## Code Standards
- Naming: [conventions]
- Error handling: [strategy]
- Logging: [approach]
- Configuration: [where settings live]

## Development Phases
1. [Phase 1 scope]
2. [Phase 2 scope]
3. [Phase 3 scope]
```

---

## File Structure

```
claude-code-agents/
├── README.md              ← You are here
├── architect.md           ← Solutions Architect
├── python_expert.md       ← Python Expert
├── data_expert.md         ← Data & Database Expert
├── qa_reviewer.md         ← QA Reviewer & Testing Expert
├── devops_expert.md       ← DevOps & Deployment Expert
├── excel_expert.md        ← Excel & Report Output Expert
├── technical_writer.md    ← Technical Writer & Documentation Expert
└── frontend_expert.md     ← Frontend & UI Expert
```

---

## Contributing

To add a new agent:

1. Follow the existing format: **Role → Responsibilities → Patterns (with code) → Communication Style → When to Use**
2. Start with "Read `CLAUDE.md`" so it's immediately project-aware
3. Include concrete code examples for every pattern you want enforced
4. Add a review checklist with checkboxes
5. List anti-patterns alongside the preferred patterns
6. Keep it under 200 lines — focused expertise, not encyclopedic coverage
7. Add an entry to this README with the same structure as existing agents

---

## License

MIT — Use these however you want. Attribution appreciated but not required.

---

*Built for AI-assisted development workflows. These prompts grew out of real production projects automating enterprise geodatabase management, environmental compliance reporting, and regulatory data pipelines.*
