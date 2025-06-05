This is a task orchestration and persistence system for LLM's based on Markdown checklists.

# Instructions
* Look for and run the requested task matching the name requested
* Read and complete each step in the markdown task file, one-by-one, in order, from top to bottom
* If a task is checked [x], move on to the next unchecked step
* When completing a task, check it and re-save the file. This allows resumption if interrupted
* If a step asks you to complete another task, do so
  * Complete all steps in the referenced task per these rules, including subtasks
  * Once the child task is fully completed, carry on with the original parent task and check the step if finished
* If a step asks you to generate another task, follow the Task Rules
* If the instructions ask to skip a sub-task or step, skip it, and check it off
* Steps may loop. A looping step has a current_attempt, and max_attempts value. Increment the current attempt in the 
markdown front-matter upon the start of each atempt to complete the step, and save. After the attempts are exhausted,
provide a helpful message with the task that failed, the number of attempts, and why it failed.


# Task Rules
* Tasks must:
  * be concise--every token has a cost
  * must be fully spelled out with actionable instructions and no skipped or undefined steps
  * must have sensible, descriptive, CamelCase names ending in .md
  * must be generated into the /tasks folder
* Tasks may:
  * reference other tasks, as steps
  * involve tools, code execution, research, interaction, etc.
  * generate code or other outputs
  * generate other markdown task checklists

* Task Looping:
  * If a step may fail and require “fix then retry,” put that into its own file
  * If a step is “one and done” (e.g. CreateBranch, CreateSpec), keep it flat--don't nest checkboxes
  * Inside a loop file, each “atomic action” should be a single checkbox

### Looping Example:

Place "front matter" like this at the top of a markdown containing a loop.  Use one loop per file.

---
current_attempt: 0
max_attempts: 3
---
- Loop: ** Run Tests**
  - Execute `npm test` (or `pytest`, etc.)
    - If tests failed, Do FixErrors.md
    - [ ] If tests passed, mark this loop done and continue. 