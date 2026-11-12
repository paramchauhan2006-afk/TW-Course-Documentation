# Git and GitHub

Git is a distributed version control system for tracking changes in source code. GitHub is a web-based hosting service for Git repositories that enables collaboration and provides additional features like issue tracking and pull requests.

## What is Git?

Git manages and tracks changes to files, allowing:
- Version history of all changes
- Collaboration without conflicts
- Branching and merging workflows
- Distributed development
- Backup and recovery

## What is GitHub?

GitHub extends Git with:
- Remote repository hosting
- Web interface for repositories
- Collaboration features (Pull Requests, Issues)
- Project management tools
- CI/CD integration
- Documentation hosting (GitHub Pages)

## Key Concepts Learned

### Basic Git Workflow

```
Working Directory → Staging Area → Local Repository → Remote Repository
                 (add)         (commit)          (push)
```

### Repository Types

**Local Repository**: Git repository on your machine
**Remote Repository**: Repository hosted on server (GitHub, GitLab, etc.)

### Three States of Files

1. **Modified**: Changed but not staged
2. **Staged**: Marked for next commit
3. **Committed**: Stored in local repository

## Essential Git Commands

### Configuration

```bash
# Set user name
git config --global user.name "Your Name"

# Set email
git config --global user.email "your.email@example.com"

# View configuration
git config --list

# Set default editor
git config --global core.editor "vim"
```

### Repository Creation

```bash
# Initialize new repository
git init

# Clone existing repository
git clone https://github.com/user/repo.git

# Clone specific branch
git clone -b branch-name https://github.com/user/repo.git
```

### Basic Operations

```bash
# Check repository status
git status

# Add files to staging area
git add filename.txt
git add .                    # Add all files
git add *.java              # Add all Java files

# Commit changes
git commit -m "Commit message"

# Commit with detailed message
git commit                  # Opens editor

# Add and commit in one step
git commit -am "Message"    # For tracked files only
```

### Viewing History

```bash
# View commit history
git log

# Compact log
git log --oneline

# Graph view
git log --graph --oneline --all

# Show specific number of commits
git log -n 5

# Show changes in commits
git log -p

# Show commits by author
git log --author="Name"
```

### Viewing Changes

```bash
# Show unstaged changes
git diff

# Show staged changes
git diff --staged

# Show changes between commits
git diff commit1 commit2

# Show changes in specific file
git diff filename.txt
```

### Branching

```bash
# List branches
git branch

# Create new branch
git branch feature-branch

# Switch to branch
git checkout feature-branch

# Create and switch to branch
git checkout -b new-feature

# Delete branch
git branch -d branch-name

# Force delete unmerged branch
git branch -D branch-name

# Rename current branch
git branch -m new-name
```

### Merging

```bash
# Merge branch into current branch
git merge feature-branch

# Abort merge on conflicts
git merge --abort

# Continue merge after resolving conflicts
git merge --continue
```

### Remote Operations

```bash
# Add remote repository
git remote add origin https://github.com/user/repo.git

# View remotes
git remote -v

# Remove remote
git remote remove origin

# Rename remote
git remote rename old-name new-name

# Fetch from remote (doesn't merge)
git fetch origin

# Pull from remote (fetch + merge)
git pull origin main

# Push to remote
git push origin main

# Push new branch to remote
git push -u origin feature-branch

# Delete remote branch
git push origin --delete branch-name
```

### Undoing Changes

```bash
# Discard changes in working directory
git checkout -- filename.txt

# Unstage file (keep changes)
git reset HEAD filename.txt

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Revert commit (creates new commit)
git revert commit-hash
```

### Stashing

```bash
# Stash current changes
git stash

# Stash with message
git stash save "Work in progress"

# List stashes
git stash list

# Apply latest stash
git stash apply

# Apply specific stash
git stash apply stash@{0}

# Apply and remove stash
git stash pop

# Delete stash
git stash drop stash@{0}

# Clear all stashes
git stash clear
```

### Tagging

```bash
# Create lightweight tag
git tag v1.0.0

# Create annotated tag
git tag -a v1.0.0 -m "Version 1.0.0"

# List tags
git tag

# Push tags to remote
git push origin --tags

# Delete tag
git tag -d v1.0.0

# Delete remote tag
git push origin --delete v1.0.0
```

## GitHub-Specific Features

