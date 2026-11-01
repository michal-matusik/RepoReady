# RepoReady

A Bash command-line tool planned for Purdue CS 193, Fall 2026.
Status: project setup and planning; the application is not implemented yet.

## Project goal

Help developers check whether a local Git repository or remote public GitHub repository is documented, organized, and ready to share.
RepoReady will combine common maintenance checks into one actionable report without requiring a clone for remote audits.

## MVP scope

- Accept and validate one local repository path or public GitHub repository.
- Check README and `.gitignore` presence and obvious README placeholder text.
- Summarize recent commits in both modes.
- Report uncommitted changes and untracked files locally; show `N/A` for remote working-tree checks.
- Flag potentially sensitive tracked filenames without printing file contents.
- Display `PASS`, `WARN`, `FAIL`, and `N/A` findings, with optional Markdown export.
- Handle invalid inputs, network failures, and API errors clearly.

Audits will leave the target repository unchanged.
Filename warnings are basic hygiene checks, not a comprehensive security scan.

## Planned usage

These commands describe the intended interface and are not runnable yet:

```bash
./repoready.sh /path/to/project
./repoready.sh --github michal-matusik/RepoReady
./repoready.sh --github michal-matusik/RepoReady --output report.md
```

## Tech stack

- Bash 3.2+ and standard Unix utilities.
- Git for local repository data.
- GitHub CLI (`gh`), GitHub REST API, and `jq` for public remote repository data.
- ShellCheck and Bats for code quality and testing.
- Markdown for documentation and exported reports.

No database is planned.
Local audits will work offline; remote audits will require network access.

## Future plans

- Audit multiple repositories or all public repositories in an account.
- Support explicitly authorized private repository audits.
- Check README relative links and referenced files.
- Integrate GitHub Actions and scheduled audits.
- Compare saved reports over time.
