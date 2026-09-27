<!-- To see this file in a clean, formatted view, select ▼ in the upper-right corner of the editor pane, then select "Markdown Preview". -->

# IT 140 Module Four Assignment | Pseudocode Revisited

---

> [!IMPORTANT]
>
> * 🚫 **Fork** — Do NOT fork this repo!!! Instead, follow the instructions below.
> * 🚫 **Use this template** — Do NOT click the green *Use the template* button!!! Instead, follow the instructions below.
> * ⭐ **Star** — Click to bookmark this repo, if desired.
> * 👁️ **Watch** — Click to receive notices of repo changes, if desired.
>   * **Students:** Not recommended. Watching generates unnecessary notifications.
>   * **Faculty:** Consider selecting **Watch → Custom → Releases + Issues** to receive major repository updates and follow reported issues.

---

> [!NOTE]
> **🆕 New for 2026 C-5:** IT 140 now uses GitHub repositories to provide assignment starter files, development resources, and supporting documentation.
>
> If you have a question, check [GitHub Discussions](https://github.com/GC-STEM/it140-m4-assignment/discussions) to see whether it has already been answered or ask a new question.
>
> If you find a problem with this GitHub repository or its instructions, or have a suggestion for improvement, please open [GitHub Issues](https://github.com/GC-STEM/it140-m4-assignment/issues) to review existing issues or create a new issue.

---

* **Course**: IT 140 - *Introduction to Scripting*
* **Task Title**: 4-3: Pseudocode Revisited
* **Task Type**: Required, graded, one submission required
* **Repository Version**: 1.0.4
* **Repository Version DTG**: 2026-09-07-14-30
* **Design Problem**: Higher/Lower Game
* **Graded Deliverable**:
  * [`design/hilow_game.pseudo`](design/hilow_game.pseudo)

**Required assignment progress:** **0 Start Here** → [1 Analyze](analysis/README.md) → [2 Design](design/README.md) → [3 Submit](#3-submit-your-assignment)

**Optional SDLC practice:** [Construct](src/README.md) → [Test](tests/README.md)

> [!IMPORTANT]
> The **Module Four Assignment Guidelines and Rubric in D2L Brightspace** is the official source for assignment requirements, grading criteria, and submission requirements. This repository provides starter files, reference documents, and step-by-step guidance to help you complete those requirements.

## What You Are Doing in Module Four

Module Four continues the design-before-code work from Module Three and adds **loops** to the input/output and decision-branching concepts you have already practiced.

You will design pseudocode for a Higher/Lower Game. The game must:

* obtain and validate lower and upper bounds;
* generate a random number between those bounds;
* obtain and validate guesses;
* distinguish guesses that are too low, too high, or correct; and
* repeat until the correct number is guessed.

The repository also includes optional Python construction and testing practice so you can continue through the complete simplified Software Development Life Cycle (SDLC):

> **Analyze → Design → Construct → Test**

For the graded Module Four assignment, however, your required path is:

> **Analyze → Design → Submit**

Construct and Test are optional practice and do not add graded deliverables.

## What You May Edit

### Graded and submitted

Edit and submit:

* [`design/hilow_game.pseudo`](design/hilow_game.pseudo) — graded pseudocode

### Working notes; not submitted

You may also edit:

* [`hilow_game_sdw.md`](hilow_game_sdw.md) — Software Development Worksheet (SDW) working notes

The SDW is a learning aid. It is not a graded deliverable unless your instructor specifically tells you otherwise.

### Optional practice; not submitted

After your graded pseudocode is complete, you may edit:

* [`src/hilow_game.py`](src/hilow_game.py) — optional Python construction practice

The provided test file is a practice tool. Do not edit it to make a test pass.

### Course-provided reference and support files

Do not edit the SRS, SDD, Draw.io file, README files, tests, `.github` files, repository configuration, or other course-managed files. They provide requirements, guidance, examples, checks, or configuration.

> [!NOTE]
> `design/hilow_game.drawio` is a course-provided reference file. The Module Four assignment does **not** require a flowchart submission.

## 0. Meet the Prerequisites

Before starting this assignment:

* [ ] Complete the GitHub and Course IDE portions of the [Module One Setup Tasks](https://github.com/GC-STEM/it140-m1-setup-tasks).
* [ ] Complete the assigned Module Four zyBooks activities before relying on the assignment to teach loops from the beginning.
* [ ] Open the **Module Four Assignment Guidelines and Rubric** and the **Higher/Lower Game Sample Output** in D2L Brightspace before editing the starter file.

Relevant Module Four zyBooks topics include:

* **4.1 Loops (general)**
* **4.2 While loops**
* **4.3 More while examples**
* **4.7 While vs. for loops**
* **4.9 Developing programs incrementally**

Earlier topics on input/output, `if`/`elif`/`else`, relational operators, Boolean expressions, and indentation also apply.

## 1. Set Up or Open Your Assignment Repository

You create your personal `it140-m4-assignment` repository only once.

> [!IMPORTANT]
> **Windows users:** Run all `bash` command blocks in this README in a **Git Bash** terminal. Do not use PowerShell or Command Prompt for these command blocks.

### If You Have Not Created It Yet

Use the VS Code integrated terminal. First confirm the GitHub account you use for IT 140:

```bash
gh auth status
```

If the correct account is not active, use the GitHub CLI sign-in or account-switching instructions from the Module One Setup Tasks before continuing.

Then run:

<!-- ci:command-test id=setup-personal-repo fixture=empty-repos expect=repo -->
```bash
cd ~/Repos
gh auth setup-git
gh api --method PUT user/starred/GC-STEM/it140-m4-assignment
gh repo create it140-m4-assignment --template GC-STEM/it140-m4-assignment --private --clone
cd it140-m4-assignment
git remote -v
```

Confirm that the final remote belongs to **your GitHub account**.

> [!NOTE]
> These creation commands are for the first successful setup only. If a personal repository or local folder already exists, open that existing work instead of creating another repository.

### If You Already Created It on This Device

Open the existing local clone from a terminal:

<!-- ci:command-test id=open-existing-repo fixture=existing-repo expect=repo -->
```bash
cd ~/Repos/it140-m4-assignment
code .
```

*Reminder*. In terminal commands, **`~`** means your home folder, and **`.`** means the current working directory. `code .` opens the current folder in VS Code.

>*Note*
> If VS Code opens in Restricted Mode, your `~/Repos` folder should already be trusted if you completed the Module One course IDE setup. Normally, you will not see this warning.
>
> If you see the **Restricted Mode** warning bar:
>
> ![Restricted Mode warning bar in VS Code](https://raw.githubusercontent.com/GC-STEM/it140-m2-assignment/main/.github/assets/22_vscode_restricted_mode_bar.png)
>
> 1. Click **Manage** on the **Restricted Mode** warning bar.
> 2. In **Workspace Trust**, find **Trusted Folders & Workspaces**.
> 3. Use the control in that section to add a trusted folder.
> 4. In the folder selection window, go to your home folder and select the entire **Repos** folder.
> 5. Confirm the folder selection and trust it when prompted.
> 6. Verify that your **Repos** folder appears under **Trusted Folders & Workspaces**.
>
> Trust the entire `~/Repos` folder rather than only `it140-m4-assignment`. VS Code applies trust to all subfolders of a trusted parent folder, including this assignment repository.

### Understand the Related Copies

Your Module Four assignment normally has three related copies:

* **Public course template on GitHub:** `GC-STEM/it140-m4-assignment`. This is the course-provided starting point. Do not fork or edit this copy.
* **Your personal GitHub repository:** `it140-m4-assignment` in your own GitHub account. This stores work you push to GitHub.
* **A local clone on a device:** Usually `~/Repos/it140-m4-assignment`. This is the copy you open in VS Code and edit.

The setup command creates the personal GitHub repository and then creates its local clone on the device where you run the command.

### If Your Personal Repository Exists but This Device Does Not Have a Local Clone

Clone your existing personal repository rather than creating a new one:

<!-- ci:command-test id=clone-existing-repo fixture=empty-repos expect=repo -->
```bash
cd ~/Repos
gh repo clone "$(gh api user --jq .login)/it140-m4-assignment"
cd it140-m4-assignment
git status
```

### If You Work on More Than One Device

Using one device for an assignment is the simplest and safest approach. If you must switch devices, synchronize your work before and after the switch.

Before leaving the device where you have been working:

<!-- ci:command-test id=sync-before-switch fixture=existing-repo expect=repo -->
```bash
cd ~/Repos/it140-m4-assignment
git status
git add hilow_game_sdw.md design/hilow_game.pseudo src/hilow_game.py
git commit -m "Save Module Four assignment progress"
git push
```

On the other device, before editing any file:

<!-- ci:command-test id=sync-after-switch fixture=existing-repo expect=repo -->
```bash
cd ~/Repos/it140-m4-assignment
git pull --ff-only
git status
```

> [!WARNING]
> If `git pull --ff-only` or `git push` reports an error or says the histories cannot be fast-forwarded, **stop and do not make more changes on either device** until you get help. Do not try random merge or reset commands.

## 2. Complete the Assignment

### 2.1 Analyze the Requirements

Open [Analyze Phase](analysis/README.md).

During Analyze, focus on **what** the Higher/Lower Game must do. Use:

* the official Guidelines and Rubric in D2L Brightspace;
* the official Higher/Lower Game Sample Output;
* the provided [Software Requirements Specification (SRS)](analysis/hilow_game_srs.md); and
* the optional [Software Development Worksheet (SDW)](hilow_game_sdw.md).

Pay particular attention to **what repeats** and **what stops each repetition**. The assignment requires validation for both the selected bounds and the player's guesses.

### 2.2 Create the Graded Pseudocode

Open [Design Phase](design/README.md).

Complete:

* [`design/hilow_game.pseudo`](design/hilow_game.pseudo)

Your pseudocode should logically outline the required game, identify inputs and outputs, and use decision branching and loops to control program flow.

The rubric weights are:

* **Logical Steps — 35%**
* **Input/Output — 30%**
* **Program Flow — 35%**

Review the completed pseudocode against the current Guidelines and Rubric before submission.

### 2.3 Save Your Work to GitHub

Save your files normally while you work in VS Code. Periodically commit and push your assignment work so your personal GitHub repository contains a current backup.

<!-- ci:command-test id=save-progress fixture=existing-repo expect=repo -->
```bash
cd ~/Repos/it140-m4-assignment
git status
git add hilow_game_sdw.md design/hilow_game.pseudo src/hilow_game.py
git commit -m "Save Module Four assignment progress"
git push
```

These commands:

* `git status` shows the current state of your local repository.
* `git add` prepares only your student-editable Module Four files to be saved.
* `git commit` saves a snapshot of those files in your local Git repository.
* `git push` uploads that commit to your personal GitHub repository.

---

> [!NOTE]
> If Git reports `nothing to commit, working tree clean`, your current files have already been committed. The `git push` command will still check whether your personal GitHub repository is up to date.  

---

> [!IMPORTANT]
> **Saving your work to GitHub does not submit your assignment.** Assignment submission, grading, and instructor feedback remain in D2L Brightspace.

---

### 2.4 Review the Assignment Checks

Each push to your personal repository runs the **IT 140 Checks** workflow.

A newly created personal repository should **not** fail merely because the graded pseudocode is still the untouched starter file. Once you begin changing the graded pseudocode, the checks provide formative feedback about the current repository state.

The assignment artifact check can verify basic conditions such as:

* required course files are still present;
* committed changes are limited to student-editable files;
* after graded work begins, the graded pseudocode differs from the starter state;
* the pseudocode retains its outer `START` / `END` structure;
* changed pseudocode no longer contains starter `TODO:` prompts; and
* course-provided Markdown and configuration remain internally consistent.

The checks also verify that the provided Draw.io reference remains readable, but the Draw.io file is **not** a graded Module Four deliverable.

The optional Python construction file and optional practice tests are **not required by the student assignment artifact check**.

The checks **do not grade the quality or correctness of your pseudocode**. A green check is not a grade and does not submit your assignment.

To review a run:

1. Open your personal repository on GitHub.
2. Select **Actions**.
3. Open the most recent **IT 140 Checks** run.
4. Open **Assignment artifact check** and review the summary.

## 3. Submit Your Assignment

In D2L Brightspace, open the **Module Four Assignment** and follow the current submission instructions.

Submit exactly the graded design file required by the assignment:

* [`design/hilow_game.pseudo`](design/hilow_game.pseudo)

Do **not** submit the SDW, Draw.io reference, optional Python practice file, test file, GitHub Actions output, SRS, SDD, or repository README files unless your instructor specifically requests them.

## Optional: Continue Through Construct and Test

After the graded pseudocode is complete and ready to submit, you may continue through the remaining SDLC phases for practice:

1. [Construct](src/README.md) — translate your own pseudocode into a small Python program.
2. [Test](tests/README.md) — manually test the program and optionally run the provided practice tests.

Optional practice is intended to help you connect design to implementation before the larger course projects. It does not change the one-file Module Four submission.

## Restore or Restart Your Assignment Repository

Choose the recovery method that matches the problem. Preserve existing work whenever possible.

> [!IMPORTANT]
> **Windows users:** Run the `bash` command blocks in this section in **Git Bash**, not PowerShell or Command Prompt.

### Restore a Damaged Local Copy From GitHub

Use this when the copy you previously pushed to GitHub is good but the local folder is damaged or confusing.

<!-- ci:command-test id=restore-local-copy fixture=existing-repo expect=repo -->
```bash
cd ~/Repos
mv it140-m4-assignment "it140-m4-assignment-local-backup-$(date +%Y%m%d-%H%M%S)"
gh repo clone "$(gh api user --jq .login)/it140-m4-assignment"
cd it140-m4-assignment
git status
```

### Start Over From the Current Course Template

Use this only when you intentionally want a fresh assignment copy. Preserve the old local folder and GitHub repository first.

<!-- ci:command-test id=restart-from-template fixture=existing-repo expect=repo -->
```bash
cd ~/Repos
backup="it140-m4-assignment-backup-$(date +%Y%m%d-%H%M%S)"
mv it140-m4-assignment "$backup"
gh repo rename "$backup" --repo "$(gh api user --jq .login)/it140-m4-assignment" --yes
gh repo create it140-m4-assignment --template GC-STEM/it140-m4-assignment --private --clone
cd it140-m4-assignment
git remote -v
```

> [!IMPORTANT]
> Starting over does not automatically copy work from the preserved repository into the new one.

## Help and Support

Use the [Module Four Assignment Wiki](https://github.com/GC-STEM/it140-m4-assignment/wiki) for supplemental explanations of the SDLC, assignment documents, pseudocode, loops, course IDE tools, Git/GitHub, testing, sources, and AI use.

* Use [GitHub Discussions](https://github.com/GC-STEM/it140-m4-assignment/discussions) for questions about using this repository that do not request a completed graded solution.
* Use [GitHub Issues](https://github.com/GC-STEM/it140-m4-assignment/issues) to report a technical problem with the provided repository, starter files, documentation, or automated checks.
* For **Codio Virtual Desktop performance, access, or outage problems**, contact the **IT Service Desk** using the link on the main menu bar in D2L Brightspace.
* For **course IDE setup or lifecycle-script problems**, see [Setup Problems and Support](https://github.com/GC-STEM/it140-m1-setup-tasks/wiki/Setup-Problems-and-Support).
* Contact your instructor through D2L Brightspace for assignment requirements, grading, feedback, deadlines, submissions, or course-specific questions.

Do not post your completed graded pseudocode publicly when asking for help.
