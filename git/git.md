# GIT

## Create a new git repo

This section explains how to initialize a new local Git repository in an existing folder and ensure the initial branch is named `main`.

1. Open a terminal and change into the folder where you want the repository:

   ```sh
   cd /path/to/your/folder
   ```

2. Initialize the repository and create the `main` branch in one step (Git 2.28+):

   ```sh
   git init -b main
   ```

   - The `-b main` flag creates and sets the initial branch to `main`.

3. Add files and make the initial commit:

   ```sh
   git add .
   git commit -m "Initial commit"
   ```

4. (Optional) Make `main` the default for all future `git init` on this machine:

   ```sh
   git config --global init.defaultBranch main
   ```

5. (Optional) To publish to GitHub:

   - Create a new empty repository on GitHub (do not initialize with README).
   - Add the remote and push:

     ```sh
     git remote add origin https://github.com/youruser/yourrepo.git
     git push -u origin main
     ```


## Upload a local repo to GitHub

If you already have a local repository and want to rename the current default branch to `main` and push to GitHub:

1. Rename the branch locally (if needed):

   ```sh
   git branch -m master main
   ```

2. Update remote and push:

   ```sh
   git push -u origin main
   git push origin --delete master   # optional: remove old branch on remote
   ```

3. On GitHub, go to the repository settings and set `main` as the default branch, then delete `master` if desired.

