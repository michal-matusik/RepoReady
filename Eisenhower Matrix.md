# Eisenhower Matrix

RepoReady - CS 193, Fall 2026

The Do quadrant defines the MVP for auditing one local Git repository or one remote public GitHub repository.
All features below are planned, not implemented.

| | Urgent | Not urgent |
| --- | --- | --- |
| Important | Do: deliver the single-repository audit MVP | Schedule: expand after the MVP |
| Not important | Delegate: use existing tools | Delete: exclude from this project |

## Do - Important and urgent (MVP)

1. Accept a local repository path or a public GitHub repository and validate the input.
2. Read local repository data through Git or remote public repository data through the GitHub CLI/API without cloning.
3. Check README and `.gitignore` presence and obvious README placeholder text.
4. Summarize recent commits for local and remote repositories, including empty histories.
5. Detect uncommitted changes and untracked files locally; mark the remote working-tree check `N/A`.
6. Flag potentially sensitive tracked filenames without exposing file contents.
7. Produce actionable terminal results with optional Markdown export.
8. Handle invalid inputs, API errors, unavailable data, and rate limits; test both audit modes.

## Schedule - Important but not urgent (V2+)

1. Audit multiple repositories in one command or all public repositories in a GitHub account.
2. Add explicitly authorized private repository audits.
3. Check broken relative README links and missing referenced files.
4. Integrate GitHub Actions and scheduled audits.
5. Compare saved reports over time.

## Delegate - Urgent but not important (use existing tools)

1. Use Git commands to inspect local repositories instead of implementing Git internals.
2. Use the GitHub CLI/API for remote requests and `jq` for JSON parsing.
3. Use standard Unix utilities for text matching and formatting.
4. Use ShellCheck for common Bash mistakes and Bats for automated testing.

Delegate refers to relying on established tools, not delegating the student's implementation or diagram to AI.

## Delete - Not important and not urgent (cut)

1. AI-generated code reviews or automatic code rewriting.
2. A web dashboard, user accounts, and cloud report storage.
3. Automatic modification or deletion of audited repository files.
4. Comprehensive secret-content scanning and vulnerability analysis.
5. Automatic repair commits or pull requests.
