# BUDDY Commands Documentation

## Entry Point: `/project:buddy`

**Trigger**: Automatically executed when user says "hi buddy", "hey buddy", etc.

**Purpose**: Smart router that assesses context and guides to appropriate workflow.

**Flow**:
1. Checks if user mentioned a task name in greeting
2. If task mentioned, finds matching task and routes directly based on status
3. If no task mentioned, lists all tasks and shows status
4. Routes based on context:
   - Specific task mentioned → Direct routing to plan/work
   - No tasks exist → buddy-new
   - Tasks exist but none specified → Show selection menu

---

## `/project:buddy-new` - Create New Task

**Purpose**: Scope and define a new task through conversation.

**Key Points**:
- Starts with conversational greeting
- Helps user articulate clear, focused goals
- Creates minimal structure - no planning files yet
- Only creates `TASK.md` and `PROGRESS.md`

**Created Files**:
- `.buddy/tasks/[task-name]/TASK.md` - Full task description
- `.buddy/tasks/[task-name]/PROGRESS.md` - Simple checklist starting with "Created"

**Output**: Task ready for planning phase

---

## `/project:buddy-plan` - Plan Current Task

**Purpose**: Collaborative planning session to break work into phases.

**Key Features**:
- **Task Selection**: Lists available tasks if none specified
- **Replanning Support**: Can modify existing plans
- **Collaborative Dialogue**: Explores approaches, challenges assumptions
- **Phase Creation**: Breaks work into independent, resumable phases

**Process**:
1. Load task context from `TASK.md`
2. Review existing plans if replanning
3. Collaborative planning conversation:
   - Explore technical approaches
   - Discuss trade-offs
   - Break into phases
   - Challenge and refine
4. Create/update plan files
5. Update progress checklist

**Created/Updated Files**:
- `PLAN.md` - High-level strategy and decisions
- `PHASE-1.md`, `PHASE-2.md`, etc. - Detailed phase plans
- `PROGRESS.md` - Updated with phase checkboxes

**Plan Change Handling**:
- Reviews existing plans when replanning
- Preserves completed work where possible
- Cleans up orphaned phase files
- Resets progress for changed phases

---

## `/project:buddy-work` - Execute Implementation

**Purpose**: Work through planned phases with continuous collaboration.

**Key Features**:
- **Task Selection**: Lists available tasks if none specified
- **Pre-Implementation Check**: Reviews plan before starting
- **Plan Flexibility**: Can adjust plans during implementation
- **Continuous Dialogue**: Regular check-ins and feedback
- **Progress Tracking**: Updates checklist as phases complete

**Process**:
1. Load task and current phase context
2. Pre-implementation check (opportunity to adjust plan)
3. Collaborative implementation:
   - Regular check-ins
   - Decision points
   - Alternative suggestions
   - Progress celebration
4. Update progress as phases complete
5. Transition between phases

**Plan Change During Work**:
- Can update `PLAN.md` if approach changes
- Modifies affected `PHASE-N.md` files
- Updates progress checklist if phases change
- Resets progress for impacted phases

---

## Command Relationships

```
"hi buddy" → buddy → buddy-new → buddy-plan → buddy-work
                 ↓         ↑           ↑           ↓
                 └─ existing tasks ────┴───────────┘
```

## File Management

### Automatic Creation
- `buddy-new`: Creates `TASK.md` and `PROGRESS.md`
- `buddy-plan`: Creates `PLAN.md` and `PHASE-N.md` files
- `buddy-work`: Updates existing files, no new creation

### Automatic Updates
- All commands can update `PROGRESS.md` checklist
- `buddy-plan` and `buddy-work` can modify plan files
- Orphaned phase files are cleaned up during replanning

### File Consistency
- Progress checklist always reflects current phase structure
- Phase files match the phases in progress checklist
- Plan changes cascade to affected phase files