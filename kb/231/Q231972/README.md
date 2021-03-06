---
layout: page
title: "Q231972: How to Set Up Your Windows NT Network File System Server"
permalink: /kb/231/Q231972/
---

## Q231972: How to Set Up Your Windows NT Network File System Server

{% raw %}

	Article: Q231972
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbnetwork kbtool
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, used with:
	   - Microsoft Windows NT Services for UNIX Add-On Pack 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides an example of a simple network file system (NFS) server
	configuration that may be useful for a system administrator. Note that you can
	build on this configuration or customize it as needed. This configuration uses a
	local password file for authentication instead of the network information
	service (NIS).
	
	MORE INFORMATION
	================
	
	To create a simple network file system (NFS) server configuration:
	
	1. Choose an NTFS partition to work with.
	
	  NOTE: NTFS provides file-level security that does not exist with FAT.
	
	2. Create a new folder to share, create a file in this folder, right-click the
	  new folder, and then click Properties.
	
	3. Click the Security tab, click Permissions, and then click to select the
	  "Replace Permissions on Subdirectories" check box.
	
	4. Click to select the "Replaced Permissions on Existing Files" check box. Click
	  the individual permissions under the Name area one at a time, and then press
	  Remove to delete them.
	
	5. Click Add, click Show Users, click Everyone, click the administrators group
	  and the user named administrator, and then click Add. Change the type of
	  access to FULL CONTROL, click OK, click OK, click YES to replace permissions,
	  and then click OK.
	
	6. Click Start, point to Programs, point to "Windows NT Services for UNIX", and
	  then click "Server for NFS". Click the NFS Client Groups tab, press ALT+G to
	  add a group, type "AllowedHosts" (without the quotation marks) for the Group
	  Name, and then click OK. Press ALT+M to add a member to this group, type the
	  hostname or IP address of your NFS client, click OK, and then click Apply.
	  Note that you cannot use wildcard characters.
	
	7. Click the Share Options tab, type the full path to the folder you created in
	  step 2, and then click Share. Change the type of access to No Access, press
	  ALT+A to add the client group you previously created, click AllowedHosts, and
	  then click Add. Now decide whether to grant root privileges, or configure for
	  an anonymous user:
	
	   - Root as root: Press ALT+A to add, set the type of access to Root, click
	     OK, and then click OK.
	
	   - Root as anonymous: Press ALT+A to add, set the type of access to
	     Read-Write, click OK, and then click OK.
	
	8. On the Share Options tab, press ALT+Y, and then click Apply.
	
	9. Press ALT+O to configure user/group mappings, press ALT+E to edit your
	  password file and enter the following information:
	
	  New User Name is root
	  New User UID is 0
	  New User GID is 1 (Solaris uses 1, BSD uses 0)
	
	10. Press ALT+A to add, and then press ALT+O. Click "root(0)" under NFS Users,
	  and then click Administrator under Windows Users. Press ALT+D to add the
	  mapping, and then press ALT+A to apply your changes.
	
	11. Log on to your UNIX NFS client as root. Verify you can see the NT NFS Server
	  share by using the showmount command with the "-e <NT server name>"
	  parameter, where <Windows NT server name> is the name or IP address of
	  the Windows NT NFS Server. Your command should look like this:
	
	  #showmount -e <Windows NT server name>
	
	  Exports list on sfu:
	
	  /F/home/sfu , 192.168.105.80
	
	12. Mount the drive to verify functionality with syntax similar to this:
	
	  mount NTSERVER:/f/home/sfu /mnt
	
	  List the files in the export:
	
	  ls -la
	
	  total 3
	  drwxrwxrwx 3 root root 96 May 26 11:53 .
	  drwxr-xr-x 36 root root 1024 May 25 16:26 ..
	  -rwxrwxrwx 1 root root 0 May 26 11:53 testfile
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork kbtool 
	Technology        : kbWinNTsearch kbWinNTSsearch
	Version           : winnt:4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
