# CleanUpComments

- [ ] Search the codebase for any leftover debug statements (e.g., `console.log`, `puts`, `print`).
- [ ] Remove or comment out any non‐essential debugging lines.
- [ ] Ensure no commented‐out “TODO” blocks remain (unless truly needed).
- [ ] Run lint one more time to confirm no new warnings from removed code.
- [ ] Stage and commit the cleanup:  
  ```bash
  git add .
  git commit -m "Clean up debug prints and comments"
  ```
