---
layout: page
title: "Q185018: XADM: How To Export Public Folder Directory Data To A CSV File"
permalink: /kb/185/Q185018/
---

## Q185018: XADM: How To Export Public Folder Directory Data To A CSV File

{% raw %}

	Article: Q185018
	Product(s): Microsoft Exchange
	Version(s): 4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article explains how to export the directory entries for Microsoft Exchange
	Server public folders.
	
	The Microsoft Exchange Administrator program does not export public folder data.
	In some cases, it may be useful to export the directory attributes associated
	with public folders to manipulate this data and then import it back. You can
	import the .csv file using the Exchange Administrator program.
	
	MORE INFORMATION
	================
	
	The Dsexport.exe utility, which is available in the Microsoft Platform Software
	Development Kit (SDK), can be used to export directory information about public
	folders. Dsexport.exe is located in the Samples\Dbmsg\Exchange\Dsexport
	directory.
	
	Dsexport.exe has some command-line arguments that are not recognized by the
	Microsoft Exchange Administrator Import\Export processor. It is these arguments
	that make this tool particularly useful for dumping objects other than mailbox
	or recipient container objects.
	
	For more information about Dsexport.exe, consult the Microsoft Platform SDK
	documentation.
	
	Using Dsexport.exe:
	
	Dsexport.exe outputs information into a text file as comma separated values
	(CSV). If the target file exists prior to running Dsexport.exe, and this target
	CSV file lists the name of each of the desired object attributes separated by
	commas, the file is used as a template header file when Dsexport.exe is
	executed. This provides the ability to control which object attributes are
	dumped. If the CSV file does not exist, the file will be created with 13 basic
	fields.
	
	1. Copy Dsexport.exe to the \Exchsrvr\Bin directory.
	
	2. In the \Exchsrvr\Bin directory, create a text file called PFlist.csv with
	  only the following single line of text in it:
	
	        Obj-Class,Directory Name,Display Name,E-mail Addresses
	   
	
	  You can add any other attribute you require to the above header line.
	
	3. Execute the following command-line (all on one line) from the \Exchsrvr\Bin
	  directory:
	
	  dsexport /FILE=PFLIST.CSV /DSA=%1 /BASEPOINT=/o=%2/ou=%3
	  /CLASSES=PUBLIC-FOLDER /HIDDEN /SUBTREE
	
	  where:
	
	  %1 = <local exchange servername> (Case sensitive)
	  %2 = <organization name> (Case sensitive)
	  %3 = <site name> (Case sensitive)
	
	This will result in a PFList.csv file that includes one line for each public
	folder in the site.
	
	In order to export a list of all public folders in the entire Exchange
	organization instead of for one particular site, use the following command line
	(all on one line):
	
	  "dsexport /FILE=PFLIST.CSV
	  /DSA=%1/BASEPOINT=/o=%2/CLASSES=PUBLIC-FOLDER/HIDDEN /SUBTREE" (without the
	  quotation marks)
	
	Additional query words: print public folder hierarchy
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : :4.0,5.0,5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
