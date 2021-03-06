---
layout: page
title: "Q104844: Changes to Windows NT Driver Library: Storage"
permalink: /kb/104/Q104844/
---

## Q104844: Changes to Windows NT Driver Library: Storage

{% raw %}

	Article: Q104844
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5
	Operating System(s): 
	Keyword(s): kb3rdparty kbhw kbHardware
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.5 
	- Microsoft Windows NT Server version 3.5 
	-------------------------------------------------------------------------------
	
	- THESE DRIVERS ARE TESTED AND CERTIFIED WITH WINDOWS NT VERSION 3.5 ONLY -
	
	SUMMARY
	=======
	
	Below is a summary of the changes to the storage device drivers in the Microsoft
	Windows NT Driver Library (WNTDL). The WNTDL offers support for several
	printers, displays, and network adapter cards not provided with Windows NT
	version 3.1.
	
	For additional information about WNTDL, please click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q100209 Windows NT 3.5 Driver Library
	
	NOTE: Wntdl.txt contains a complete listing of the WNTDL's contents and
	instructions for obtaining the WNTDL.
	
	MORE INFORMATION
	================
	
	SCSI: AMD PCNet/SCSI Embedded 1.95 (AMD.EXE) S14890
	---------------------------------------------------
	
	09/23/94 - AMD.EXE version 1.95 has been added to the WNTDL. This driver supports
	the embedded AMD PCNet/SCSI adapter. This driver has been tested with the Compaq
	Deskpro XL 466 and the HP Vectra XU 5/90c.
	
	SCSI: AMI Series48 EISA 1.03 (AMI48.EXE) S14522
	-----------------------------------------------
	
	09/23/94 - AMI48.EXE has been updated on the WNTDL. This driver supports the AMI
	Series 48 cache and non-cache adapters.
	
	03/11/94 - AMI48.EXE has been updated on the WNTDL. The AMI SCSI driver is for
	use with the AMI EISA SCSI Series 48 and Series 441.
	
	01/31/94 - American Megatrends, Inc. SCSI driver for use with AMI EISA noncaching
	SCSI Series 48.
	
	SCSI: ASP ABP-842 VLB 3.10 (ASP.EXE) S14891
	-------------------------------------------
	
	09/23/94 - ASP.EXE has been added to the WNTDL. This driver supports the Advanced
	System Products ABP-842 adapter.
	
	SCSI: CMD CSA-6000/F EISA 1.1 (CMD600.EXE) S14629
	-------------------------------------------------
	
	09/23/94 - CMD600.EXE has been updated on the WNTDL. This driver supports the CMD
	CSA-6000/F adapter.
	
	03/11/94 - CMD600.EXE has been added to the WNTDL. The CMD SCSI driver is for use
	with the CSA-6000 SCSI controller.
	
	SCSI: Exabyte 2501 Tape Driver (EX2501.EXE) S14785
	--------------------------------------------------
	
	06/09/94 - EX2501.EXE has been added to the WNTDL. This driver supports the
	Exabyte 2501 SCSI tape drive.
	
	SCSI: IBM IBMRAID MCA 3.10 (IBMRAD.EXE) S14892
	----------------------------------------------
	
	09/23/94 - IBMRAD.EXE has been added to the WNTDL. This driver supports the IBM
	RAID adapter.
	
	SCSI: Procom Xelerator ISA 3.10 (PRXEL.EXE) S14470
	--------------------------------------------------
	
	09/23/94 - PRXEL.EXE has been updated on the WNTDL. This driver supports the
	Procom Technology ISA SCSI Xelerator adapter.
	
	12/28/93 - This file is new to the WNTDL and supports the Procom Tech SCSI
	Xelerator adapter. It is an NDIS 3.0 network adapter driver for use with the NCR
	WaveLAN AT and MCA adapters.
	
	SCSI: QLogic Fast!SCSI Family 3.10 (QLOGIC.EXE) S14783
	------------------------------------------------------
	
	09/23/94 - QLOGIC.EXE has been updated on the WNTDL. This driver supports the
	QLogic EISA, ISA, and VLB adapters.
	
	06/09/94 - QLOGIC.EXE has been added to the WNTDL. This is a SCSI mini-port
	driver for use with QLogic EISA, ISA, and VL controllers.
	
	SCSI: QLogic Fast!SCSI PCI 3.5 (QLPCI.EXE) S14893
	-------------------------------------------------
	
	09/23/94 - QLPCI.EXE has been added to the WNTDL. This driver supports the QLogic
	Fast!SCSI PCI adapter.
	
	SCSI: Rancho RT1600-5 ISA 2.10 (RANCHO.EXE) S14894
	--------------------------------------------------
	
	09/23/94 - RANCHO.EXE has been added to the WNTDL. This driver supports the
	Rancho Technology RT1600-5 SCSI adapter.
	
	SCSI: Sankyo Tape Driver (SANKYO.EXE) S14639
	--------------------------------------------
	
	03/11/94 - SANKYO.EXE has been added to the WNTDL. This driver provides support
	for Sankyo tape drives CP150SE, CP525SE, and CP1000SE.
	
	SCSI: Tekram DC-820C EISA 3.10 (DCSCSI.EXE) S15217
	--------------------------------------------------
	
	03/17/95 - DCSCSI.EXE has been added to the WNTDL. This SCSI driver supports the
	Tekram DC-820C EISA adapter board on X86 systems.
	
	Sony 31A MIPS Driver (S31AM.EXE) S14234
	---------------------------------------
	
	08/20/93 - S31AM.EXE has been added to the WNTDL. This file contains the MIPS
	storage driver for the Sony 31A drive and a license agreement. See WNTDL.TXT for
	specific devices supported by this driver.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kb3rdparty kbhw kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS350 kbWinNTS350search
	Version           : winnt:3.5
	
	=============================================================================
	

{% endraw %}
