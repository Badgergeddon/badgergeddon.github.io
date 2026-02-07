---
title: Cosmic Files
description: Cosmic files
date: 2026-02-07
tags: [cosmic, popos, files]
categories: [software]
---

COSMIC Files (the file manager for System76's new
COSMIC Desktop Environment) is currently in alpha/beta development, and its Samba (SMB) support is a known area of active work with several reported issues. 
If your Samba shares are broken or won't connect, here are the most common causes and fixes:
1. Missing Dependencies
On some distributions, COSMIC Files requires specific backends to handle network protocols like SMB. 

    Fix: Ensure you have the necessary gvfs packages installed. Users have reported that installing gvfs-smb or similar backends is required for Samba access to function in the file manager. 

2. Silent Failures when Mounting 
A common bug involves the GUI dialog for mounting a Samba share "silently failing." You might enter your credentials, but the share never appears in the sidebar. 

    **Workaround: Try connecting via the terminal or using an alternative file manager (like Nautilus or Thunar) to verify the server is reachable. If it works elsewhere, it is a known bug in cosmic-files.** 

**I went for Nautilus - Cosmic files and Samba IS just a bit too buggy at the moment**

3. Permission and Lock Issues
Users have reported that even when shares are successfully mounted, files may appear "locked" or cannot be edited. 

    Status: This is an open issue in the COSMIC Files GitHub repository. System76 frequently releases updates to the cosmic-epoch packages; ensure your system is fully updated to receive the latest fixes. 

4. Broken Sidebar Links
If you previously had a Samba share pinned and it now opens in a text editor or fails to load, the sidebar entry might be corrupted. 

    Fix: Right-click the entry to remove it and try re-adding the network location manually. 

For persistent issues, you can track development or report new bugs on the official COSMIC Files GitHub Issues page. 
Are you seeing a specific error message when you try to connect, or is the share simply not appearing?