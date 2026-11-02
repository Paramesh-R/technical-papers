# GIT BASICS – CHEAT SHEET

## 1. Important Git Terminologies

| Term              | Explanation                                                 |
| ----------------- | ----------------------------------------------------------- |
| Repository (Repo) | A collection of project files and their version history.    |
| Commit            | A snapshot of changes saved in Git history.                 |
| Branch            | An independent line of development.                         |
| HEAD              | A pointer to the current commit/position in the repository. |
| Master/Main       | The primary branch of a repository.                         |
| Staging Area      | An area where changes are prepared before committing.       |
| Working Directory | The location where you create, modify and delete files.     |
| SHA-1             | A hash used to identify Git objects and commits.            |

## 2. Git Workflow

Git has three important areas:

1. Working Directory
2. Staging Area (Index)
3. Local Repository (Commit Area)

**Workflow:**

Working Directory → Staging Area → Local Repository

- Working Directory: Make changes to files.
- Staging Area: Select changes that should be included in the next commit.
- Local Repository: Save staged changes using a commit.

## 3. Git Installation

Check whether Git is installed:

```bash
git --version
```

Install Git on Ubuntu:

```bash
sudo apt update
sudo apt install git
```

## 4. Git Configuration

Configure your username:

```bash
git config --global user.name "Your Name"
```

Configure your email:

```bash
git config --global user.email "you@example.com"
```

View all configurations:

```bash
git config --list
```

Open Git configuration file:

```bash
nano ~/.gitconfig
```

Configuration file location:

```bash
~/.gitconfig
```

## 5. Essential Git Commands

### Repository Initialization

| Command         | Purpose                              |
| --------------- | ------------------------------------ |
| `git init`      | Initialize a new Git repository.     |
| `git clone URL` | Clone an existing repository.        |
| `git status`    | Check the current repository status. |

### Staging and Committing

| Command                   | Purpose                                 |
| ------------------------- | --------------------------------------- |
| `git add filename`        | Add a specific file to staging.         |
| `git add .`               | Stage changes in the current directory. |
| `git add -A`              | Stage all changes in the repository.    |
| `git commit -m "message"` | Create a commit with a message.         |
| `git log`                 | Display commit history.                 |
| `git log --oneline`       | Display compact commit history.         |

## 6. Git Branches

A branch allows developers to work on different features independently.

List branches:

```bash
git branch
```

Create a branch:

```bash
git branch leaf
```

Switch to a branch:

```bash
git switch leaf
```

Create and switch to a new branch:

```bash
git switch -c leaf
```

Merge a branch into the current branch:

```bash
git merge leaf
```

Delete a branch:

```bash
git branch -d leaf
```

## 7. GitHub vs GitLab

| GitHub                                     | GitLab                                                       |
| ------------------------------------------ | ------------------------------------------------------------ |
| Platform built around Git.                 | Platform built around Git.                                   |
| Widely used for open-source collaboration. | Commonly used for software development and DevOps workflows. |
| Hosts Git repositories.                    | Hosts Git repositories.                                      |

**Remember:** Git is the version control system. GitHub and GitLab are platforms that host Git repositories and provide collaboration features.

## 8. Git Best Practices

1. **Use .gitignore**
   - Specify files and directories that Git should ignore.
   - Examples: virtual environments, cache files and temporary files.

2. **Write meaningful commit messages**
   - Clearly describe what was changed.
   - Example: `Add CSV file validation`.

3. **Make small commits**
   - Break large tasks into smaller units.
   - Each commit should represent a logical change.

4. **Commit frequently**
   - Don't wait until the end of the day.
   - Maintain a useful project history.

5. **Commit working code**
   - Avoid commits that break existing functionality.

6. **Review changes before committing**
   - Use `git diff` to inspect changes.
   - Remove unnecessary debugging statements.

7. **Always test your code**
   - Test new changes.
   - Check whether existing functionality is affected.

8. **Never commit secrets**
   - Never commit passwords, API keys, tokens or other sensitive credentials.

## 9. .gitignore

`.gitignore` is a file that specifies which untracked files and directories Git should ignore.

Example:

```gitignore
__pycache__/
*.pyc
.env
venv/
.idea/
```

## 10. Sample Git Practice

**Task:** Initialize a repository, create files, make commits, create a branch and merge it.

```bash
# Initialize repository
git init

# Create a file
touch a.txt

# Stage and commit
git add a.txt
git commit -m "Add a.txt"

# Create a new branch
git branch leaf

# Switch to the new branch
git switch leaf

# Create another file
touch b.txt

# Stage and commit
git add b.txt
git commit -m "Add b.txt"

# Switch back to main branch
git switch master

# Merge leaf into master
git merge leaf
```

Note: If your initial branch is named `main`, use `main` instead of `master`.