### Pull Requests

Process for contributing changes:
1. Fork repository
2. Clone fork locally
3. Create feature branch
4. Make changes and commit
5. Push to your fork
6. Create Pull Request on GitHub
7. Code review and discussion
8. Merge after approval

### Issues

- Track bugs and feature requests
- Assign to team members
- Label and milestone organization
- Link to pull requests

### GitHub CLI

```bash
# Authenticate
gh auth login

# Create repository
gh repo create project-name

# Clone repository
gh repo clone user/repo

# Create pull request
gh pr create

# View pull requests
gh pr list

# Create issue
gh issue create

# View issues
gh issue list
```

## Branching Strategies

### Git Flow

```
master (production)
  ├── develop
  │   ├── feature/new-feature
  │   ├── feature/another-feature
  ├── release/1.0
  ├── hotfix/urgent-fix
```

**Branches:**
- `master`: Production-ready code
- `develop`: Integration branch
- `feature/*`: New features
- `release/*`: Release preparation
- `hotfix/*`: Production fixes

### GitHub Flow

Simplified workflow:
1. Create branch from `main`
2. Make changes
3. Open Pull Request
4. Review and discuss
5. Merge to `main`
6. Deploy

## Best Practices

### Commit Messages

**Good Format:**
```
Short summary (50 chars or less)

Detailed explanation if needed. Wrap at 72 characters.
Explain what and why, not how.

- Bullet points are okay
- Use imperative mood: "Add feature" not "Added feature"
```

**Examples:**
- ✅ "Add user authentication system"
- ✅ "Fix memory leak in image processor"
- ✅ "Update documentation for API v2"
- ❌ "Fixed stuff"
- ❌ "asdfgh"
- ❌ "Made changes"

### Repository Organization

```
project/
├── .gitignore         # Files to ignore
├── README.md          # Project documentation
├── LICENSE            # License file
├── .github/           # GitHub-specific files
│   └── workflows/     # GitHub Actions
├── docs/              # Documentation
├── src/               # Source code
└── tests/             # Test files
```

### .gitignore

```gitignore
# Compiled files
*.o
*.pyc
*.class

# Build directories
build/
dist/
target/

# Dependencies
node_modules/
venv/

# IDE files
.vscode/
.idea/
*.swp

# OS files
.DS_Store
Thumbs.db

# Sensitive files
.env
secrets.txt
```

## Common Workflows

### Start New Feature

```bash
git checkout main
git pull origin main
git checkout -b feature/new-feature
# Make changes
git add .
git commit -m "Implement new feature"
git push -u origin feature/new-feature
# Create PR on GitHub
```

### Update Feature Branch

```bash
git checkout main
git pull origin main
git checkout feature/my-feature
git merge main
# Resolve conflicts if any
git push origin feature/my-feature
```

### Fix Merge Conflicts

```bash
# After conflict occurs
git status                    # See conflicted files
# Edit files to resolve conflicts
git add resolved-file.txt
git commit -m "Resolve merge conflicts"
```

## Important Notes

1. **Commit Often**: Small, focused commits are better
2. **Pull Before Push**: Always pull latest changes first
3. **Branch Names**: Use descriptive names (feature/add-login)
4. **Never Rewrite Public History**: Don't force push to shared branches
5. **Review Before Commit**: Check what you're committing
6. **Protect Main Branch**: Use branch protection rules on GitHub

## Common Mistakes to Avoid

1. ❌ Committing sensitive data (passwords, API keys)
2. ❌ Large binary files in repository
3. ❌ Unclear commit messages
4. ❌ Working directly on main branch
5. ❌ Not pulling before pushing
6. ❌ Committing merge conflicts
7. ❌ Force pushing to shared branches

## Key Takeaways

- Git tracks all changes with complete history
- Branching enables parallel development
- Commits should be atomic and meaningful
- Pull Requests facilitate code review
- Remote repositories enable collaboration
- .gitignore prevents tracking unwanted files
- Good commit messages are documentation
- GitHub adds collaboration features to Git

## Useful Aliases

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --oneline --graph --all'
```

## Resources

- Official Git Documentation: https://git-scm.com/doc
- GitHub Guides: https://guides.github.com/
- Pro Git Book: https://git-scm.com/book
- Git Cheat Sheet: https://education.github.com/git-cheat-sheet-education.pdf
