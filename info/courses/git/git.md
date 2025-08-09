[version control](./images/git.png)

---

# Git Usage Manual

## Initial Setup
```bash
# Configure username
git config --global user.name "Your Name"

# Configure email
git config --global user.email "your.email@example.com"
```

## Starting a New Repository
```bash
# Initialize a Git repository
git init

# Add GitHub remote repository
git remote add origin https://github.com/your-username/your-repository.git
```

## Basic Workflow
```bash
# Check files status
git status

# Add files to staging
git add .                    # Add all files
git add filename.extension   # Add specific file

# Create commit
git commit -m "Descriptive commit message"

# Send changes to GitHub
git push origin main        # depending on main branch
```

## Branches
```bash
# Create new branch
git branch branch-name

# Switch to a branch
git checkout branch-name

# Create and switch to new branch (shortcut)
git checkout -b branch-name

# List branches
git branch
```

## Updating Local Repository
```bash
# Download changes from remote repository
git pull origin main

# Check remote branches
git fetch
```

## Other Commands
```bash
# Check commit history
git log                      # Detailed
git log --oneline            # Summarized

# Switch to a specific commit
git checkout <hash_do_commit>                    # Read mode
git reset --hard <hash_do_commit>                # Permanently revert (delete later commits)
git checkout -b nova-branch <hash_do_commit>     # A new branch from an old commit

# Turn a secondary branch into a new "main"
git branch -m develop main
git push origin main

# Clone a repository
git clone https://github.com/your-username/repository-name.git
```

## Important Tips
1. Always check which branch you're working on using `git branch`
2. Make frequent commits with clear and descriptive messages
3. Keep your local repository updated with `git pull` before starting work
4. Use `.gitignore` to exclude files and folders that shouldn't be versioned