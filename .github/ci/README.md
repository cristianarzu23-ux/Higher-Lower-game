<!-- To see this file in a clean, formatted view, select ▼ in the upper-right corner of the editor pane, then select "Markdown Preview". -->

# IT 140 Module Four Assignment | GitHub Continuous Integration Guide

This guide explains the GitHub Actions checks used in the Module Four assignment repository.

> [!IMPORTANT]
> **GitHub continuous integration (CI) provides feedback. It does not grade or submit the assignment.** Students submit the required file in **D2L Brightspace**, and the D2L assignment rubric determines the grade.

## About CI

**Continuous integration (CI)** is automated checking that runs after repository changes are saved to GitHub. GitHub Actions provides the CI for this repository.

The Module Four repository separates two purposes:

* **Student CI** gives formative feedback about the current state of the graded pseudocode and protected repository files.
* **Course-repository CI** protects the public assignment template, documentation, starter artifacts, command instructions, and supporting files.

| Term | Meaning |
| --- | --- |
| **course repository** | `GC-STEM/it140-m4-assignment`, the public starter repository maintained for the course |
| **personal repository** | The private repository a student creates from the course template |
| **workflow** | Instructions in `.github/workflows/` that tell GitHub Actions what to run |
| **Assignment artifact check** | The student-facing job that checks repository integrity and graded-pseudocode state |
| **Course repository check** | The maintainer-facing job that validates the public assignment package |
| **README command checks** | Cross-platform checks for Bash command blocks in README files |

## Student CI

The student-facing **Assignment artifact check** focuses on the Module Four repository and the one graded file:

`design/hilow_game.pseudo`

It can check that:

* required course files remain present;
* committed changes stay within the student-editable file set;
* the provided Draw.io reference remains readable XML;
* pseudocode retains its required `START` / `END` structure;
* changed pseudocode no longer contains starter `TODO:` prompts; and
* once graded work begins, the graded pseudocode differs from the starter state.

The optional `src/hilow_game.py` program and optional practice tests are **not required by student CI** and do not determine the Module Four assignment-check result.

### Fresh Personal Repositories Are Neutral

The graded pseudocode intentionally begins in a starter state. Creating a personal repository is not a student error.

A brand-new personal repository with no committed graded-pseudocode change should therefore not fail simply because the assignment has not been started yet.

After the student changes the graded pseudocode, CI can report remaining starter TODO prompts, damaged required structure, or protected-file changes. That is development feedback, not a grade.

### How Students Should Use CI Feedback

> **Work → Save locally → Commit → Push → Review CI → Improve**

To review feedback:

1. Open the personal `it140-m4-assignment` repository on GitHub.
2. Select **Actions**.
3. Open the most recent **IT 140 Checks** workflow run.
4. Open **Assignment artifact check**.
5. Read the summary and first failing step, if any.

A green result means the automated checks passed for the repository state they inspect. It does **not** mean the pseudocode satisfies every rubric criterion, and it does not submit the assignment.

## When Something Fails

After graded work begins, a failed student check may indicate:

* starter `TODO:` prompts remain in the changed pseudocode;
* the required `START` / `END` structure was damaged;
* a protected course file was modified, deleted, renamed, or added unexpectedly; or
* a provided repository artifact is damaged.

Read the first error, correct that problem, commit and push the correction, and review the new run.

A repository or CI problem is more likely when a newly created personal repository fails before graded work changes, GitHub Actions fails during checkout/setup, the feedback clearly does not match the files stored on GitHub, or several students report the same infrastructure failure.

Use the support routing in the root [README](../../README.md). Do not post completed graded work, credentials, tokens, or private identifying information in public GitHub Issues or Discussions.

## Faculty Guidance

CI is **formative feedback**, not grading automation.

When helping a student:

* use the workflow summary to distinguish repository-integrity problems from pseudocode structure/TODO-state problems;
* remember that the provided Draw.io file is a reference, not a graded Module Four deliverable;
* remember that optional Python practice is outside the graded Module Four CI scope;
* use the official D2L Guidelines and Rubric for grading; and
* treat a green workflow as only one development signal, not proof of assignment completeness or quality.

If many students encounter the same GitHub Actions setup failure, investigate a repository or platform problem before assuming identical student errors.

## Course Repository CI

### Course Repository Check

[`tests.yml`](../workflows/tests.yml) runs a separate **Course repository check** in `GC-STEM/it140-m4-assignment`.

The course job validates areas such as:

* required files and stable Markdown sections;
* local Markdown links;
* JSON and TOML configuration;
* the graded pseudocode starter and provided Draw.io reference;
* the repository social-preview image;
* course-managed Python syntax and Ruff checks; and
* the intentionally incomplete starter state through [`check_starter.py`](./check_starter.py).

[`check_repository.py`](./check_repository.py) contains repository and artifact checks used by both course and personal repositories. Student mode changes only student-facing completion behavior; it does not weaken protection of course-managed files.

### README Command Checks

[`readme-commands.yml`](../workflows/readme-commands.yml) runs only in the public course repository and validates README command blocks on Linux/Bash, macOS/zsh, and Windows/Git Bash.

[`check_readme_commands.py`](./check_readme_commands.py) checks every fenced `bash`, `sh`, or `shell` block for syntax and cross-platform policy violations. It also smoke-tests selected procedural blocks marked with comments such as:

```text
<!-- ci:command-test id=open-existing-repo fixture=existing-repo expect=repo -->
```

The smoke tests use disposable directories and harmless command shims. The checker rejects Command Prompt or PowerShell syntax inside Bash blocks, Windows drive paths, backslashes with `~` or `$HOME`, and `code ~/Repos/...` instead of `cd ...` followed by `code .`.

### External Link Checks

[`external-links.yml`](../workflows/external-links.yml) protects external links in course-managed Markdown. External sites can fail temporarily, so confirm a link is actually stale before replacing it.

## Maintainer Guidance

When course CI fails, fix the cause rather than weakening the check merely to make the workflow green. Confirm whether the change intentionally altered a required file, stable section marker, student-editable path, starter artifact, or command sequence.

To run the README checker locally when Bash is available:

```bash
python3 .github/ci/check_readme_commands.py --shell bash --platform linux
```

Preserve this student CI lifecycle:

1. **Untouched personal starter:** neutral; no failure solely because work has not started.
2. **Graded pseudocode changes:** structural or remaining-starter problems may produce formative failures.
3. **Changed pseudocode passes structural checks:** student CI can be green.
4. **At every state:** green is not a grade or submission.

Do not add the optional Python program or optional practice tests as student requirements unless the assignment requirements themselves change.

## Summary

* Student CI gives limited formative feedback about repository integrity and the one graded pseudocode deliverable.
* A new personal repository is not treated as a failure simply because the graded starter file is untouched.
* Optional Python work remains optional and outside the student CI requirement.
* The provided Draw.io file remains a course reference, not a graded deliverable.
* Course CI protects the template, starter artifacts, documentation, commands, and configuration.
* README commands are checked on Linux/Bash, macOS/zsh, and Windows/Git Bash.
* D2L Brightspace remains the assignment submission and grading system.
