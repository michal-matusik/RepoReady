# Development plan

## Scope and process

Implement the project incrementally as student-authored Bash code.
Preserve both local and remote public GitHub audits throughout the MVP.
The milestones below are a plan, not a record of completed implementation.
Do not fabricate commits to suggest work that has not occurred.

| Milestone | Completion criteria | Suggested commit |
| --- | --- | --- |
| 1. Repository setup | Publish planning docs and root matrix; add the student's real diagram and editable source before submission | `chore: initialize project and planning docs` |
| 2. CLI input | Accept a local path or `--github owner/repo`; define help, output option, and invalid-input behavior | `feat: add CLI input and validation` |
| 3. Local analysis | Retrieve tracked files, status, and recent history; handle paths with spaces and repositories without commits | `feat: add local repository analysis` |
| 4. GitHub integration | Read public metadata, files, and commits without cloning; handle access errors, rate limits, pagination, and incomplete responses | `feat: add public GitHub repository analysis` |
| 5. Documentation checks | Run README, `.gitignore`, and placeholder checks in both modes with consistent results | `feat: add documentation checks` |
| 6. Git analysis | Summarize recent commits in both modes; report local changes only in local mode and `N/A` remotely | `feat: add Git status and history checks` |
| 7. Filename checks | Inspect tracked filenames in both modes and explain warnings without printing sensitive contents | `feat: add sensitive filename warnings` |
| 8. Reports | Produce terminal and Markdown reports with matching results, actionable messages, and documented exit codes | `feat: add terminal and Markdown reports` |
| 9. Testing | Exercise both modes, missing files, empty history, invalid inputs, and remote failures; pass ShellCheck and Bats checks | `test: cover local and remote audits` |
| 10. Final polish | Verify the complete user workflow; document real setup, examples, limitations, and prepare the walkthrough | `docs: finalize usage and demonstration` |

## Planned verification

Use temporary local repositories for clean, dirty, empty-history, missing-documentation, and sensitive-filename cases.
Include filenames and directory paths containing spaces.
Use controlled GitHub API responses to cover inaccessible repositories, network failures, rate limits, and truncated or paginated data.
Validate one real public repository end to end when remote integration exists.
Verify terminal and Markdown findings agree and that auditing leaves the target repository unchanged.

## Decisions to finalize during implementation

- Exact placeholder patterns and filename patterns, with documented false-positive limits.
- Precise `PASS`, `WARN`, `FAIL`, and `N/A` meanings and exit-code policy.
- Supported README names, history length, and remote response completeness checks.
- Dependency installation and GitHub authentication instructions after testing the supported environments.

These decisions remain student implementation work.
