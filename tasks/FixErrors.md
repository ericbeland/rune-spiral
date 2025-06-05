<!-- FixErrors.md -->
# FixErrors

- [ ] Open the most recent test or validation output log.
- [ ] For each listed failure (unit tests, lint errors, validation mismatches):
  - [ ] Locate the relevant source file and line number.
  - [ ] Edit the code to correct the issue.
  - [ ] Save the file.
- [ ] Re‐run lint or tests as appropriate to confirm fixes.
- [ ] Repeat until there are no remaining errors or failures.
- [ ] Commit all fixes:  
  ```bash
  git add .
  git commit -m "Fix errors encountered during test/validation"
  ```
