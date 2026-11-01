# RepoReady

A planned Bash command-line tool for checking whether a Git repository is documented, organized, and ready to share.
Built by Michal Matusik for Purdue CS 193, Fall 2026.

## Project goal

Keeping several projects ready to share means repeatedly checking documentation, Git history, and repository files.
RepoReady will bring those checks into one readable report for either a local Git repository or a remote public GitHub repository, without requiring a clone for remote audits.

## Status

This repository contains project setup and planning documents only.
The application, installation steps, and audit commands have not been implemented yet.
The student-drawn System Diagram and its editable source are still required before Homework 9 is ready to submit.

## MVP scope

- Accept one local repository path or one public GitHub repository per audit.
- Validate the input and report invalid paths, missing repositories, and unavailable remote data clearly.
- Check README and `.gitignore` presence and warn about obvious README placeholder text.
- Summarize recent commits for both repository types.
- Report uncommitted changes and untracked files for local repositories; show `N/A` for remote working-tree checks.
- Flag potentially sensitive tracked filenames without printing their contents.
- Display actionable `PASS`, `WARN`, `FAIL`, and `N/A` results in the terminal and optionally export Markdown.

The tool will audit repositories without changing their files, commits, or settings.
Missing remote data must be reported as unavailable rather than treated as a passing check.

## Planned usage

These examples describe the intended interface and are not runnable yet:

```bash
# Audit one local Git repository
./repoready.sh /path/to/project

# Audit one public GitHub repository without cloning it
./repoready.sh --github michal-matusik/RepoReady

# Save an audit report
./repoready.sh --github michal-matusik/RepoReady --output report.md
```

## Planned tech stack

| Tool | Intended role |
| --- | --- |
| Bash 3.2+ | Command-line interface and audit orchestration, targeting macOS and Linux |
| Git | Local repository validation, tracked file listing, status, and commit history |
| GitHub CLI (`gh`) and GitHub REST API | Read public repository metadata, files, and commit history |
| `jq` | Parse JSON responses |
| Standard Unix utilities | Process text and format results |
| ShellCheck and Bats | Check Bash quality and automate tests |
| Markdown | Documentation and exported audit reports |

No database is planned.
Local audits will work offline; remote audits will require network access and will handle API rate limits and access errors.
Private repository auditing is outside the MVP, even if GitHub CLI credentials can access private repositories.

## Repository structure

```text
README.md                Project overview and intended interface
Eisenhower Matrix.md     Prioritized feature scope
lib/                     Reserved for future Bash helpers
tests/                  Reserved for future automated tests
docs/                   Development plan and submission checklist
```

The future root entry point will be `repoready.sh`.
The `lib/` and `tests/` directories currently contain documentation only.

## Development plan

1. Repository setup - Create the repository, README, matrix, and student-drawn diagram.
2. CLI input - Accept local paths or public GitHub repositories.
3. Local analysis - Retrieve local Git data and files.
4. GitHub integration - Fetch remote repository data through the API.
5. Documentation checks - Check README, `.gitignore`, and placeholders.
6. Git analysis - Check commit history and local changes.
7. Security checks - Detect potentially sensitive filenames.
8. Report generation - Display results and export Markdown.
9. Testing - Test functionality and handle errors.
10. Final polish - Improve documentation and usability.

Each milestone should produce a meaningful commit as the student builds the project.
See the [development plan](docs/development-plan.md) for acceptance criteria.

## Future plans

- Audit multiple repositories or all public repositories in an account.
- Support explicitly authorized private repository audits.
- Check README relative links and referenced files.
- Run scheduled audits and integrate GitHub Actions.
- Compare reports over time.

These features are scheduled for V2 or later, after the single-repository MVP works end to end.

## Planning and course deliverables

- [Eisenhower Matrix](Eisenhower%20Matrix.md)
- [Development plan](docs/development-plan.md)
- [Homework 9 submission checklist](docs/submission-checklist.md)

The System Diagram is pending student work and has no file or image link yet.
The instructor requires the Eisenhower Matrix and System Diagram to be clearly named files at the repository root, on the default branch, in its latest commit snapshot.
The diagram must be drawn by the student in draw.io, Lucidchart, or a comparable tool.

## Limitations

Filename warnings are a basic hygiene check, not a guarantee that a repository contains no secrets.
The MVP will not scan file contents for credentials or perform a comprehensive vulnerability audit.
Placeholder warnings may need manual review, and remote repositories cannot reveal local uncommitted changes.
