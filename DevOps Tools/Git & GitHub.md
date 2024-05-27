
## Basic Concepts

- **Repository (Repo)**: A directory that contains all of your project's files and the revision history of each file.
- **Commit**: A snapshot of changes made to the repository.
- **Branch**: A parallel version of your repository, used to develop features independently from other work.
- **Merge**: Combining changes from different branches.
- **Pull Request (PR)**: A method of submitting contributions to a project.
- **Clone**: A copy of a repository that is stored on your local machine.
- **Fork**: A personal copy of someone else's project.

## Git Configuration

### Global Configuration
```
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Check Configuration
```
git config --list
```

# Basic Commands

## Initialize a New Repository
```
git init
```

## Clone a Repository
```
git clone https://github.com/user/repo.git
```

## Check Repository Status
```
git status
```

## Add Files to Staging Area
```
git add <file>
# Example:
git add README.md

# Add all files
git add .
```

## Commit Changes
```
git commit -m "Commit message"
```

## View Commit History
```
git log
```

# Branching and Merging

## Create a New Branch
```
git branch <branch_name>
# Example:
git branch feature-branch
```

## List Branches
```
git branch
```

## Switch to a Branch
```
git checkout <branch_name>
# Example:
git checkout feature-branch
```

## Create and Switch to a New Branch
```
git checkout -b <branch_name>
# Example:
git checkout -b feature-branch
```

## Merge a Branch
```
git checkout main
git merge <branch_name>
# Example:
git merge feature-branch
```

## Delete a Branch
```
git branch -d <branch_name>
# Example:
git branch -d feature-branch
```

# Remote Repositories

## Add a Remote Repository
```
git remote add origin https://github.com/user/repo.git
```

## View Remote Repositories
```
git remote -v
```

## Push Changes to Remote Repository
```
git push origin <branch_name>
# Example:
git push origin main
```

## Pull Changes from Remote Repository
```
git pull origin <branch_name>
# Example:
git pull origin main
```

## Fetch Changes from Remote Repository
```
git fetch
```

## Remove a Remote Repository
```
git remote remove <remote_name>
# Example:
git remote remove origin
```

# GitHub Workflow

## Fork a Repository
1. Go to the repository on GitHub.
2. Click the Fork button on the top right.

## Create a Pull Request
1. Commit and push your changes to your fork.
2. Go to the original repository on GitHub.
3. Click the New Pull Request button.
4. Select your fork and branch as the source.
5. Fill out the PR template and click Create Pull Request.

## Syncing a Fork
```
# Add the upstream repository
git remote add upstream https://github.com/original_owner/repo.git

# Fetch the latest changes from upstream
git fetch upstream

# Checkout your main branch
git checkout main

# Merge the changes from upstream into your main branch
git merge upstream/main
```

# Stashing Changes

## Save Changes to Stash
```
git stash
```

## List Stashed Changes
```
git stash list
```

## Apply Stashed Changes
```
git stash apply
```

## Drop Stashed Changes
```
git stash drop
```

# Tagging

## Create a Tag
```
git tag -a v1.0 -m "Version 1.0"
```

## List Tags
```
git tag
```

## Push Tags to Remote
```
git push origin --tags
```

## Delete a Tag
```
git tag -d <tag_name>
# Example:
git tag -d v1.0
```

# Undoing Changes

## Amend the Last Commit
```
git commit --amend -m "New commit message"
```

## Unstage a File
```
git reset <file>
# Example:
git reset README.md
```

## Revert a Commit
```
git revert <commit_hash>
# Example:
git revert abc1234
```

## Reset to a Previous Commit
```
git reset --hard <commit_hash>
# Example:
git reset --hard abc1234
```

# Ignoring Files

## Create a .gitignore File
```
# Example .gitignore file
*.log
node_modules/
dist/
```

# Git Aliases

## Create Aliases
```
git config --global alias.st status
git config --global alias.ci commit
git config --global alias.co checkout
git config --global alias.br branch
```

# Resources

[Git Documentation](https://docs.github.com/en)

This cheat sheet provides a comprehensive overview of Git and GitHub, covering basic concepts, commands, branching, merging, remote repositories, GitHub workflow, stashing, tagging, undoing changes, ignoring files, and aliases.
