---
layout: page
title: "Q107131: WFWG: Creating a New SYSTEM.INI Without Third-Party Drivers"
permalink: /kb/107/Q107131/
---

## Q107131: WFWG: Creating a New SYSTEM.INI Without Third-Party Drivers

{% raw %}

	Article: Q107131
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): WINDOWS:3.1,3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	You can use your original Microsoft Windows for Workgroups version 3.1 or 3.11
	disks to create a new SYSTEM.INI file for your specific hardware and version of
	the network operating system.
	
	Creating a new SYSTEM.INI file can be useful for troubleshooting or for replacing
	a damaged or deleted SYSTEM.INI file.
	
	MORE INFORMATION
	================
	
	To create a new SYSTEM.INI file that does not contain references to third-
	party device drivers but that is configured for your specific hardware, do
	the following:
	
	1. Rename the SYSTEM.INI file to SYSTEM.BKP.
	
	2. Expand the file SYSTEM.SR_ from the original Windows for Workgroups
	   3.1 or 3.11 disks to your Windows directory (usually C:\WINDOWS) by
	   typing the following at the MS-DOS command prompt and pressing
	   ENTER:
	
	      c:\windows\expand a:system.sr_ c:\windows\system.ini
	
	   NOTE: For Windows for Workgroups 3.1, this file is located on Disk 3
	   for both the 1.44-megabyte (MB) 3.5-inch and 1.2-MB 5.25-inch disk
	   sets. For Windows for Workgroups 3.11, this file is located on Disk 2
	   for both the 1.44-MB 3.5-inch and 1.2-MB 5.25-inch disk sets.
	
	3. Change to the Windows for Workgroups drive and then change to the
	   Windows directory. For example, at the MS-DOS command prompt, type
	   the following, pressing ENTER after each line:
	
	      c:
	      cd \windows
	
	4. To start the MS-DOS portion of Windows for Workgroups Setup, type
	   "setup" (without the quotation marks) at the MS-DOS command prompt.
	
	5. The options are either blank or contain some incorrect defaults
	   similar to the following:
	
	      Keyboard:   keyboard.typ
	      Codepage:   woafont.fon
	
	   Select the correct hardware options for your system.
	
	6. Accept the changes.
	
	   NOTE: When you accept the changes, you are given the option to have
	   Setup copy new drivers.
	
	7. Open the new SYSTEM.INI file in a text editor, such as MS-DOS 6.0
	   or 6.2 Editor. Make the following changes to the SYSTEM.INI file:
	
	    - Add PROGMAN.EXE to the SHELL= line in the [boot] section.
	
	    - Remove or remark out the TASKMAN.EXE= line in the [boot]
	      section.
	
	    - Add the following NETWORK.DRV= line to the [boot] section:
	
	         [boot]
	         Network.drv=wfwnet.drv
	
	    - For Windows for Workgroups 3.1, change the network= line in the
	      [386Enh] section to the following:
	
	         [386Enh]
	         network=vnetbios.386,vnetsup.386,vredir.386,vserver.386,
	         vbrowse.386,vwc.386
	
	    - For Windows for Workgroups 3.11, change the network= line in the
	      [386Enh] section to the following:
	
	         [386Enh]
	         network=*vnetbios,vnetsup.386,vredir.386,vserver.386,*vwc
	
	      NOTE: The network= setting in the [386Enh] section of the SYSTEM.INI
	      file should be on one line and should not contain spaces or wrapping
	      around the second line.
	
	   - To enable 32-bit disk access, add the following lines to the
	     [386Enh] section:
	
	        32BitDiskAccess=<Boolean>
	        device=*int13
	        device=*wdctrl
	
	     NOTE: To enable 32-bit disk access, replace <Boolean> with "True"
	     (without the quotation marks). If you do not want 32-bit disk access
	     enabled, replace <Boolean> with "False" (without the quotation
	     marks).
	
	     For more information about 32-bit disk access, see Appendix D in
	     the Windows Resource Kit, or query on the following words in the
	     Microsoft Knowledge Base:
	
	         Windows and 3.1 and 32-bit and disk and access
	
	8. Start Windows for Workgroups without attempting to load any network
	   drivers:
	
	   - To start Windows for Workgroups 3.1 in standard mode, type the
	     following at the MS-DOS command prompt:
	
	     win /s
	
	     NOTE: Standard mode is not accessible in Windows for Workgroups
	     3.11.
	
	   - For Windows for Workgroups 3.11, type the following at the MS-DOS
	     command prompt:
	
	     win /n
	
	9. In the Main group, choose Control Panel and then choose the Network
	   icon.
	
	   For Windows for Workgroups 3.11, open the SYSTEM.INI file in a text
	   editor, such as Notepad.
	
	10. Add the workgroup and computer names.
	
	   For Windows for Workgroups 3.11, add the ComputerName= and Workgroup=
	   settings in the [Network] section.
	
	11. In Windows for Workgroups 3.1, do the following:
	
	   - Choose the Adapters button.
	
	   In Windows for Workgroups 3.11, do the following:
	
	   - Choose the Network Setup icon in the Network group, then choose the
	     Drivers button.
	
	12. Add the network interface card (NIC).
	
	   NOTE: You may need to first remove and then reinstall the NIC driver.
	
	13. When Windows prompts you to restart the computer, choose the
	   Continue button.
	
	14. Exit Windows and restart Windows in 386 enhanced mode.
	
	
	Additional query words: 3.10 3.11 re-create recreate rebuild rebuilding system.src 3rdparty clean
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW310 kbWFW311
	Version           : WINDOWS:3.1,3.11
	
	=============================================================================
	

{% endraw %}
