---
layout: page
title: "Q103945: PC Mac: Macintosh Client Version 3.0.6 Update"
permalink: /kb/103/Q103945/
---

## Q103945: PC Mac: Macintosh Client Version 3.0.6 Update

{% raw %}

	Article: Q103945
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0,3.0a,3.0b,3.2,3.2a
	Operating System(s): 
	Keyword(s): kbgraphxlinkcritical
	Last Modified: 21-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.0, 3.0a, 3.0b, 3.2, 3.2a, on platform(s):
	   - the operating system: Mac OS (ALL) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft provides a replacement for the Macintosh client file that is included
	with versions 3.0, 3.0a, 3.0b, 3.2, and 3.2a of Microsoft Mail for PC Networks.
	
	For complete information about obtaining and installing the Macintosh client
	file, see the following sections:
	
	- To download the updated file
	
	- To update your Macintosh client file
	
	MORE INFORMATION
	================
	
	This update contains the Macintosh client file, a replacement for the Macintosh
	client file included with versions 3.0, 3.0a, 3.0b, and 3.2 of Microsoft Mail
	for PC Networks. This update includes the following modifications:
	
	- With the earlier version of this file, the computer could stop responding
	  when sending a message to a personal group under low memory conditions. The
	  Macintosh client file has been modified to correct this problem.
	
	
	- Some network operating systems will not allow a file to be created in all
	  uppercase letters. The Macintosh client file has been modified for these
	  types of networks to allow the client to create filenames in lowercase
	  letters if LOWRCASE.GLB exists in the GLB subdirectory of the Mail database.
	
	
	- With the earlier version of this file, when mail is sent to global groups
	  that contain nonalphabetic characters in their names, the recipient field
	  appears blank when the message is viewed by a Mail for Windows user. The
	  Macintosh client file has been modified to correct this problem.
	
	
	This replacement file also resolves the following problems that can occur when
	you use version 3.0, 3.0a, 3.0b, 3.2, or 3.2a of Microsoft Mail for PC
	Networks:
	
	- Extended template information that exceeds 64K is now correctly displayed
	  when you choose the Info button in the Addressing dialog box of the Macintosh
	  client.
	
	- The Macintosh client has been modified to enable you to address mail to an
	  X.400 recipient when the address exceeds 52 characters. Attempting to do this
	  with previous versions of the Macintosh client could produce the following
	  error message:
	
	  The application "unknown" has unexpectedly quit, because an error of type 1
	  occurred. OK?
	
	- If you attempt to forward a message in the Macintosh client, and you choose
	  not to forward an attachment to that message, the following error message is
	  generated:
	
	  Low on Memory. Unable to complete the operation. Please close some windows.
	
	  The Macintosh client has been modified to forward the message without
	  generating the error.
	
	
	- On a Power Macintosh, if the check box Open "To" Address Selector (from the
	  Compose menu, select Get Info) is selected, and you attempt to forward or
	  reply to a message, the following error message is generated and can hang the
	  machine:
	
	  The system has closed the following application "Unknown" because of an error
	  type 1".
	
	  The Macintosh client has been modified to forward or reply to a message
	  without generating the error or hanging the machine.
	
	
	To download the updated file
	----------------------------
	
	The following file is available for download from the Microsoft Download Center:
	
	  DownloadDownload Maclient.hqx now
	  (http://download.microsoft.com/download/pcmail/Update/4/MacOS/EN-US/Maclient.hqx)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	You should receive the following files:
	
	Microsoft Mail (414,806 bytes, dated 02-15-95, 9:14 P.M.)
	README.TXT
	
	To update your Macintosh client file
	------------------------------------
	
	NOTE: The Macintosh client file is in a self-extracting archive (.SEA) format as
	well as in Bin-Hex (.HQX) format to allow you to use an MS-DOS- formatted disk.
	To access the workstation software, you need to decode the file using a decoding
	utility, such as StuffIt or Compact Pro. These utilities can be found on most
	major bulletin boards, such as America Online and AppleLink.
	
	From an IBM or compatible computer
	----------------------------------
	
	1. At the MS-DOS command prompt, type the following and press ENTER
	
	  " copy <path>:\maclient.hqx <destination> " (without the
	  quotation marks)
	
	  where <path> is the drive and directory where you downloaded the
	  MACLIENT.HQX file and <destination> is the drive and directory where
	  your postoffice currently resides. For example, if you downloaded the file to
	  the TEST directory on drive D and the postoffice is located in the MAILDATA
	  directory on drive C, type the following command:
	
	  " copy d:\test\maclient.hqx c:\maildata " (without the quotation marks)
	
	2. From a Macintosh that has access to the Mail postoffice share, use one of the
	  decoding utilities, such as StuffIt or Compact Pro, to decode the file into
	  its original format by doing the following:
	
	   - To use StuffIt: From the Other menu, choose Bin-Hex. Then select Decode
	     Bin-Hex File.
	
	  -or-
	
	   - To use Compact Pro: From the Misc menu, choose Convert FROM BinHex4.
	
	  The utility will generate a Macintosh file called MACLIENT.SEA in the same
	  location as the original file.
	
	3. Each Macintosh user can then use AppleShare to update his or her subdirectory
	  of the postoffice to the local Macintosh.
	
	  The MACLIENT.SEA file is a self-extracting archive. Double-click the icon to
	  extract the Microsoft Mail file.
	
	From an Apple Macintosh
	-----------------------
	
	1. If you download MACLIENT.SEA, go to step 2.
	
	  If you download the .HQX file, use one of the decoding utilities, such as
	  StuffIt or Compact Pro, to decode the file into its original format by doing
	  the following:
	
	   - To use StuffIt: From the Other menu, choose Bin-Hex. Then select Decode
	     Bin-Hex File.
	
	  -or-
	
	   - To use Compact Pro: From the Misc menu, choose Convert FROM BinHex4.
	
	  The utility will generate a Macintosh file called MACLIENT.SEA in the same
	  location as the original file.
	
	2. Copy the file to a share that each Macintosh user has access to, such as the
	  MAILDATA subdirectory of the postoffice. Then using AppleShare, each
	  Macintosh user can update his or her Mail client software by copying
	  MACLIENT.SEA from the MAILDATA subdirectory of the postoffice to the local
	  Macintosh and double-clicking it to extract the Macintosh file.
	
	Additional query words: 3.00 3.00a 3.00b 3.20 BugList3.00a BugList3.00b KBCategory: kbenv kbfile kbtlc kbbug3.00 kbbug3.20 kbbug3.20a kbfix3.20a
	
	======================================================================
	Keywords          : kbgraphxlinkcritical 
	Technology        : kbMailSearch kbZNotKeyword3
	Version           : WINDOWS:3.0,3.0a,3.0b,3.2,3.2a
	
	=============================================================================
	

{% endraw %}
