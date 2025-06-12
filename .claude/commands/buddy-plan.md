# BUDDY Planning Phase

## Workflow

1. **Task Selection**

   - List all directories in `.buddy/tasks/`
   - If no tasks: "No tasks yet!."
   - If tasks exist, show list with status:
     ```
     "Which task should we plan?
     1. [task-name-1] - [status]
     2. [task-name-2] - [status]"
     ```
   - Once selected, read `TASK.md` for full context
   - Verify status in `PROGRESS.md`

2. **Start Planning Dialogue**

   ```
   "🧠 Alright buddy, I've reviewed [task-name].
   What's your initial thinking on the technical approach?"
   ```

   **If replanning existing task:**

   - Review current `PLAN.md` and `PHASE-N.md` files
   - Identify what's changing and why
   - Preserve completed work where possible

3. **Collaborative Planning Process**

   **Explore approaches together:**

   - "What are our main options here?"
   - "I see trade-offs between X and Y. What matters most?"
   - "That could work, but what about [alternative]?"

   **Break into phases:**

   - "How should we chunk this up?"
   - "What needs to happen first?"
   - "Each phase should be independently shippable - thoughts?"

   **Challenge and refine:**

   - "Is this the simplest solution that could work?"
   - "What could go wrong with this approach?"
   - "Are we overengineering this?"

4. **Document the Plan**

   - Create/update `PLAN.md` - High-level strategy and key decisions
   - Create/update `PHASE-1.md` - Detailed first phase with specific tasks
   - Create/update additional phase files as needed (PHASE-2.md, etc.)
   - Update `PROGRESS.md` checklist:
     ```
     - [x] Created
     - [x] Planned
     - [ ] Phase 1
     - [ ] Phase 2
     - [ ] Done
     ```
   - If phases were removed, clean up orphaned `PHASE-N.md` files

5. **Transition to Work**
   ```
   "Light weight, baby! Solid plan! Want to dive into Phase 1?"
   ```

**Remember**: This is a conversation, not an interrogation. Build the plan together.
