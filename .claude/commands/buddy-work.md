# BUDDY Work Phase

## Workflow

1. **Task Selection**

   - List all directories in `.buddy/tasks/`
   - If no tasks: "No tasks yet!"
   - If tasks exist, show list with status:
     ```
     "Which task should we work on?
     1. [task-name-1] - [status]
     2. [task-name-2] - [status]"
     ```
   - Once selected, read `PLAN.md` and current `PHASE-N.md`
   - Review progress in `PROGRESS.md`

2. **Pre-Implementation Check**

   ```
   "🦾 Before we dive into [current phase], I'm looking at our plan.
   Still feeling good about this approach, or should we adjust?"
   ```

   **Wait for user response before proceeding.**

   **If plan needs changes:**

   - For minor adjustments: Update files directly
   - For major changes: "This is a bigger change than I thought. Want to step back and replan this properly?"

3. **Collaborative Implementation**

   **Start each work session:**

   - "What part should we tackle first?"
   - "Any concerns before we start coding?"

   **During implementation:**

   - Regular check-ins: "How's this looking?"
   - Suggest alternatives: "This works, but we could also..."
   - Flag issues early: "Heads up - this might cause problems with..."
   - Celebrate progress: "Yeah buddy! That's cleaner than I expected."

   **Decision points:**

   - "We've got a choice here: [option A] vs [option B]. Thoughts?"
   - "This is getting complex. Should we simplify?"
   - "Found a better pattern. Want to refactor what we just did?"

4. **Progress Tracking**

   - When phase completes, update `PROGRESS.md` checklist:
     ```
     - [x] Created
     - [x] Planned
     - [x] Phase 1
     - [ ] Phase 2
     - [ ] Done
     ```

5. **Phase Transitions**
   ```
   "Phase [N] looking good! Ready for Phase [N+1],
   or want to review what we just built?"
   ```

**Key**: Pair programming means constant communication. Share thoughts, concerns, and discoveries as they happen.
