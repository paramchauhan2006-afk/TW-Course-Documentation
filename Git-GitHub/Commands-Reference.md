# Git Commands Reference Guide

Comprehensive reference for Git commands organized by category.

## Configuration Commands

```bash
# User Configuration
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

# View Configuration
git config --list
git config user.name
git config --global --list

# Editor Configuration
git config --global core.editor "code --wait"
git config --global core.editor "vim"

# Aliases
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph --all"

# Remove Configuration
git config --global --unset user.name
```

## Repository Commands

```bash
# Initialize Repository
git init
git init project-name

# Clone Repository
git clone <url>
git clone <url> <directory-name>
git clone -b <branch> <url>

# Clone with Depth (shallow clone)
git clone --depth 1 <url>
```

## Status and Information

```bash
# Status
git status
git status -s                 # Short format
git status -sb                # Short with branch info

# Log
git log
git log --oneline
git log --oneline --graph --all
git log -n 5                  # Last 5 commits
git log --since="2 weeks ago"
git log --author="Name"
git log --grep="keyword"
git log -p                    # Show patches
git log --stat                # Show statistics

# Show Specific Commit
git show <commit-hash>
git show HEAD
git show HEAD~2

# Blame (line-by-line history)
git blame <file>
```

## Staging and Committing

```bash
# Add Files to Staging
git add <file>
git add .                     # All files
git add *.txt                 # All txt files
git add src/                  # All files in directory

# Add with Patch Mode
git add -p                    # Interactive staging

# Remove from Staging
git reset HEAD <file>
git restore --staged <file>

# Commit
git commit -m "Message"
git commit                    # Opens editor
git commit -am "Message"      # Add and commit tracked files
git commit --amend            # Modify last commit
git commit --amend -m "New message"
```

## Branching

```bash
# List Branches
git branch                    # Local branches
git branch -a                 # All branches
git branch -r                 # Remote branches

# Create Branch
git branch <branch-name>
git branch <branch-name> <commit-hash>

# Switch Branch
git checkout <branch-name>
git switch <branch-name>

# Create and Switch
git checkout -b <branch-name>
git switch -c <branch-name>

# Rename Branch
git branch -m <old> <new>
git branch -m <new>           # Rename current

# Delete Branch
git branch -d <branch-name>
git branch -D <branch-name>   # Force delete

# Compare Branches
git diff <branch1>..<branch2>
git log <branch1>..<branch2>
```

## Merging

```bash
# Merge Branch
git merge <branch-name>
git merge --no-ff <branch>    # No fast-forward
git merge --squash <branch>   # Squash commits

# Abort Merge
git merge --abort

# Merge Tool
git mergetool
```

## Remote Operations

```bash
# Add Remote
git remote add <name> <url>
git remote add origin https://github.com/user/repo.git

# View Remotes
git remote
git remote -v

# Remove Remote
git remote remove <name>

# Rename Remote
git remote rename <old> <new>

# Show Remote Info
git remote show origin

# Fetch
git fetch
git fetch origin
git fetch origin <branch>

# Pull
git pull
git pull origin main
git pull --rebase             # Rebase instead of merge

# Push
git push
git push origin main
git push -u origin main       # Set upstream
git push --all                # All branches
git push --tags               # Push tags
git push origin --delete <branch>  # Delete remote branch

# Force Push (dangerous)
git push --force              # Never use on shared branches
git push --force-with-lease   # Safer alternative
```

## Undoing Changes

```bash
# Discard Working Directory Changes
git checkout -- <file>
git restore <file>

# Discard All Changes
git checkout .
git restore .

# Unstage Files
git reset HEAD <file>
git restore --staged <file>

# Reset Commits
git reset --soft HEAD~1       # Keep changes staged
git reset --mixed HEAD~1      # Keep changes unstaged
git reset --hard HEAD~1       # Discard changes
git reset --hard <commit>     # Reset to specific commit

# Revert Commit (safe, creates new commit)
git revert <commit-hash>
git revert HEAD
```

## Stashing

```bash
# Stash Changes
git stash
git stash save "Message"
git stash -u                  # Include untracked files

# List Stashes
git stash list

# Apply Stash
git stash apply               # Apply latest
git stash apply stash@{0}     # Apply specific
git stash pop                 # Apply and remove

# Show Stash Content
git stash show
git stash show -p

# Drop Stash
git stash drop stash@{0}

# Clear All Stashes
git stash clear
```

## Tagging

```bash
# List Tags
git tag
git tag -l "v1.*"             # Filter tags

# Create Lightweight Tag
git tag v1.0.0

# Create Annotated Tag
git tag -a v1.0.0 -m "Version 1.0.0"

# Tag Specific Commit
git tag -a v1.0.0 <commit> -m "Message"

# Show Tag
git show v1.0.0

# Push Tags
git push origin v1.0.0
git push origin --tags

# Delete Tag
git tag -d v1.0.0             # Local
git push origin --delete v1.0.0  # Remote
```

