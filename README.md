# BUDDY Framework

BUDDY is a pair programming framework for Claude Code that creates a collaborative, conversational development experience. Buddy acts as an experienced engineer working alongside you, not just following commands.

## Quick Start

1. Say "hi buddy" to see task list, or "hi buddy let's work on [task-name]" to jump directly to a task
2. Follow the collaborative workflow
3. Switch tasks anytime by mentioning them in conversation

## Core Concepts

### Buddy Personality
- **Direct & Critical**: Challenges assumptions and design decisions
- **Collaborative**: True pair programming with constant dialogue
- **Technical Excellence**: Pushes for quality over quick fixes
- **Conversational**: Regular check-ins, suggestions, and feedback

### Task Structure
```
.buddy/tasks/[task-name]/
├── TASK.md          # Description, goals, constraints
├── PROGRESS.md      # Simple checklist
├── PLAN.md          # High-level strategy (created during planning)
└── PHASE-N.md       # Detailed phase plans (created during planning)
```

### Progress Tracking
Simple checkbox format in `PROGRESS.md`:
```
- [x] Created
- [x] Planned
- [ ] Phase 1
- [ ] Phase 2
- [ ] Done
```

## Commands

### Entry Point
- **"hi buddy"** → Automatically runs `/project:buddy`
- Shows task list and routes to appropriate workflow

### Available Commands
- `/project:buddy` - Main entry point and router
- `/project:buddy-new` - Create new task
- `/project:buddy-plan` - Plan task phases
- `/project:buddy-work` - Execute implementation

## Workflow Overview

1. **Start**: "hi buddy" → see task list
2. **Create**: Define task scope and goals
3. **Plan**: Break into phases collaboratively
4. **Work**: Execute phases with continuous feedback
5. **Iterate**: Adjust plans as needed

See individual command documentation for details.