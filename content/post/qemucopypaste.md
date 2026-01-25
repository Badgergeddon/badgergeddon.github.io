---
title: "To enable copy-paste between a QEMU host and guest"
description: "To enable copy-paste between a QEMU host and guest"
date: 2026-01-25
tags: [qemu,software,howto,virtualization]
categories: [software]
---

To enable copy-paste between a QEMU host and guest, install `spice-vdagent` (or guest tools) in the guest OS, ensure it's running, and use the SPICE display protocol for seamless clipboard sharing, often requiring the `virtio-serial` device and correct QEMU arguments in your setup. For Windows guests, you may also need to install VirtIO drivers, and for Linux guests, ensure the service starts correctly after X starts. 

For Linux Guests (e.g., Ubuntu, Fedora)

1. **Install Agent:** In the guest VM, run `sudo apt install spice-vdagent` (Debian/Ubuntu) or `sudo dnf install spice-vdagent` (Fedora).
2. **Ensure Service is Running:** The agent usually starts automatically, but you might need to run `sudo systemctl start spice-vdagent` or add it to startup.
3. **Use SPICE:** Ensure your QEMU setup uses the SPICE display protocol (e.g., `-display spice`) and includes `virtio-serial` devices for communication. 

For Windows Guests (e.g., Windows 10/11)

1. **Install VirtIO Drivers:** Download and install the VirtIO guest tools (virtio-win-pkg) from Fedora's website for the necessary Spice Guest Driver and VirtIO Serial driver.
2. **Install Agent:** Install `spice-vdagent` within the guest after the drivers are in place.
3. **Check Service:** Verify the `spice-vdagent` service is running in Windows Services.
4. **Use SPICE:** Use SPICE for display and ensure the correct QEMU arguments for `virtio-serial` are set. 

For Both & General Troubleshooting

- **Restart:** Restart the guest VM and potentially the host's `virt-manager` (if used) after installation.
- **QEMU Arguments:** When launching QEMU, ensure you have lines like these for the host to pass to the guest:
    
    ```
    -device virtio-serial-pci \
    -chardev spicevmc,id=charchannel1,name=vdagent \
    -device virtserialport,chardev=charchannel1,id=channel1,name=com.redhat.spice.0
    ```
    
- **Alternative (Manual):** If all else fails, you can use standard copy-paste, but you might need to click the VM's title bar first, then click inside the guest before pasting (less reliable).
- **Drag & Drop:** For file transfers, drag-and-drop often works with the same setup (spice-vdagent + virtio drivers).#