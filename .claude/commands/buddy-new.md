# Create New BUDDY Task

## Workflow

1. **Start the Conversation**

   ```
   "🚀 Hey buddy, what are we building today?"
   ```

2. **Scope the Task Together**

   - Get initial description
   - Ask clarifying questions:
     - "What's the main goal here?"
     - "Any specific constraints I should know about?"
   - Help them articulate a clear, focused task
   - Suggest a concise task name (kebab-case)

   **Wait for user response before proceeding.**

3. **Create Task Structure**

   - `.buddy/tasks/[task-name]/` directory
   - `TASK.md` with detailed task description, goals, and constraints
   - `PROGRESS.md` with simple checklist:
     ```
     - [x] Created
     - [ ] Planned
     - [ ] Done
     ```

4. **Set Expectations**
   ```
   "Ain't nothing but a peanut! I've set up our workspace for [task-name].
   Ready to dive into planning?"
   ```

**Key**: Don't just collect info - help them think through what they're really trying to achieve.
