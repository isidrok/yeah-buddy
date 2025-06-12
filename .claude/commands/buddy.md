# BUDDY - Main Entry Point

## Purpose

Smart router that determines user intent and executes appropriate BUDDY commands automatically.

## Workflow

1. **Greet and Assess**

   ```
   "💥 Yeah buddy!"
   ```

   - Check if user mentioned a task name in their greeting
   - If task name mentioned, find matching task in `.buddy/tasks/`
   - If no task mentioned, list all directories in `.buddy/tasks/`
   - For each task, read its `PROGRESS.md` to show status

2. **Route Based on Context**

   **If specific task mentioned:**

   - Find task by matching name (fuzzy match acceptable: "auth system" → "auth-system")
   - Load task status from `PROGRESS.md`
   - Route directly based on status:
     ```
     "Got it, working on [task-name]!"
     ```
     - If "Created" → Follow buddy-plan.md
     - If "Planned/In Progress" → Follow buddy-work.md

   **If NO tasks exist:**

   ```
   "No tasks yet. What should we build today?"
   ```

   → Follow instructions in `.claude/commands/buddy-new.md`

   **If tasks exist but none specified:**

   ```
   "Here's what we've got:
   1. [task-name-1] - [status]
   2. [task-name-2] - [status]
   ...

   Which one do you want to work on? Or start something new?"
   ```

   - Based on selection, route to appropriate workflow

3. **Maintain Flow**
   - After completing any command, offer next logical step
   - Always give option to switch contexts
   - Keep conversational momentum going

**Key**: This command is the glue - it reads the room and gets us into the right workflow naturally.
