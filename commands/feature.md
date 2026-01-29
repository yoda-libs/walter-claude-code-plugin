---
description: "Feature Development Workflow"
arguments: "description"
arguments_description: "Description of the feature or task to implement (required)"
---

# Feature Development Workflow

Orchestrate a complete feature development lifecycle using specialized Walter subagents.

## Usage

```
/walter:feature <description>
```

**Example:**
```
/walter:feature Add user authentication with OAuth2 support
```

## Input
$ARGUMENTS - Description of the feature or task to implement (required)

---

## Pre-Flight Check

**FIRST**, run this command to check if Walter has been initialized for this project:

```bash
test -f .walter/init && echo "INITIALIZED" || echo "NOT_INITIALIZED"
```

### If NOT_INITIALIZED

The project has not been set up for Walter agents. You must initialize it first.

**Read the initialization instructions:**
```
Read .walter/init-instructions.md
```

**Follow those instructions to:**
1. Create the knowledge base structure (`.walter/project-kb/`)
2. Populate KB with parallel subagents (features, patterns, SOPs)
3. Create `.walter/WALTER-PROJECT.md` with operational config
4. Install the agent-browser skill
5. Create the `.walter/init` marker file

**Do NOT proceed with feature development until initialization is complete.**

---

### If INITIALIZED

**Read the project knowledge base first:**
```
Read .walter/project-kb/README.md
```

This will help you understand:
- Existing features (to avoid duplication and understand context)
- Code patterns (to follow established conventions)
- SOPs (to know how things are done in this project)

Then proceed with the feature development workflow below.

---

## Workflow Overview

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  1. PLAN    │ ──► │  2. DEVELOP │ ──► │  3. TEST    │ ──► │  4. REVIEW  │ ──► │  5. DOCUMENT│
│  product-mgr│     │  developer  │     │  qa-tester  │     │ code-reviewer│    │  kb-updater │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
```

Each phase uses a specialized subagent. All agents:
- Read `.walter/WALTER-PROJECT.md` for operational commands and config
- Reference `.walter/project-kb/` for project knowledge when needed

---

## Phase 1: Planning

**Subagent**: `walter-product-manager`
**Access**: Read-only

Create a PRD with acceptance criteria:

```
Use the walter-product-manager subagent to plan: $ARGUMENTS
```

The product manager will:
- Read `.walter/project-kb/features/` to understand existing features
- Read `.walter/project-kb/patterns/` to consider technical constraints
- Create a PRD with testable acceptance criteria

**Output**: PRD saved to `.walter/PRDs/`

**Exit Criteria**:
- PRD created with all sections
- Acceptance criteria defined (Given/When/Then format)
- User has reviewed and approved the PRD

---

## Phase 2: Development

**Subagent**: `walter-developer`
**Access**: Full (read/write)

Implement the feature according to the PRD:

```
Use the walter-developer subagent to implement [PRD_PATH]
```

The developer will:
- Read `.walter/project-kb/patterns/` for code conventions
- Read `.walter/project-kb/sop/` for how to perform tasks
- Follow commands from `.walter/WALTER-PROJECT.md`

**Output**: Working code with tests

**Exit Criteria**:
- All acceptance criteria implemented
- Tests passing with required coverage
- Linter and type checks pass

---

## Phase 3: Testing

**Subagent**: `walter-qa-tester`
**Access**: Read-only + agent-browser skill

Validate the implementation against acceptance criteria:

```
Use the walter-qa-tester subagent to validate [PRD_PATH]
```

**Output**: Test report with APPROVED/REJECTED verdict

**If REJECTED**: Return to Phase 2, fix issues, then re-test

**Exit Criteria**:
- All acceptance criteria verified
- All automated tests passing
- UI tested with agent-browser (for UI features)
- No critical/high severity bugs
- **APPROVED** status

---

## Phase 4: Code Review

**Subagent**: `walter-code-reviewer`
**Access**: Read-only

Security audit and code quality review:

```
Use the walter-code-reviewer subagent to review [PRD_PATH]
```

The reviewer will:
- Check code against `.walter/project-kb/patterns/`
- Verify security patterns from `.walter/WALTER-PROJECT.md`

**Output**: Security & code review report with APPROVED/REJECTED verdict

**If REJECTED**: Return to Phase 2, fix issues, re-test (Phase 3), then re-review

**Exit Criteria**:
- No critical/high security issues
- Code follows project patterns
- Data isolation verified (if applicable)
- **APPROVED** status

---

## Phase 5: Update Knowledge Base

**Subagent**: `walter-kb-updater`
**Access**: Full (read/write)

Document the newly implemented feature in the knowledge base:

```
Use the walter-kb-updater subagent to document [PRD_PATH]
```

The KB updater will:
- Read the PRD and implementation
- Create feature documentation in `.walter/project-kb/features/`
- Document any new patterns in `.walter/project-kb/patterns/`
- Add any new SOPs in `.walter/project-kb/sop/`
- Update the relevant index files

**Output**: Updated knowledge base documentation

**Exit Criteria**:
- Feature documented in project-kb
- New patterns documented (if any)
- New SOPs documented (if any)
- Index files updated

---

## Quick Reference

| Phase | Subagent | Access | Output |
|-------|----------|--------|--------|
| 1. Plan | `walter-product-manager` | Read-only | PRD |
| 2. Develop | `walter-developer` | Full | Code + Tests |
| 3. Test | `walter-qa-tester` | Read-only + browser | Test Report |
| 4. Review | `walter-code-reviewer` | Read-only | Review Report |
| 5. Update KB | `walter-kb-updater` | Full | KB Documentation |

---

## Current Task

**Feature**: $ARGUMENTS

### Action Required

1. **Check initialization**: Run the pre-flight check above
2. **If not initialized**: Follow `.walter/init-instructions.md`
3. **If initialized**:
   - Read `.walter/project-kb/README.md` for project context
   - Start Phase 1 with walter-product-manager
