---
title: "Mount a remote rsync.net filesystem in Linux"
description: "Mount a remote rsync.net filesystem in Linux"
date: 2026-01-25
tags: [rsync,storage,howto]
categories: [software]
---

[Rysync.net rules for backups](https://rsync.net/)

To mount a remote rsync.net filesystem in Linux, you can use the `rsync` command with the `--mount` option. This option allows you to mount a remote directory as a local filesystem, enabling you to access and manipulate files as if they were on a local disk.

Here's an example command:
```bash
rsync -avz --mount --remote-option=--mount-options=sync=meta,attr rsync://username:password@rsync.net/path/to/remote/directory /local/mount/point
```
Replace:

* `username` and `password` with your actual rsync.net credentials
* `rsync.net/path/to/remote/directory` with the actual path to the remote directory you want to mount
* `/local/mount/point` with the desired local mount point

The `--remote-option` flag specifies the `--mount-options` option, which configures the mount. In this example, `sync=meta,attr` enables metadata and attribute synchronization between the remote and local filesystems.

**Notes:**

* Make sure you have the `rsync` package installed on your Linux system.
* Verify that your rsync.net account has the necessary permissions to access the remote directory.
* The `--mount` option is only available in rsync 3.2.3 and later versions.
* You may need to adjust the `--remote-option` and `--mount-options` flags depending on your specific use case and rsync.net configuration.

After running the command, you should be able to access the remote filesystem at the specified local mount point. You can then use standard Linux commands (e.g., `ls`, `cp`, `mv`, `rm`) to interact with the mounted filesystem. When you're finished, you can unmount the filesystem using the `umount` command.