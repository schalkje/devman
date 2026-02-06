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

[filesystem]
umask = 22
```

#### Add to `/etc/fstab`
Open the `/etc/fstab` file:
```bash
sudo nano /etc/fstab
```

Add the following line to mount the folder automatically:
```
C:/repo /home/$(whoami)/repo drvfs defaults 0 0
```

### Restart WSL
Finally, restart WSL to apply the changes:
```bash
wsl --shutdown
```

After restarting WSL, the folder `~/repo` will automatically mount to `C:\repo`.