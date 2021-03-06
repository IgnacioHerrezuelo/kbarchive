---
layout: page
title: "Q184426: Internet Information Server Training Comments and Corrections"
permalink: /kb/184/Q184426/
---

## Q184426: Internet Information Server Training Comments and Corrections

{% raw %}

	Article: Q184426
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocerr
	Last Modified: 07-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft Internet Information Server Training Kit ISBN 1-57231-731-0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information on known errors, corrections, and comments
	relating to the Microsoft Press book Microsoft Internet Information Server
	Training Kit, ISBN 1-57231-731-0.
	
	The following topics are covered:
	
	- Proxy Server Installation Steps Do Not Match Evaluation Edition
	
	- CD-ROM: Internet.exe Has a Large Blank Area on Screen
	
	- Error When Installing NT Option Pack On A Computer With SP4
	
	- Proxy Server Book References Internet Service Manager Instead Of MMC
	
	- Page xxiv: NT 4.0 Service Pack 3 Installation Instructions Incorrect
	
	- Page xxv: Internet Explorer 4.01 Installation Instructions Incorrect
	
	- Pages 6, 45, 53: IIS 4.0 Does Not Include The POP3 Server
	
	- Page 10 (IIS 4.0): Cannot Run Index Server On NT Workstation
	
	- Page 18: Only NT Server Lets You Install All IIS Options
	
	- Pages 18 - 20 (IIS): Corrections To IIS Installation Options
	
	- Pages 21 - 22: Corrections To IIS Installation Instructions
	
	- Page 44: Incorrect Information About LAT
	
	- Page 45-46: IIS Does Not Include Mail Server
	
	- Page 88-89: Step missing when adding a WWW virtual server
	
	- Page 97: Screenshot May Not Match Your Computer
	
	- Page 112: Fifth Default Folder In Mailroot Folder
	
	- Page 124: Corrections to Log File Format Information
	
	- Page 134: Expand Default NNTP Site Before Selecting Directories
	
	- Page 136: Typographical Error
	
	- Page 151: Technical Error
	
	- Page 163: Text Error
	
	- Page 190: Error In Step 5
	
	- Page 213: Delete Step 5 From The Last Procedure
	
	- Page 225: Directory Location Is Not Accurate
	
	- Page 255: Step 2 Should Include "Point to Windows NT 4.0 Option Pack"
	
	- Page 255: "laurel" Can't Log In To "Index Server Sample Query Form"
	
	- Page 270: How To Install SQL Server
	
	- Page 271: Error Message When Installing The Sample Bank Package
	
	- Page 276: URLs For Netshow Sessions Are No Longer Available
	
	- Page 295: Misplaced Line Of Type
	
	- Page 327: The Answer To Question 2 Is Incorrect
	
	- Page 358: The Index Listing For CRL Should Include Page 180
	
	MORE INFORMATION
	================
	
	Proxy Server Installation Steps Do Not Match Evaluation Edition
	---------------------------------------------------------------
	
	The text of the "Microsoft Proxy Server 2.0 Training" book is written assuming
	that the user will be using the full retail version. This is mentioned in the
	introduction to the book.
	
	On page 12, the Proxy Server installation steps are correct as written for the
	retail version of Proxy Server. However, the evaluation version setup process is
	slightly different.
	
	Correction:
	
	Page 12, Step 1:
	
	Add text:
	
	If you are using the evaluation version of Proxy Server included with this kit,
	run the following file from the course compact disc to begin the installation:
	
	  \Software\Proxy\msp2i.exe
	
	A license agreement will appear. Click Yes to accept the evaluation version
	license agreement.
	
	
	CD-ROM: Internet.exe Has a Large Blank Area on Screen
	-----------------------------------------------------
	
	Page 5 indicates that for an overview of Internet concepts, the reader can run
	the Internet.exe presentation file on the course compact disc.
	
	In running this projector on a Win NT system (and on a win 95 system), after the
	initial map dissolved into focus showing internet routes, a large, empty box
	overlays the map for a portion of the presentation. The speaker lists several
	concepts, but these are not bulleted anywhere in the visual display, and the box
	covers most of the display.
	
	There is no resolution for this problem at this time.
	
	Microsoft Press has confirmed this to be a problem and will post further
	information when available.
	
	
	Error When Installing NT Option Pack On A Computer With SP4
	-----------------------------------------------------------
	
	When you install Windows NT Option Pack on a computer that already has Windows NT
	4.0 Service Pack 4 installed, the following message appears:
	
	Setup detected that Windows NT 4.0 SP4 or greater is installed on your machine.
	We haven?t tested this product on SP4. Do you wish to proceed?
	
	Click OK to continue the installation. Once the setup program has completed, and
	the computer has restarted, you can reapply the Windows NT 4.0 Service Pack 4.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q195015 TITLE : XADM: Option Pack Installation Conflicts with
	  Service Pack 4
	
	
	Proxy Server Book References Internet Service Manager Instead Of MMC
	--------------------------------------------------------------------
	
	Proxy Server 2.0 Training refers to IIS 3.0 and Internet Service manager.
	Everything else in this training kit is geared toward IIS 4.0 which uses
	Management Console (MMC) for administration.
	
	MMC is the utility installed with IIS 4.0 included in the training package.
	Unfortunately, this causes discrepancies between the Proxy Server book and the
	actual user interface, as MMC is not covered in the Proxy Server Training book.
	
	IIS 3.0, which uses Internet Service Manager, is no longer available, can not be
	downloaded, and is not on the CDs included with this kit.
	
	
	Page xxiv: NT 4.0 Service Pack 3 Installation Instructions Incorrect
	--------------------------------------------------------------------
	
	Page xxiv, under the subheading To Install Windows NT 4.0 Service Pack 3:
	
	Change:
	"1. From the Windows NT 4.0 Option Pack compact disc, double-click nt4sp3_i.exe
	in the WinntSP3\i386 folder."
	
	To:
	"1. From the course compact disk, double-click nt4sp3_i.exe in the
	Software\WinntSP3\i386 folder.
	
	
	Page xxv: Internet Explorer 4.01 Installation Instructions Incorrect
	--------------------------------------------------------------------
	
	Page xxv, under the subheading To Install Internet Explorer 4.01:
	
	Change:
	"1. From the Windows NT 4.0 Option Pack compact disk, double-click ie4setup.exe
	in the ie401\x86 folder."
	
	To:
	"1. From the course compact disk, double-click ie4setup.exe in the
	Software\ie401\x86 folder."
	
	
	Page 6, 45, 53: IIS 4.0 Does Not Include The POP3 Server
	--------------------------------------------------------
	
	Pages 6, 45, and 53: All three pages reference the POP3 service. Although the
	SMTP server component of IIS 4.0 will support the POP3 email service, the POP3
	server is not included with IIS 4.0.
	
	
	Page 10 (IIS 4.0): Cannot Run Index Server On NT Workstation
	------------------------------------------------------------
	
	Page 10 and 11 of the IIS 4.0 Training book states that you can run Index Server
	on Windows NT Workstation 4.0. This is incorrect. Index Server can only be run
	on Windows NT Server 4.0.
	
	Additionally, neither Microsoft Site Server Express nor Certificate Server can be
	run on Windows NT Workstation 4.0. They can only run on Windows NT Server 4.0.
	
	
	Page 18: Only NT Server Lets You Install All IIS Options
	--------------------------------------------------------
	
	Page 18, Note:
	
	The note on this page states that the different Internet Information Server
	installation options can also be installed on both Windows NT Workstation and
	Windows 95. This is not entirely true, since not all of the IIS installation
	options are available for Windows NT Workstation and Windows 95.
	
	For a complete list of what is not available, please refer to pages 10 and 11,
	under the subheadings Windows NT Workstation and Windows 95. Also, please refer
	to the corrections for page 10 that are included in this Knowledge Base
	article.
	
	
	Pages 18 - 20 (IIS): Corrections To IIS Installation Options
	------------------------------------------------------------
	
	Pages 18 - 20:
	
	The following is a corrected list of what is installed during the Minimum,
	Typical and Custom installations of Internet Information Server on Windows NT
	Server 4.0:
	
	Minimum:
	
	- Internet Information Server. A Web server that uses TCP/IP to host Web sites
	  on the corporate intranet or the Internet.
	
	- Microsoft Transaction Server (MTS). A transaction processing system for
	  developing, deploying, and managing distributed server applications. A
	  transaction is a server operation that succeeds or fails as a whole, even if
	  the operation involves many steps. Microsoft Transaction Server also supports
	  process isolation of applications. The default installation installs the core
	  components and core documentation, but does not install the development
	  components.
	
	- Microsoft Data Access Components. Eases use of databases with support for a
	  variety of connections including Microsoft ActiveX Data Objects with Remote
	  Data Service, and OLE DB. OLE DB is a data-access interface that provides
	  consistent access to Structured Query Language (SQL) and non-SQL data
	  sources.
	
	- Active Server Pages. Enables you to use server-side scripting and components
	  to create browser-independent dynamic content.
	
	- FrontPage Extensions. Allows the use of Microsoft FrontPage to manage your
	  Web site, as well as create the site content. The components installed
	  include everything but the Visual InterDev components.
	
	- Microsoft Management Console (MMC). Provides the ability to custom-design
	  administration tools that "snap-in." Microsoft Management Console creates a
	  uniform look and feel, regardless of the administration tool being used.
	
	- Internet Service Manager snap-in. Offers complete control of your Web and FTP
	  sites with a wizard-driven graphical interface.
	
	- Index Server. Creates a site index and search for text in a variety of
	  formats.
	
	- Context-sensitive Help. Supplies documentation for Microsoft Management
	  Console and context-sensitive Help for the interfaces.
	
	Typical:
	
	- File Transfer Protocol (FTP) Service. Installs the necessary components to
	  operate an FTP Server.
	
	- SMTP Service. Supports SMTP.
	
	- Windows Script Host. Enables you to use Cscript or Wscript to administer
	  servers from the command prompt.
	
	- Internet Service Manager (HTML). Administers your Web and FTP sites from
	  across the intranet or the Internet by using a Web browser.
	
	- Documentation. Provides online documentation covering server administration,
	  content management, and content development, including indexing, scripting,
	  and programming.
	
	- Programmability. The Microsoft Script Debugger provides you with a
	  comprehensive debugging environment for testing and correcting errors in your
	  Web document scripts. You can use Microsoft Script Debugger to debug both
	  client scripts and server scripts.
	
	- Additional Services. The Java Virtual Machine makes it possible to run Java
	  applications on the server.
	
	Custom:
	
	- Site Server Express. Enables you to analyze activity logs to determine site
	  usage statistics and check links on your Web site to be sure they are
	  functioning properly.
	
	- Web Publishing Wizard. Makes sending files to another server for publishing
	  quick and simple.
	
	- Posting Acceptor. Makes it possible for others to upload files to your Web
	  site.
	
	- Additional Documentation. Complete documentation for all of the installable
	  components.
	
	- NNTP Service. Supports NNTP used for discussion groups.
	
	- Certificate Server. Enables you to issue your own client and server
	  certificates.
	
	- Visual InterDev RAD Remote Deployment Support. Enables the remote deployment
	  of applications on your Web server.
	
	- Internet Connection Services for RAS. A set of core Windows NT services that
	  facilitate the creation of secure, seamless virtual private networks (VPNs),
	  and improved dial-up connections.
	
	- Microsoft Message Queue. Allows applications to pass along transaction
	  notification and continue processing without waiting for confirmation that
	  the transaction has completed.
	
	
	Pages 21 - 22: Corrections To IIS Installation Instructions
	-----------------------------------------------------------
	
	Message Queue and Visual InterDev RAD Remote Development Support are not
	components to be selected during the installation of Internet Information
	Server. Installation instructions should be modified to include other minor
	corrections as well.
	
	Corrected installation instructions are as follows:
	
	To install Internet Information Server 4.0:
	
	1. From the course compact disc, double-click setup.exe in the
	  \Software\NTOPTPAK\Winnt.srv folder.
	  The Microsoft Windows NT 4.0 Option Pack Setup dialog box appears.
	
	2. Click Next.
	  The End User License Agreement appears.
	
	3. Click Accept.
	  You are prompted to choose Minimum, Typical, or Custom installation.
	
	4. Click Custom.
	  The options available for installation appear.
	
	5. Scroll down the list and select all the components except Visual InterDev RAD
	  Remote Development Support and Microsoft Message Queue.
	
	6. Select Internet Information Server (IIS).
	
	7. Click Show Subcomponents.
	
	8. Select Internet NNTP Service.
	
	9. Click OK.
	
	10. Click Next.
	  You are prompted for the default publishing folders and the application
	  installation folders.
	
	11. Click Next at each prompt to accept the default folders.
	
	  When the Microsoft Certificate Server dialog box appears, you will need to
	  specify the location.
	
	  To add Microsoft Certificate Server:
	
	12. Type C:\Inetpub in Shared Folder to configure the storage location for
	  Certificate Server. Use the default database location and log location.
	
	13. Click Next.
	
	14. Click OK to create the C:\Winnt\System32\Certlog folder.
	
	You are prompted to enter Identifying Information according to the following
	table.
	
	
	Page 44: Incorrect Information About LAT
	----------------------------------------
	
	On page 44, please remove the third bulleted item.
	
	
	Page 45-46: IIS Does Not Include Mail Server
	--------------------------------------------
	
	The information on pages 45 to 46 could be construed to indicate that Internet
	Information Server is a mail server capable of handling SMTP, POP3 and IMAP
	messages. While Internet Information Server is designed to integrate with other
	Microsoft mail servers such as Microsoft Exchange, Internet Information Server
	is not a mail server itself.
	
	
	Page 88-89: Step missing when adding a WWW virtual server
	---------------------------------------------------------
	
	The virtual server exercise on page 88 and 89 is missing a step. You need to add
	the name of the new virtual server, computernameA, to the HOSTS file for this
	exercise to work.
	
	On page 87, the book indicates that the HOSTS file provides name resolution for
	host names to IP addresses. The HOSTS file can be used as a local DNS
	equivalent, as this kit is designed for self-study and there is only one
	computer being used.
	
	You can find the HOSTS file in the winnt\system32\drivers\etc directory. Since it
	is a simple text file you can use a text editor, such as Notepad, to create or
	change the HOSTS file.
	
	Please Note: A sample versions of a HOSTS files named HOSTS.sam is added to the
	Windows NT \systemroot\System32\drivers\Etc directory when Microsoft TCP/IP is
	installed. This is only an example file; do not use this file as the primary
	HOSTS file.
	
	The HOSTS file format is the same as the format for host tables. For example, the
	entry for a computer with an address of 192.102.73.6 and a host name of
	mfg1.widgets.com looks like this:
	
	131.107.1.240 mfg1.widgets.com
	
	The entry for this exercise can use the server's IP address, or the loopback
	address if you are using DHCP.
	For example:
	
	172.0.0.1 computernameA
	
	The Hosts file does not need to be explicitly referenced anywhere in IIS. It is a
	static file that is used by PING and TCP/IP utilities to resolve the name. It
	resides on each computer and is parsed whenever a host name is referenced. Once
	you have edited the HOSTS file to include the virtual domain that you created in
	this exercise, you will be able to bring the domain up in your browser.
	
	
	Page 97: Screenshot May Not Match Your Computer
	-----------------------------------------------
	
	On page 97, the Screenshot may not match your computer.
	
	The Connection Timeout is 900 in the Screenshot, but If you have done the
	practice exercise on page 35 this will have been changed to 60.
	
	
	Page 112: Fifth Default Folder In Mailroot Folder
	-------------------------------------------------
	
	On Page 112, the first sentence in the second paragraph states that when you
	install SMTP, five default folders are installed in the Mailroot folder. Only
	four are listed in the bulleted items at the bottom of the page.
	
	Add the following item after the last bullet on the page:
	"Mailbox: Stores messages so that they can be retrieved by individual users. This
	is set in mailroot by default, but you can move it to a different location and
	specify a virtual directory path to this directory for each of the mail
	services."
	
	
	Page 124: Corrections to Log File Format Information
	----------------------------------------------------
	
	On Page 124, in the section titled "Monitoring the SMTP Service", the fourth
	bullet is missing.
	
	Add:
	ODBC Logging. A fixed format logged to a database.
	
	Also on this page, in the first paragraph under "Monitoring the SMTP Service",
	the default format should be W3C Extended Log File Format.
	
	Change:
	"The default format is the Microsoft IIS Log File Format."
	
	To:
	"The default format is the W3C Extended Log File Format."
	
	
	Page 134: Expand Default NNTP Site Before Selecting Directories
	---------------------------------------------------------------
	
	On Page 134, under the section titled "To create a virtual directory", in Step 1
	you must first expand Default NNTP Site before you select Directories.
	
	Change:
	"Using either Internet Service Manager or Internet Service Manager (HTML) select
	Directories."
	
	To:
	"Using either Internet Service Manager or Internet Service Manager (HTML) expand
	the Default NNTP Site and select Directories."
	
	
	Page 136: Typographical Error
	-----------------------------
	
	On page 136, in the section titled "To create an expiration policy", add a comma
	to Step 2.
	
	Change:
	"On the Action menu, click New expiration policy."
	
	To:
	"On the Action menu, click New, and then Expiration policy."
	
	
	Page 151: Technical Error
	-------------------------
	
	Page 151, bullet point 3, last sentence:
	
	Change:
	"...but is only supported (at this time) by Internet Explorer 3.0 and later."
	
	To:
	"...but is only supported (at this time) by Internet Explorer 2.0 and later."
	
	
	Page 163: Text Error
	--------------------
	
	Page 163, step 2:
	
	Change:
	"Type c:\cert\newkeyrq.txt"
	
	To:
	"Type notepad c:\cert\newkeyrq.txt"
	
	
	Page 190: Error In Step 5
	-------------------------
	
	In Step 5 on page 190, you should be copying from the New Certificate Request
	file that was generated in the previous chapter.
	
	Change:
	"Copy the contents between and including the following lines:"
	
	To:
	"Copy the contents of the New Certificate Request file, newkeyrq.txt, between and
	including the following lines:"
	
	
	Page 213: Delete Step 5 From The Last Procedure
	-----------------------------------------------
	
	0n page 213, under the section titled "To change the security level of Internet
	Explorer", you can delete Step 5.
	
	This is the last step in the procedure and it instructs you to "Close Internet
	Explorer". This step is not necessary as you will need Internet Explorer open
	for the next exercise.
	
	
	Page 225: Directory Location Is Not Accurate
	--------------------------------------------
	
	Change:
	
	- Sample HTML and script files are copied to /Iissamples/Issamples
	
	- Administration files are copied to /Iisadmin/Isadmin
	
	- Documentation files are copied to /Iishelp/Ix
	
	To:
	
	- Sample HTML and script files are copied to C:\Inetpub\Iissamples\Issamples
	
	- Administration files are copied to C:\System32\Iisadmin\Isadmin
	
	- Documentation files are copied to C:\WINNT\Help\Ix
	
	
	Page 255: Step 2 Should Include "Point to Windows NT 4.0 Option Pack"
	---------------------------------------------------------------------
	
	On page 255, in the section titled "To test the security of Index Server", Step 2
	should include instructions to point to Windows NT 4.0 Option Pack.
	
	Change:
	"Click the Start button, point to Programs, point to Microsoft Index Server, and
	then click Index Server Sample Query Form."
	
	To:
	"Click the Start button, point to Programs, point to Windows NT 4.0 Option Pack,
	point to Microsoft Index Server, and then click Index Server Sample Query
	Form."
	
	
	Page 255: "laurel" Can't Log In To "Index Server Sample Query Form"
	-------------------------------------------------------------------
	
	On page 255, step 3 through 5, user "Laurel" is unable to log onto the "Index
	Server Sample Query Form" page because the user does not have the "log on
	locally" user rights assigned.
	
	You will need to assign the 'log on locally' user rights to the users when you
	create the user account on page 253.
	
	
	Page 270: How To Install SQL Server
	-----------------------------------
	
	The instructions on page 270 of how to install Microsoft SQL Server 6.5 are
	correct for the released version of SQL Server, but are incorrect for the
	evaluation edition included on the Internet Information Server Training Kit
	CD-ROM.
	
	To install the evaluation version of Microsoft SQL Server, follow these steps:
	
	1. On the IIS Training Kit CD-ROM, change to the \Software\Mssql directory.
	
	2. Copy Sqlx86.exe to a temporary directory on your hard drive.
	
	3. From the temporary directory on your hard drive, run the following command:
	
	  Sqlx86.exe -d
	
	Sqlx86.exe is a self-extracting executable file. When run, the file will create a
	directory structure containing all of the files needed to set up the SQL Server
	Evaluation.
	
	1. From the temporary directory, change to the \i386 directory.
	
	2. Run Setup.exe.
	
	The Welcome dialog box should appear. Follow the steps beginning with step 3 on
	page 270 to continue with the installation.
	
	
	Page 271: Error Message When Installing The Sample Bank Package
	---------------------------------------------------------------
	
	On page 271, in the procedure to install the sample bank package, you may receive
	an error message after Step 8 that indicates that the "mts4.cab is missing from
	the installation directory". This file can be found on the CD-ROM that you used
	to install the NT Option Pack.
	
	If you have the first printing of this Training Kit, the file is located on the
	Windows NT Server Evaluation Edition CD-ROM, in the following location:
	
	<cd-rom drive>:\Software\NTOPTPAK\Winnt.SRV
	
	If you have a later printing, the NT Option Pack is included on a seperate CD.
	
	In addition, it is helpful to note that when the Windows NT Option Pack, or
	components, are reinstalled, the latest service pack should also be reapplied.
	
	
	Page 276: URLs For Netshow Sessions Are No Longer Available
	-----------------------------------------------------------
	
	On page 276, the URLs that point to www.audionet.com are no longer available.
	
	
	Page 295: Misplaced Line Of Type
	--------------------------------
	
	On page 295, the second setence in Step 5 needs to be moved up to Step 4. If you
	click OK in Step 5, you will not see the file name anymore.
	
	Change:
	4. Under Log file directory, type the folder in which log files should be saved,
	accept the default if offered, or click Browse and locate the folder.
	5. Click OK.
	A file name is displayed beneath the box showing the folder.
	
	To:
	4. Under Log file directory, type the folder in which log files should be saved,
	accept the default if offered, or click Browse and locate the folder.
	A file name is displayed beneath the box showing the folder.
	5. Click OK.
	
	
	Page 327: The Answer To Question 2 Is Incorrect
	-----------------------------------------------
	
	On page 327, the answer to question 2, from page 12, is incorrect as Index Server
	can not run on workstation.
	
	Change:
	"The component that enables full-text searching is Index Server. Index Server
	works with Internet Information Server running on a computer that runs Windows
	NT Workstation, but is not supported by Internet Information Server running on
	Windows 95."
	
	To:
	"The component that enables full-text searching is Index Server. Index Server
	works with Internet Information Server running on a computer that runs Windows
	NT Server, but is not supported by Internet Information Server running on
	Windows NT Workstation or Windows 95."
	
	
	Page 358: The Index Listing For CRL Should Include Page 180
	-----------------------------------------------------------
	
	On page 358, the index listing for CRL should include page 180.
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: 1-57231-731-0 TKBOOK NTOPTPK NT40
	
	======================================================================
	Keywords          : kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
