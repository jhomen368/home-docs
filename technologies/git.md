---
tags:
  - windows
  - linux
  - git
---

### 1. Install Git
Install Git using the command:
```bash
sudo apt install git-all
```

### 2. Commit Guidelines
Use specific commit message types for clarity:
- **feat**: New feature (e.g., `git commit -m "feat:UI: Added login functionality"`)
- **fix**: Bug fix
- **chore**: Non-feature/fix changes, e.g., updating dependencies
- **refactor**: Code restructuring without new features or fixes
- **docs**: Documentation updates
- **style**: Formatting changes
- **test**: Test modifications
- **perf**: Performance improvements
- **ci**: Continuous integration changes
- **build**: Build system changes
- **revert**: Reverts a commit

### 3. Merging Branches
Merge the test branch into main with these steps:
1. Check out and pull the latest from test:
   ```bash
   git checkout test
   git pull
   ```
2. Switch to main and pull updates:
   ```bash
   git checkout master
   git pull
   ```
3. Merge without fast-forward or commit:
   ```bash
   git merge --no-ff --no-commit test
   ```
4. Resolve conflicts by editing files, then add changes:
   ```bash
   git add .
   ```
5. Commit the merge:
   ```bash
   git commit -m 'merge test branch'
   ```
6. Push to remote:
   ```bash
   git push
   ```

### 4. SSH Key Setup
Generate an SSH key for GitHub authentication:
```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```
Add the public key to your GitHub account under Settings > SSH and GPG keys.

### Practice Tips
- **Test Repository**: Create a test repo to practice commits, merges, and conflict resolution.
- **SSH Key Test**: Use `ssh -T git@github.com` to verify SSH setup.

By following these steps, you can efficiently manage your Git workflow with clear commit histories and secure authentication.
