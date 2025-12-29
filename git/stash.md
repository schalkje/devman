# Git Stashes

## What Are Stashes?
A stash in Git is a mechanism to temporarily save changes that are not yet ready to be committed. It allows you to save your work-in-progress changes and revert your working directory to a clean state, enabling you to switch branches or work on something else without losing your progress.

## When to use Stashes and when Worktrees

| Feature                  | Stashes                                      | Worktrees                                    |
|--------------------------|----------------------------------------------|---------------------------------------------|
| Purpose                 | Temporarily save changes                     | Work on multiple branches simultaneously    |
| Persistence             | Temporary                                   | Persistent                                  |
| Risk of Data Loss       | Higher (if not applied or cleared properly) | Lower                                       |
| Use Case                | Quick context switching                     | Long-term parallel development             |
| Ease of Use             | Simple commands                             | Requires setup                              |
| Disk Space Usage        | Minimal                                     | Requires additional disk space             |
| Switching Contexts      | Fast                                        | Requires navigating to the worktree folder |

Use the table above to decide which approach best suits your workflow.


## How to Use Stashes

### Creating a Stash
To create a stash, use the following command:
```bash
git stash
```
This saves your uncommitted changes and reverts your working directory to the last committed state.

You can also provide a message to describe the stash:
```bash
git stash push -m "Your stash message"
```

### Viewing Stashes
To see a list of all stashes, use:
```bash
git stash list
```
This will display all stashes along with their index and description.

### Reapplying a Stash
To reapply the most recent stash, use:
```bash
git stash apply
```
If you want to reapply a specific stash, use its index:
```bash
git stash apply stash@{index}
```

### Applying and Removing a Stash
To reapply and remove a stash in one step, use:
```bash
git stash pop
```

### Cleaning Up Stashes
To delete a specific stash, use:
```bash
git stash drop stash@{index}
```

To clear all stashes, use:
```bash
git stash clear
```



## Summary
- Use stashes to temporarily save changes and revert to a clean state.
- Prefer worktrees for long-term parallel work on multiple branches.
- Manage stashes with commands like `git stash`, `git stash list`, `git stash apply`, and `git stash clear`.