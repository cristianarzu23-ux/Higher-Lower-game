<!--
MAINTAINER NOTE:
This filename intentionally contains a Cyrillic capital IE: Е (U+0415)
instead of the ASCII capital E: E (U+0045).

It is visually similar to README.md, but GitHub does not treat it as the
special .github/README.md file that would override the repository-root README.

Do not "correct" the filename unless this behavior is no longer desired.
-->

# About the `.github` Folder

> [!IMPORTANT]
> Do **not** modify or delete the `.github/` folder or any files in it. This folder is for repository administration and automated checks. It is not a graded Module Four deliverable.

## What Is Here?

This repository uses `.github/` for GitHub-specific configuration and maintenance files:

* `ISSUE_TEMPLATE/` — forms for reporting a repository problem or requesting an improvement
* `ci/README.md` — guide to student and course continuous-integration behavior
* `ci/check_repository.py` — repository, documentation, and assignment-artifact checks
* `ci/check_starter.py` — validates the intended course starter state
* `ci/check_readme_commands.py` — validates documented Bash commands across supported shells
* `workflows/tests.yml` — active **IT 140 Checks** workflow
* `workflows/readme-commands.yml` — Linux/Bash, macOS/zsh, and Windows/Git Bash README-command checks
* `workflows/external-links.yml` — external-link validation for course documentation
* `social-preview.png` — repository social-preview image

The former `workflows/tests.yml.disabled` file is no longer part of the repository. Optional Python practice remains optional and is documented in the assignment files rather than maintained as a second disabled workflow.

## Automated Checks

### Personal Student Repositories

The student-facing **Assignment artifact check** provides limited formative feedback about repository integrity and the one graded Module Four pseudocode file.

A new personal repository is not treated as a failure simply because the pseudocode is still in its starter state. Once graded work changes, the check can report remaining starter TODOs, damaged required structure, or changes to protected course files.

The optional Python program and optional practice tests are not student CI requirements. The provided Draw.io file remains a course reference, not a graded deliverable.

### Public Course Repository

The public `GC-STEM/it140-m4-assignment` repository receives deeper maintainer checks for the starter package, Markdown structure and local links, Python support files, social preview, README commands, and external links.

See the [CI Guide](ci/README.md) for details.

## Issue or Assignment Question?

Use [GitHub Issues](https://github.com/GC-STEM/it140-m4-assignment/issues) for a technical problem with this repository, its starter files, documentation, or automated checks.

Use [GitHub Discussions](https://github.com/GC-STEM/it140-m4-assignment/discussions) for questions about using the repository that do not request or post a completed graded solution.

For Codio Virtual Desktop performance, access, or outage problems, contact the **IT Service Desk** from the main menu bar in D2L Brightspace. For course IDE setup or lifecycle-script problems, use the Module One setup support resources.

Questions about assignment requirements, grading, submissions, deadlines, accommodations, or instructor feedback belong with the instructor in D2L Brightspace.