## Diff Commands

```bash
# Show Unstaged Changes
git diff

# Show Staged Changes
git diff --staged
git diff --cached

# Compare Commits
git diff <commit1> <commit2>

# Compare Branches
git diff <branch1>..<branch2>

# Diff Specific File
git diff <file>
git diff HEAD <file>

# Diff Statistics
git diff --stat
```

## Search Commands

```bash
# Search in Files
git grep "search-term"
git grep -n "search-term"     # Line numbers
git grep -c "search-term"     # Count

# Search in History
git log -S "search-term"      # Commits with term
git log --grep="search-term"  # Search commit messages
```

## Cleaning

```bash
# Show What Would Be Deleted
git clean -n

# Remove Untracked Files
git clean -f

# Remove Untracked Files and Directories
git clean -fd

# Remove Ignored Files Too
git clean -fdx
```

## Rebasing

```bash
# Rebase onto Branch
git rebase <branch>
git rebase main

# Interactive Rebase
git rebase -i HEAD~3

# Continue Rebase
git rebase --continue

# Abort Rebase
git rebase --abort

# Skip Commit
git rebase --skip
```

## Cherry-picking

```bash
# Apply Specific Commit
git cherry-pick <commit-hash>

# Cherry-pick Multiple Commits
git cherry-pick <commit1> <commit2>

# Cherry-pick Range
git cherry-pick <commit1>..<commit2>
```

## Submodules

```bash
# Add Submodule
git submodule add <url> <path>

# Initialize Submodules
git submodule init

# Update Submodules
git submodule update

# Clone with Submodules
git clone --recursive <url>
```

## Advanced Commands

```bash
# Reflog (recovery)
git reflog
git reflog show HEAD

# Bisect (find bug)
git bisect start
git bisect bad
git bisect good <commit>
git bisect reset

# Archive
git archive --format=zip HEAD > project.zip

# Describe
git describe
git describe --tags

# Shortlog
git shortlog
git shortlog -sn              # Summary by author
```

## Inspection Commands

```bash
# File History
git log --follow <file>

# Who Changed What
git blame <file>

# List Files in Commit
git ls-tree -r <commit> --name-only

# Show File from Commit
git show <commit>:<file>
```

## Useful Combinations

```bash
# Undo Last Commit but Keep Changes
git reset --soft HEAD~1

# Amend Last Commit (add more files)
git add forgotten-file
git commit --amend --no-edit

# Sync Fork with Upstream
git fetch upstream
git checkout main
git merge upstream/main

# Create Branch from Stash
git stash branch <branch-name>

# View Commits Not in Remote
git log origin/main..HEAD

# Delete All Local Branches Except Main
git branch | grep -v "main" | xargs git branch -D
```

## Conflict Resolution

```bash
# After Conflict
git status                    # See conflicts
# Edit files manually
git add <resolved-file>
git commit

# Accept Theirs/Ours
git checkout --theirs <file>
git checkout --ours <file>

# Merge Tool
git mergetool
```

## Performance Commands

```bash
# Garbage Collection
git gc

# Prune
git prune

# Optimize Repository
git gc --aggressive

# Count Objects
git count-objects -v

# Repository Size
git rev-list --objects --all | git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' | sort -k3 -n
```

## Troubleshooting Commands

```bash
# Fix Detached HEAD
git checkout main

# Recover Deleted Branch
git reflog
git checkout -b <branch> <commit-hash>

# Undo git add (before commit)
git reset

# Recover Lost Commits
git reflog
git cherry-pick <commit-hash>

# Fix Wrong Commit Message
git commit --amend -m "Correct message"

# Remove File from Git but Keep Locally
git rm --cached <file>
```

## Safety Commands

```bash
# Dry Run Push
git push --dry-run

# Check What Would Be Pulled
git fetch --dry-run

# Verify Repository
git fsck

# Check Remote Connection
git remote -v
git ls-remote
```

## Quick Reference Patterns

```bash
# HEAD References
HEAD           # Current commit
HEAD~1         # One commit before
HEAD~2         # Two commits before
HEAD^          # First parent
HEAD^^         # Grandparent

# Commit Ranges
<commit1>..<commit2>   # Commits between
<commit1>...<commit2>  # Symmetric difference

# Special Names
main           # Branch name
origin/main    # Remote branch
@              # Shorthand for HEAD
```

This reference covers the most commonly used Git commands. For detailed information on any command, use:

```bash
git help <command>
git <command> --help
man git-<command>
```
