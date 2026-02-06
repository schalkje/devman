# Mounting a Repo Folder in Your Home Folder on WSL2

By default, WSL exposes your Windows drives under `/mnt/<drive>` (for example: `C:\repo` is available at `/mnt/c/repo`).

Sometimes it’s nicer to work from a path in your Linux home folder (shorter paths, consistent tooling, and you can standardize on `~/repo`). This page shows a clean way to do that.

## Option A — Mount `C:\repo` into `~/repo` (recommended)

This creates a real mount so `~/repo` maps directly to `C:\repo`.

### A1) One-time mount (until you restart WSL)

1) Create the mount point:
```bash
mkdir -p ~/repo
```

2) Mount the Windows folder:
```bash
sudo mount -t drvfs C:/repo ~/repo
```

Verify:
```bash
ls -la ~/repo
mount | grep -i "~/repo" || mount | grep -i " /home/" | grep -i repo
```

Unmount later if needed:
```bash
sudo umount ~/repo
```

### A2) Permanent mount (recommended)

WSL can read `/etc/fstab` on startup, but only if you enable it.

1) Enable fstab mounting and set sane defaults

Edit `/etc/wsl.conf`:
```bash
sudo nano /etc/wsl.conf
```

Suggested configuration:
```
[automount]
enabled = true
mountFsTab = true
options = "metadata,umask=22,fmask=11"
```

Notes:
- `metadata` makes Linux permissions work on the Windows filesystem (WSL stores permission metadata alongside files).
- `umask=22,fmask=11` yields typical permissions: directories `755`, files `644`.

2) Add a mount entry to `/etc/fstab`

Edit `/etc/fstab`:
```bash
sudo nano /etc/fstab
```

Add a line like this (replace `<your-user>` with your Linux username):
```
C:/repo /home/<your-user>/repo drvfs metadata,umask=22,fmask=11 0 0
```

Important:
- Don’t use `$(whoami)` in `/etc/fstab`. It will not be expanded.
- If you use a different location, make sure the mount point exists (`mkdir -p ...`).

3) Restart WSL

From Windows PowerShell / CMD:
```powershell
wsl --shutdown
```

Then open your distro again. `~/repo` should now be mounted automatically.

## Option B — Symlink `~/repo` to `/mnt/c/repo` (simple, no sudo)

If you don’t need a “real” mount and just want a convenient path, a symlink is often enough:

```bash
ln -s /mnt/c/repo ~/repo
```

Pros: easy, no `sudo`, no fstab.
Cons: you’re still working on `/mnt/c` (some tools may behave slightly differently).

## Troubleshooting

- If WSL doesn’t mount your `fstab` entries, re-check `/etc/wsl.conf` has `mountFsTab = true`, then run `wsl --shutdown` again.
- If the mount point is “busy” during unmount: close terminals/editors using the path, then retry `sudo umount ~/repo`.
- If you care about Linux permissions in your repo, keep `metadata` enabled. Without it, everything tends to look like a fixed permission mask.