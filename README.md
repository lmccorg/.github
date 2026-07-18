# 🏢 LMCC Org Git Workflow Guide

 This guide provides a clear, streamlined workflow for managing code, branching, and pushing updates safely. All collaborators must follow these practices to ensure codebase stability.

---

## 🚀 The Standard Git Workflow

To keep our `main` branch stable and up to date, always follow this step-by-step development lifecycle.

### 1. Synchronize Your Local `main` Branch
Before starting any new work, ensure your local `main` branch has the latest updates from the remote repository.

```bash
# Switch to the main branch
git checkout main

# Verify you are on the main branch
git branch

# Pull the latest changes from the remote server
git pull origin main
```

### 2. Create a Feature or Deployment Branch
Never commit directly to `main` (Best Practices). Always create a dedicated branch for your feature, bug fix, or deployment task.

```bash
# Create and switch to a new branch
git checkout -b feature/your-feature-name

# Alternative: Switch to an existing deployment branch
git checkout branch-name
```

### 3. Make Changes & Commit
Work on your task within your project editor. Once ready, stage and commit your modifications with a clear, concise message.

```bash
# Check the status of your modified files
git status

# Stage all changes for the commit
git add .

# Commit changes with a meaningful message
git commit -m "feat: implement user authentication logic"
```

### 4. Push to the Remote Repository
Push your local branch up to GitHub so it can be reviewed by the team.

```bash
# Push your branch to the remote repository
git push origin your-branch-name
```

### 5. Open a Pull Request (PR) & Merge
1. Go to our GitHub repository page.
2. Click the **"Compare & pull request"** button for your recently pushed branch.
3. Provide a brief description of your changes and assign code reviewers.
4. Once the PR passes automatic checks and is approved, it will be **merged into `main`**.

<!-- 
---
## 🛠️ Multi-Environment Deployments (If Applicable)

If your project requires deploying to specific environments (e.g., `development`, `staging`, `production`) before merging into `main`:

```bash
# 1. Switch to the target environment branch
git checkout staging

# 2. Pull the latest state of that environment
git pull origin staging

# 3. Merge your feature branch into the environment branch locally
git merge feature/your-feature-name

# 4. Push the environment branch to trigger deployment pipelines
git push origin staging
```
*Note: Once verified in the target environment, proceed with creating a Pull Request to merge your original feature branch into `main`.* -->

---

## Standard `.gitignore` for ASP.NET Projects

When initializing a new repository, copy this exact block into a file named `.gitignore` at the root of your project directory or **Download** it from here **[.gitignore](https://github.com/lmccorg/.github/blob/main/.gitignore)**. This prevents temporary build artifacts and user-specific configurations from polluting the repository.

```gitignore
# IIS Express
*.vspscc
.vs/

# Build Folders
bin/
obj/
PrecompiledWeb/
Properties/PublishProfiles/

# User-specific Visual Studio settings
*.user
*.suo
*.userosscache
*.sln.docstates

# Package folders (if using `packages.config`-based NuGet)
packages/
*.nupkg
project.lock.json

# VS Code files (if you use it)
.vscode/

# Logs and temp
*.log
*.tmp

# Other
_ReSharper*/
*.DotSettings.user
```

---

## 💡 Development Best Practices

*   **Never Direct-Push to Main:** The `main` branch is protected. All code changes must pass through a Pull Request.
*   **Write Clear Commit Messages:** Use prefixes like `feat:`, `fix:`, `docs:`, or `refactor:` to make the repository history easy to navigate.
*   **Keep Pull Requests Small:** Smaller PRs are reviewed faster, tested more thoroughly, and carry significantly less risk of breaking existing functionality.
*   **Verify Code Compiles Locally:** Before pushing code or opening a PR, run a local build to ensure you aren't introducing compilation breaks or missing dependencies.
*   **Never Commit Secrets:** Do not hardcode API keys, database connection strings, or credentials. Use environment variables (`appsettings.Development.json` added to local ignore) instead.
