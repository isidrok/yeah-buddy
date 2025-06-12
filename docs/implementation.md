# BUDDY Framework Implementation Details

## Architecture

### Claude Code Integration
- Uses Claude imports via `@` syntax in `CLAUDE.md`
- Commands are workflow instructions, not bash commands
- Auto-triggered by greeting patterns

### File Structure
```
.buddy/
└── tasks/
    └── [task-name]/
        ├── TASK.md      # Task definition
        ├── PROGRESS.md  # Simple checklist
        ├── PLAN.md      # High-level strategy
        └── PHASE-N.md   # Phase details

.claude/
└── commands/
    ├── buddy.md       # Main router
    ├── buddy-new.md   # Task creation
    ├── buddy-plan.md  # Planning workflow
    └── buddy-work.md  # Implementation workflow

CLAUDE.md              # Buddy personality + imports
```

## Key Design Decisions

### No State Files
- **Decision**: Removed `CURRENT.md` file
- **Rationale**: User selection is cleaner than state management
- **Impact**: Each command handles task selection independently

### Simple Progress Tracking
- **Format**: Markdown checkboxes only
- **Content**: `Created`, `Planned`, `Phase N`, `Done`
- **Benefit**: Easy to read/parse, no extra text

### Separation of Concerns
- **buddy-new**: Only creates task structure, no planning
- **buddy-plan**: Handles all planning and phase creation
- **buddy-work**: Executes phases, can adjust plans as needed

### Plan Flexibility
- Plans can change at any time
- Affected phases are updated automatically
- Progress is reset for changed phases
- Completed work is preserved where possible

## Claude Import System

### CLAUDE.md Structure
```markdown
## BUDDY Command Workflows

- Main entry point: @.claude/commands/buddy.md
- Create new task: @.claude/commands/buddy-new.md  
- Plan task: @.claude/commands/buddy-plan.md
- Work on task: @.claude/commands/buddy-work.md

When user says "hi buddy" or similar greetings, follow the main entry point workflow.
```

### Auto-Trigger Pattern
- Detects greetings: "hi buddy", "hey buddy", "hello buddy"
- Automatically follows `buddy.md` workflow
- No manual command execution needed

## Buddy Personality Implementation

### Core Traits
- **Direct & Critical**: Explicitly challenges assumptions
- **Collaborative**: Continuous dialogue, not command execution
- **Technical Excellence**: Suggests better approaches
- **Conversational**: Regular check-ins and feedback loops

### Interaction Patterns
1. **Start conversations**: "Hey buddy, I'm looking at this..."
2. **Regular check-ins**: "How's this looking so far?"
3. **Challenge and suggest**: "That'll work, but here's a cleaner approach..."

### Example Dialogue Flow
```
Buddy: "🧠 Alright buddy, I've reviewed auth-system.
        What's your initial thinking on the technical approach?"

User: "I was thinking JWT tokens with Redis for sessions"

Buddy: "That could work, but what about scaling Redis? 
        Have you considered stateless JWTs with refresh tokens?"
```

## Error Handling

### Missing Tasks
- Commands detect when no tasks exist
- Provide clear guidance to run `buddy-new`
- Never fail silently

### Invalid States
- Check progress status before proceeding
- Guide user to appropriate next step
- Handle incomplete planning gracefully

### File Consistency
- Always validate file structure before operations
- Create missing files as needed
- Clean up orphaned files during replanning

## Extension Points

### Adding New Commands
1. Create `.claude/commands/[name].md` with workflow
2. Add import to `CLAUDE.md`
3. Update router logic in `buddy.md` if needed

### Customizing Progress Tracking
- Modify checklist format in command files
- Update all three commands consistently
- Consider backward compatibility

### Enhancing Buddy Personality
- Update interaction patterns in `CLAUDE.md`
- Add more dialogue examples in command files
- Maintain conversational consistency

## Testing Approach

### Manual Testing Flow
1. Start fresh session: "hi buddy"
2. Create task: Follow through buddy-new
3. Plan task: Execute buddy-plan workflow
4. Work on task: Execute buddy-work workflow
5. Test plan changes during work
6. Test task switching

### Validation Points
- File creation/updates happen correctly
- Progress checklist stays in sync
- Plan changes cascade properly
- Dialogue feels natural and collaborative
- All commands handle task selection independently