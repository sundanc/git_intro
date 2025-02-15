# Git Commands Reference Guide

## Basic Configuration

```bash
# Configure Git globally
git config --global user.name "Your Username"
git config --global user.email "your.email@example.com"
git config --global core.editor "code --wait"  # Set VS Code as default editor
```

## Repository Setup

```bash
# Initialize new repository
mkdir repo-name
cd repo-name
git init

# Create initial README
echo "# repo-name" >> README.md
```

## Basic Operations

```bash
# Stage changes
git add .                    # Stage all changes
git add <file1> <file2>     # Stage specific files
git add -p                   # Stage changes interactively

# Commit changes
git commit -m "Commit message"
git commit -am "Commit message"  # Stage tracked files and commit

# Status and history
git status                   # Check repository status
git log                      # View commit history
git log --oneline           # Compact history view
git diff                    # View unstaged changes
git diff --staged           # View staged changes
```

## Remote Operations

```bash
# GitHub CLI operations
gh auth login               # Login to GitHub
gh repo create repo-name --public  # Create public repository

# Remote repository setup
git remote add origin https://github.com/username/repo-name.git
git remote -v              # View remote repositories
git branch -M main        # Rename current branch to main
git push -u origin main   # Push to remote with upstream tracking

# Fetch and pull
git fetch origin          # Download objects and refs
git pull origin main      # Fetch and merge changes
git clone <repository-url>  # Clone existing repository
```

## Branch Management

```bash
# View branches
git branch                  # List local branches
git branch -a              # List all branches including remote
git branch --show-current  # Show current branch name

# Branch operations
git checkout <branch-name>     # Switch branches
git checkout -b <branch-name>  # Create and switch to new branch
git branch -d <branch-name>    # Delete local branch
git push origin --delete <branch-name>  # Delete remote branch
git merge <branch-name>        # Merge branch into current
git merge --abort             # Abort merge in case of conflicts
```

## Undo Operations

```bash
# Undo changes
git reset --soft HEAD~1     # Undo last commit, keep changes staged
git reset --mixed HEAD~1    # Undo last commit, keep changes unstaged
git reset --hard HEAD~1     # Undo last commit, discard changes
git revert <commit-hash>    # Create new commit that undoes changes
git checkout -- <file>      # Discard changes in working directory
git clean -fd              # Remove untracked files and directories
```

## Stashing

```bash
# Stash operations
git stash                           # Quick stash
git stash save "message"           # Stash with message
git stash list                     # List all stashes
git stash show                     # Show stash contents
git stash apply                    # Apply most recent stash
git stash apply stash@{n}         # Apply specific stash
git stash drop                     # Remove most recent stash
git stash clear                    # Remove all stashes
```

## Advanced Inspection

```bash
# Detailed inspection
git show <commit>           # Show commit details
git blame <file>           # Show who changed what
git reflog                 # View reference logs
git log --graph --oneline  # Show branch graph
git bisect start          # Binary search for bugs
```

## Submodules

```bash
# Submodule operations
git submodule add <url> <path>   # Add submodule
git submodule init              # Initialize submodules
git submodule update           # Update submodules
git submodule update --init --recursive  # Initialize and update recursively
```

## Aliases

```bash
# Create aliases
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
```

## Best Practices

- Write clear, concise commit messages
- Commit frequently, push regularly
- Use meaningful branch names
- Pull before pushing to avoid conflicts
- Keep main/master branch stable
- Use `.gitignore` for project-specific exclusions
- Review changes before committing
- Create feature branches for new work
- Delete merged branches to keep repository clean
