# Git Branches

Everything you need to know about working with Git branches.

## Listing Branches

### List Local Branches

```bash
git branch
```

### List Remote Branches

```bash
git branch -r
```

### List All Branches (Local + Remote)

```bash
git branch -a
```

### List Branches with Last Commit Info

```bash
git branch -v
```

### List Branches with Tracking Info

```bash
git branch -vv
```

## Creating Branches

### Create a New Branch

```bash
git branch <branch-name>
```

### Create and Switch to New Branch

```bash
git checkout -b <branch-name>
# or (Git 2.23+)
git switch -c <branch-name>
```

### Create Branch from Specific Commit

```bash
git branch <branch-name> <commit-hash>
```

### Create Branch from Remote Branch

```bash
git checkout -b <local-branch> origin/<remote-branch>
# or
git switch -c <local-branch> origin/<remote-branch>
```

## Switching Branches

### Switch to Existing Branch

```bash
git checkout <branch-name>
# or (Git 2.23+)
git switch <branch-name>
```

### Switch to Previous Branch

```bash
git checkout -
# or
git switch -
```

## Comparing Branches

### Compare Local Branch with Remote

```bash
# First fetch to get latest remote info
git fetch origin

# See commits on remote not in local
git log <branch>..origin/<branch>

# See commits on local not in remote
git log origin/<branch>..<branch>

# See all differences
git log <branch>...origin/<branch>
```

### Compare Two Branches

```bash
# Show commits in branch-b that are not in branch-a
git log branch-a..branch-b

# Show file differences between branches
git diff branch-a..branch-b

# Show just the file names that differ
git diff --name-only branch-a..branch-b

# Show stat summary of changes
git diff --stat branch-a..branch-b
```

### Check if Branch is Behind/Ahead

```bash
# Fetch first to update remote tracking info
git fetch origin

# Show ahead/behind count
git rev-list --left-right --count origin/<branch>...<branch>
```

## Syncing with Remote

### Fetch All Remote Branches

```bash
git fetch --all
```

### See Which Branches Need Updating

```bash
git remote show origin
```

### Update Local Branch with Remote

```bash
git pull origin <branch-name>
# or if tracking is set up
git pull
```

### Push Local Branch to Remote

```bash
git push origin <branch-name>
# or set upstream and push
git push -u origin <branch-name>
```

## Renaming Branches

### Rename Current Branch

```bash
git branch -m <new-name>
```

### Rename Any Branch

```bash
git branch -m <old-name> <new-name>
```

### Rename Remote Branch

```bash
# Delete old remote branch and push new one
git push origin --delete <old-name>
git push origin <new-name>
```

## Deleting Branches

### Delete Local Branch (Safe)

```bash
git branch -d <branch-name>
```

### Delete Local Branch (Force)

```bash
git branch -D <branch-name>
```

### Delete Remote Branch

```bash
git push origin --delete <branch-name>
# or
git push origin :<branch-name>
```

### Clean Up Stale Remote-Tracking Branches

```bash
git fetch --prune
# or
git remote prune origin
```

## Tracking Branches

### Set Upstream for Current Branch

```bash
git branch --set-upstream-to=origin/<branch>
# or
git branch -u origin/<branch>
```

### See Tracking Configuration

```bash
git branch -vv
```

### Unset Upstream

```bash
git branch --unset-upstream
```

## Merging Branches

### Merge Branch into Current Branch

```bash
git merge <branch-name>
```

### Merge with No Fast-Forward (Creates Merge Commit)

```bash
git merge --no-ff <branch-name>
```

### Abort a Merge

```bash
git merge --abort
```

## Finding Branches

### Find Branches Containing a Commit

```bash
git branch --contains <commit-hash>
```

### Find Merged Branches

```bash
git branch --merged
```

### Find Unmerged Branches

```bash
git branch --no-merged
```

## Useful Tips

### Show Current Branch Name Only

```bash
git branch --show-current
# or
git rev-parse --abbrev-ref HEAD
```

### List Branches Sorted by Last Commit Date

```bash
git branch --sort=-committerdate
```

### Show Branch History Graph

```bash
git log --oneline --graph --all
```
