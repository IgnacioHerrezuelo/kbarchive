---
layout: page
title: "Q175278: How to Install Additional Drives on the Shared SCSI Bus"
permalink: /kb/175/Q175278/
---

## Q175278: How to Install Additional Drives on the Shared SCSI Bus

{% raw %}

	Article: Q175278
	Product(s): Microsoft Windows NT
	Version(s): 2000,4.0
	Operating System(s): 
	Keyword(s): kbsetup
	Last Modified: 15-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Windows 2000 Advanced Server 
	- Microsoft Windows 2000 Datacenter Server 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	If you want to add additional drives to an existing cluster, special procedures
	may be necessary. This article discusses how to add additional drives on a
	shared SCSI bus when the system does not support hot swapping.
	
	MORE INFORMATION
	================
	
	
	Unless your drive cabinet supports hot swapping, you must shut down and turn off
	both cluster nodes to add or replace SCSI drives because the shared SCSI bus is
	disconnected during this procedure. If you Disconnect the bus while the cluster
	is in use, you may experience data loss or other failures. Microsoft recommends
	that you turn off all attached hardware while you perform this procedure.
	
	To add additional drives to an existing cluster:
	
	1. Change the startup values for the Clusdisk device and the Cluster Server
	  service:
	
	   - Change the Startup value for the Cluster Disk device (Microsoft Windows NT
	     4.0) or the Clusdisk device (Microsoft Windows 2000) to Disabled.
	   - Change the Startup value for the Cluster Server service to Disabled.
	
	To do so, use the appropriate method for your version of Microsoft Windows.
	
	Windows NT 4.0
	--------------
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. Double-click Devices.
	
	  c. In the list of devices, click Cluster Disk, and then click Startup.
	
	  d. Change the setting to Manual, click OK, and then click Yes.
	
	  e. Close the Devices window.
	
	  f. In Control Panel, double-click Services.
	
	  g. In the list of services, click Cluster Server, and then click Startup.
	
	  h. Change the setting to Manual, click OK, and then click Yes.
	
	  i. Close the Services window, and then close Control Panel.
	
	Windows 2000
	------------
	
	  a. Click Start, point to Programs, point to Administrative Tools, and then
	     click Computer Management.
	
	  b. In the left pane, click Device Manager.
	
	  c. On the View menu, click Show Hidden Devices.
	
	  d. In the right pane, under the Non-Plug and Play Drivers branch,
	     double-click Clusdisk.
	
	  e. Click the Driver tab.
	
	  f. In the Type box, click Disabled, and then click OK.
	
	  g. In the left pane, click the plus sign (+) next to "Services and
	     Applications" to expand the branch.
	
	  h. Under the "Services and Applications" branch, click Services.
	
	  i. In the right pane, double-click the Cluster service.
	
	  j. In the "Startup type" box, click Disabled, and then click OK.
	
	  k. Close the Computer Management tool.
	
	2. Shut down both nodes and turn off both computers.
	
	3. Turn off SCSI devices on the shared SCSI bus.
	
	4. Add or replace drives on the shared SCSI bus.
	
	5. Make sure that every device on the shared SCSI bus has a unique SCSI ID.
	
	  NOTE: Remember that the two SCSI host adapters each use a different SCSI ID
	  (usually 6 and 7).
	
	6. Make sure that the bus is terminated properly.
	
	7. Restart node 1 and allow the boot process to complete. Turn on node 2 and
	  press the SPACEBAR when the OS Loader screen appears.
	
	  NOTE: Do not allow Windows NT to start on the second node.
	
	8. On the first node, use Windows NT Disk Administrator (Windisk.exe) to
	  partition and format the drive, and then assign drive letters to the new
	  disks that are available on the shared SCSI bus.
	
	9. Select the partition, click Properties on the Tools menu, and then label the
	  partition to match its corresponding drive letter. For example, the label for
	  drive E drive should be "E". Repeat this for each partition.
	
	10. On the Partition menu, click Configuration, and then click Save.
	
	11. Restore the original startup values for the Clusdisk device and the Cluster
	  Server service:
	
	   - Change the Startup value for the Cluster Disk device or Clusdisk device to
	     System.
	   - Change the Startup value for the Cluster Server service to Automatic.
	
	  To do so, use the appropriate method in step 1 for your version of Windows.
	
	12. Restart node 1, press the SPACEBAR when the OS Loader screen appears to
	  pause the startup process.
	
	13. Select the operating system you want, and then allow Node 2 to start.
	
	  NOTE: Do not allow Windows NT to start on node 1.
	
	14. On the second node, run Windows NT Disk Administrator (Windisk.exe) for
	  Windows NT 4.0 or Disk Management (diskmgmt.msc) for Windows 2000 and
	  Windows .NET, and then assign drive letters to the new disks available on
	  the shared SCSI bus. These drive letters should match the drive labels
	  created in step 9.
	
	15. Restore the original startup values for the Clusdisk device and the Cluster
	  Server service:
	
	   - Change the Startup value for the Cluster Disk device or Clusdisk device to
	     System.
	   - Change the Startup value for the Cluster Server service to Automatic.
	
	  To do so, use the appropriate method in step 1 for your version of Windows.
	
	16. Restart node 2 (allow it to do a full restart).
	
	17. Create a physical disk resource for each new disk using Cluster
	  Administrator and bring the disks online.
	
	18. If there are no errors, select the Windows NT Server operating system on the
	  second node and press ENTER. If there are errors, check the SCSI cabling,
	  termination, and SCSI ID assignment for proper configuration.
	
	19. When the node comes online and appears so in Cluster Administrator, try
	  moving the group to the node. Check for the ability to go online on each
	  node.
	
	NOTE: For additional information, consult Chapter 4 of the MSCS Administrator's
	Guide, or the Support/Books folder on CD-ROM 1.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup 
	Technology        : kbWinNTsearch kbWinNT400search kbwin2000AdvServ kbwin2000AdvServSearch kbwin2000DataServ kbwin2000DataServSearch kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbwin2000Search kbWinAdvServSearch kbWinDataServSearch
	Version           : :2000,4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
