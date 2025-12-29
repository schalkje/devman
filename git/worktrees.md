# Working with Git Worktrees

Git worktrees allow you to have multiple branches checked out simultaneously in different directories. This is useful for working on multiple features or versions without constantly switching branches in a single working directory.

## Naming Worktrees

When working with Git worktrees, it's important to use a clear and consistent naming convention. This helps you quickly identify the purpose of each worktree and avoid confusion. Here's an example structure:

```
c:\repo\
├─ markread                  ← anchor repo (rarely opened)
└─ markread.worktrees\
   ├─ main
   ├─ feature-reader
   ├─ bugfix-markdown
   └─ experiment-ui
```

### Guidelines:
- Use the main repository folder as the "anchor repo" and rarely open it directly.
- Create a dedicated folder for worktrees, such as `repo.worktrees`.
- Name worktree directories based on their branch or purpose:
  - `main` for the main branch.
  - `feature-*` for feature branches (e.g., `feature-reader`).
  - `bugfix-*` for bug fixes (e.g., `bugfix-markdown`).
  - `experiment-*` for experimental branches (e.g., `experiment-ui`).

This structure ensures clarity and avoids clutter in your main repository folder.

---

## Creating a Worktree

To create a new worktree for an existing branch:

```sh
git worktree add <path> <branch>
```

For example, to create a worktree for a branch named `feature/x` in a directory called `/feature-x` from the anchor folder:

```sh
git worktree add c:\repo\<reponame>\feature-x feature-x
```

From a worktree to a new work tree

```sh
git worktree add ..\feature-x feature-x
```



This creates a new directory at `../feature-x` and checks out the `feature-x` branch there.

If the branch doesn't exist yet, you can create it along with the worktree:

```sh
git worktree add -b <new-branch> <path>
```

For example:

```sh
git worktree add -b new-feature ../new-feature
```

## Listing Worktrees

To see all active worktrees in the repository:

```sh
git worktree list
```

This will show the main working directory and any additional worktrees, along with their paths and current branches.

## Working in a Worktree

Each worktree is an independent working directory. You can navigate to the worktree directory and work normally:

```sh
cd ../feature-x
# Now you're in the worktree for feature-x
git status
git add .
git commit -m "Work on feature-x"
```

Changes in one worktree don't affect others, and you can push/pull independently.


## Committing Changes in a Worktree

#### Using Command Line
1. Navigate to the worktree directory:
   ```sh
   cd path/to/worktree
   ```
2. Check the status of your changes:
   ```sh
   git status
   ```
3. Stage your changes:
   ```sh
   git add .
   ```
4. Commit your changes:
   ```sh
   git commit -m "Your commit message"
   ```
5. Push the worktree branch to GitHub:
   ```sh
   git push origin worktree-branch-name
   ```

#### Using VS Code
1. Open the worktree folder in VS Code.
2. Go to the **Source Control** tab.
3. Stage the changes by clicking the `+` icon next to the files.
4. Enter a commit message in the text box and click the checkmark to commit.

---

## Merging Changes from a Worktree using a pull request

#### On GitHub
Open a pull request on GitHub to merge the branch into `main`.

1. Navigate to the repository.
2. Click **New Pull Request**.
3. Select the worktree branch and the target branch (e.g., `main`).
4. Add a title and description, then click **Create Pull Request**.
5. Review and merge the pull request.


---

## Cleaning Up a Worktree

To remove a worktree when you're done:

#### Using Command Line
1. Remove the worktree:
   ```sh
   git worktree remove path/to/worktree
   ```
    Or from inside the worktree directory:

    ```sh
    git worktree remove .
    ```
2. Prune references to worktrees that no longer exist on disk (deleted worktrees):
   ```sh
   git worktree prune
   ```
   _If a worktree directory is deleted manually (e.g., `rm -rf ../feature-x`), Git might still think it exists._


**Important:** Make sure to commit or stash any changes in the worktree before removing it, as uncommitted changes will be lost.


## Tips

- Worktrees share the same Git history and configuration, but have separate staging areas and working directories.
- The main working directory (usually where you ran `git init`) is always listed first in `git worktree list`.
- Worktrees are particularly useful for:
  - Working on multiple features simultaneously
  - Testing different branches without switching
  - Maintaining long-running branches like `gh-pages` for documentation



## Using Git Worktrees in VS Code

### Seeing the Worktree Name and Branch

To make it easier to identify which worktree and branch you're working on in VS Code, you can customize the window title. This is especially useful when working with multiple worktrees simultaneously.

### Custom Window Title (Highly Recommended)

Add the following configuration to your `settings.json` file in VS Code:

```json
"window.title": "${folderName} [${activeRepositoryBranch}]"
```

### Result

With this setting, the VS Code window title will display the folder name and the active branch. For example:

```
repo-feature-auth [feature/auth]
```

This makes it clear:
- **Which worktree** you're in (e.g., `repo-feature-auth`).
- **Which branch** is currently active (e.g., `feature/auth`).

### Why This Matters

This is the best way to avoid mistakes caused by working in the wrong worktree or branch. By always seeing the worktree and branch in the window title, you can:
- Avoid accidental changes to the wrong branch.
- Quickly switch between worktrees without confusion.
- Maintain focus and organization when working on multiple tasks.

## Why Use a Separate Worktrees Folder?

### Is it Necessary to Have Both a "Project Folder" and a "Worktree Folder"?

Yes — at least one worktree must be the "main" worktree.

In your case:

```
c:\repo\markread              ← main worktree (required)
c:\repo\markread.worktrees\…  ← additional worktrees (optional, many)
```

### Why This is Required

Git worktrees always have:

- **Exactly one main worktree** (the original clone)
- **Zero or more linked worktrees**

#### The Main Worktree
- Holds the real `.git/` directory.
- Acts as the anchor for all other worktrees.
- Cannot be removed unless you reclone the repository.

#### Other Worktrees
- Are lightweight checkouts.
- Contain a `.git` file pointing back to the main repository.

### Key Points
- ❌ You cannot have only a secondary worktree.
- ✅ You can ignore the main worktree for daily work, but it must exist.

By keeping a separate folder for additional worktrees, you maintain a clean and organized structure while ensuring the main worktree remains intact as the anchor for your repository.

---

