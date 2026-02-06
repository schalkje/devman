# Mounting a Repo Folder in Your Home Folder on WSL2

## Option A — Mount `C:\repo` into Your Linux Home (BEST)

This is the clean and correct approach.

### 1️⃣ Create a Mount Point
Run the following command to create a mount point in your Linux home directory:
```bash
mkdir -p ~/repo
```

### 2️⃣ Mount the Windows Folder
Use the following command to mount the Windows folder into your Linux home directory:
```bash
sudo mount -t drvfs C:/repo ~/repo
```

Now, the folder `~/repo` in your Linux home directory will point to `C:\repo` on your Windows system.

### 🔁 Make it Permanent (Recommended)
To ensure the mount persists across WSL restarts, follow these steps:

#### Edit `/etc/wsl.conf`
Open the WSL configuration file:
```bash
sudo nano /etc/wsl.conf
```

Add the following lines to enable automounting with the correct options:
```
[automount]
enabled = true
options = "metadata,umask=22,fmask=11"
mountFsTab = true

[filesystem]
umask = 22
```

Notes:
- `options = ...` affects how Windows drives (like `C:`) are mounted under `/mnt`.
- `mountFsTab = true` (the default) tells WSL to process `/etc/fstab` at startup.
- If you previously added something like `boot.options = ...`, remove it (see Troubleshooting below).

#### Add to `/etc/fstab`
Open the `/etc/fstab` file:
```bash
sudo nano /etc/fstab
```

Add a line to mount the folder automatically.

Important:
- `$(whoami)` does NOT work in `/etc/fstab` (it will be treated as literal text and the mount will fail).
- Use your actual Linux username in the path.

Example (replace `<linux-user>`):
```
C:/repo /home/<linux-user>/repo drvfs metadata,umask=22,fmask=11 0 0
```

Tip: confirm your Linux username with:
```bash
whoami
```

### Restart WSL
Finally, restart WSL to apply the changes.

Run this from Windows (PowerShell / CMD), not inside WSL:
```bash
wsl --shutdown
```

After restarting WSL, the folder `~/repo` will automatically mount to `C:\repo`.

## Option B — Mount to `/mnt/repo` + Symlink into `~/repo` (No Username in `/etc/fstab`)

If you want `~/repo` but don’t want to hardcode `/home/<linux-user>` in `/etc/fstab`, mount to a stable path under `/mnt` and then symlink.

### 1️⃣ Create the Mount Point
```bash
sudo mkdir -p /mnt/repo
```

### 2️⃣ Add to `/etc/fstab`
```bash
sudo nano /etc/fstab
```

Add:
```
C:/repo /mnt/repo drvfs metadata,umask=22,fmask=11 0 0
```

### 3️⃣ Create the Home Shortcut
```bash
mkdir -p ~
ln -sfn /mnt/repo ~/repo
```

### 4️⃣ Restart WSL (from Windows)
```bash
wsl --shutdown
```

After restarting, `~/repo` will point to `/mnt/repo`, which is mounted from `C:\repo`.

---

## Troubleshooting

### `wsl: Unknown key 'boot.options' in /etc/wsl.conf`
This happens when `/etc/wsl.conf` contains a setting that WSL doesn’t support, e.g.:
```
[boot]
options = "..."
```

Fix:
- Edit `/etc/wsl.conf` and delete the `boot.options` line.
- If you need boot-related settings, these are valid examples:
	- Enable systemd:
		```
		[boot]
		systemd = true
		```
	- Run a command on distro startup:
		```
		[boot]
		command = /usr/local/bin/my-startup-script
		```

If your goal was to set kernel command-line options, that is configured in Windows via `.wslconfig` (not in `/etc/wsl.conf`).

### `wsl: Processing /etc/fstab with mount -a failed`
This means at least one line in `/etc/fstab` failed to mount.

Quick checks:
1) Verify the mount point exists:
```bash
mkdir -p ~/repo
```

2) Run mount with verbose output to see the failing line:
```bash
sudo mount -a -v
```

3) Common causes:
- Using `$(whoami)` or other shell syntax in `/etc/fstab`
- Typos in the Windows path (`C:/repo`) or the Linux path (`/home/<linux-user>/repo`)
- Missing drive or folder on Windows

If you want WSL to start cleanly while you debug, you can temporarily disable fstab processing by setting this in `/etc/wsl.conf`:
```
[automount]
mountFsTab = false
```
Then restart WSL with `wsl --shutdown` (from Windows), fix `/etc/fstab`, and re-enable `mountFsTab`.