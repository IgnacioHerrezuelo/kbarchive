---
layout: page
title: "Q132744: PC Gen: Description of Mail Integrity Check MAILINT.EXE"
permalink: /kb/132/Q132744/
---

## Q132744: PC Gen: Description of Mail Integrity Check MAILINT.EXE

{% raw %}

	Article: Q132744
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 28-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Version 3.5.0 of the Microsoft Mail for PC Networks Mail Integrity Check
	(MAILINT.EXE) utility ships in the version 3.5 Microsoft Mail for PC Networks
	Resource Kit. The utility can be used to check for a variety of missing or
	corrupt mail database files and directories. It is a read-only utility, and it
	does not attempt to fix any files that fail the integrity check. This utility
	can be run while users are working on the postoffice as it does not open or
	write to any mail database files.
	
	MAILINT.EXE consists of the three modules described below: Directory Check, File
	Existence Check, and File Integrity Check. This utility is designed with
	Microsoft Visual Basic version 3.0 and requires VBRUN300.DLL to run.
	
	VBRUN300.EXE is available from the Microsoft FTP Web site. For additional
	information, please see the following article in the Microsoft Knowledge Base:
	
	  Q99251UPD: GP Fault in KRNL286 When Run EXE on 286 or w/ NT on MIPs
	
	
	Also refer to Chapter 5 of the version 3.5 of Microsoft Mail for PC Networks
	Resource Kit for other utilities available.
	
	Directory Check
	---------------
	
	Directory Check will verify the existence of 51 total directories. They include
	the following directories located under the root directory of \MAILDATA:
	
	  \XTN  \CAL
	  \FOLDERS \GLB
	  \GRP     \HLP
	  \INF     \INI
	  \KEY     \LOG
	  \USR     \MBG
	  \MEM     \MMF
	  \NME     \P1
	  \TPL     \MAI
	  \ATT
	
	The following directories located under the \ATT directory of \MAILDATA:
	
	  \AT0  \AT1
	  \AT2  \AT3
	  \AT4  \AT5
	  \AT6  \AT7
	  \AT8  \AT9
	  \ATA  \ATB
	  \ATC  \ATD
	  \ATE  \ATF
	
	And the following directories located under the \MAI directory of \MAILDATA:
	
	  \MA0  \MA1
	  \MA2  \MA3
	  \MA4  \MA5
	  \MA6  \MA7
	  \MA8  \MA9
	  \MAA  \MAB
	  \MAC  \MAD
	  \MAE  \MAF
	
	File Existence Check
	--------------------
	
	The File Existence Check will verify the existence of a core set of Mail
	postoffice files. They include the following files located under the \GLB
	directory of \MAILDATA:
	
	  ACCESS.GLB     ACCESS2.GLB
	  ACCESS3.GLB    CONTROL.GLB
	  GLOBAL.GLB     GROUP.GLB
	  GRPMEM.GLB     MASTER.GLB
	  NETPO.GLB         NETWORK.GLB
	  PROCESS.GLB    REQCONF.GLB
	  RNETSEM.GLB    SRVCONF.GLB
	  TID.GLB
	
	As well as the following files located under the \NME directory of \MAILDATA:
	
	  ADMIN.NME    ADMINSHD.NME
	
	The following files located under the \GRP directory of \MAILDATA:
	
	  ADMIN.GRP    ADMINSHD.GRP
	
	File Check will verify that each existing .KEY file has a corresponding .MBG
	file, and it will verify that each existing .MBG file has a corresponding .KEY
	file.
	
	File Integrity Check
	--------------------
	
	File Integrity Check will compare (calculate) the file size of the following
	files with the correct file size:
	
	  *.GLB     *.GRP
	  *.XTN     *.KEY
	  *.MBG     *.NME
	  *.USR
	
	Please reference the On-line Help Database Description for a list of the files
	and record sizes within each of those files.
	
	Error Messages
	--------------
	
	Below is a list of errors that the utility will detect, along with a description
	for each.
	
	- ADMIN.GRP/ADMINSHD.GRP sizes differ. If the ADMIN.GRP file size differs from
	  the ADMINSHD.GRP, make a backup of ADMIN.GRP, and copy the ADMINSHD.GRP over
	  the ADMIN.GRP.
	
	- ADMIN.NME/ADMINSHD.NME sizes differ. If the ADMIN.NME file size differs from
	  the ADMINSHD.NME, make a backup of ADMIN.NME, and copy the ADMINSHD.NME over
	  the ADMIN.NME.
	
	- Corrupt File. A file is determined to be corrupt if the file size does not
	  divide evenly with the record size for that file. For more information on the
	  record sizes, from the Mail menu, choose Help. Then select Database
	  Description. Please have the Mail Administrator contact Product Support with
	  errors found.
	
	- Directory Is a File. A file exists in the place of a directory. For example,
	  a file with the name AT8 exists in the \ATT directory. AT8 should be a
	  subdirectory of ATT, not a file. Please have the Mail Administrator contact
	  Product Support with errors found.
	
	- Directory Does Not Exist. A directory is missing from the Mail database. Use
	  the MS- DOS MKDIR command to create the missing directory.
	
	- File Does Not Exist. The File Does Not Exist error means that one of the core
	  postoffice files is missing from the Mail database. A list of the files
	  checked are:
	
	     ACCESS.GLB      ACCESS2.GLB
	     ACCESS3.GLB CONTROL.GLB
	     GLOBAL.GLB  GROUP.GLB
	     GRPMEM.GLB  MASTER.GLB
	     NETPO.GLB   NETWORK.GLB
	     PROCESS.GLB REQCONF.GLB
	     RNETSEM.GLB SRVCONF.GLB
	     TID.GLB  ADMIN.NME
	     ADMINSHD.NME   ADMIN.GRP
	     ADMINSHD.GRP
	
	- File Does Not Exist - RNETSEM.GLB. The file RNETSEM.GLB is 4 bytes and is
	  used for synchronizing the generation of RNETWORK.GLB by the External mail
	  program. If this file is missing, the first run of External mail program will
	  create this file.
	
	- KEY Exists Without MBG. Every user will have a hexid.KEY and hexid.MBG file.
	  This program will gather the list of .KEY files and verify a corresponding
	  .MBG file exists. This error will appear when the hexid.MBG file is missing
	  from the MBG directory.
	
	- MBG Exists Without KEY. Every user will have a hexid.MBG and hexid.KEY file.
	  This program will gather the list of .MBG files and verify a corresponding
	  .KEY file exists. This error will show when the hexid.KEY file is missing
	  from the KEY directory.
	
	- Missing SRVCONF.GLB. This file should exist only if the postoffice is the
	  Directory Synchronization (Dir-Sync) server. The SRVCONF.GLB file is the
	  Dir-Sync server's configuration file.
	
	- PO Not Found at <location>. If you receive this error after selecting
	  the start button, then the program could not find a MASTER.GLB in the GLB
	  directory of the path entered into the Location of PO dialog box. Please
	  enter a valid directory for the postoffice.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN350
	Version           : WINDOWS:3.5
	
	=============================================================================
	

{% endraw %}
