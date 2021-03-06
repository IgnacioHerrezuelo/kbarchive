---
layout: page
title: "Q257876: HOWTO: Allow Printing from an Exchange Event Script"
permalink: /kb/257/Q257876/
---

## Q257876: HOWTO: Allow Printing from an Exchange Event Script

{% raw %}

	Article: Q257876
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): kbExchange550 kbMsg kbEvent
	Last Modified: 16-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates one way to print a log or other simple document from
	an Exchange Server event script. This example uses a COM object to implement the
	printing functionality by way of the Print Object. In addition, the account
	under which the Exchange Event Service runs must have a default printer
	installed.
	
	MORE INFORMATION
	================
	
	On the Exchange Server, the Exchange Event Service runs under a specific
	account, usually the Exchange Service Account. In order for printing to succeed
	from an event script, the account requires a default printer in its registry
	hive.
	
	1. In Control Panel, open the Services applet, select the Microsoft Exchange
	  Event Service, and then open the Startup dialog box. Note which account the
	  service runs under.
	
	2. Open User Manager (Programs/Administrative Tools (Common)/User Manager for
	  Domains). View the domain in which the Exchange server resides. Add the
	  account noted in step 1 to either the Administrators group or the Power Users
	  group.
	
	3. Log on to the Exchange Server as the account noted in step 1. Add a printer
	  to the system and make it the default printer.
	
	4. Log on to a client computer as a user that has permissions to create an event
	  script and add the following code to a Microsoft Exchange 5.5 public folder:
	
	  <SCRIPT RunAt=Server Language=VBScript>
	
	  Option Explicit 
	
	  ' DESCRIPTION: This event is fired when a new message is added to the folder.
	  Public Sub Folder_OnMessageCreated
	
	     script.response = "Message Created -"
	     PrintScript
	     script.response = script.response & "- Finished"
	
	  End Sub
	
	  Sub PrintScript
	
	     Dim objprint
	
	     Set objprint = CreateObject("PrintMsgProj.PrintMsgCls")
	     objprint.PrintMsg
	
	  End Sub
	  </SCRIPT>
	
	5. Create an ActiveX DLL which uses the Print object to print a text string:
	
	  a. Start a new project in Microsoft Visual Basic and select ActiveX DLL.
	     Class1 is created by default; change the name to "PrintMsgCls".
	
	  b. From the Visual Basic Project menu, select Project1 Properties. Change the
	     Project name to "PrintMsgProj" and the Project Description to "Print EV
	     Script Test Object". Click OK to close the Project Properties dialog box.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q281630 HOWTO: Configure Visual Basic DLL Project Properties to Run in IIS,
	  MTS, or COM+
	
	6. Paste the following code into the General Declarations section of
	  PrintMsgCls:
	
	  Public Sub PrintMsg()
	
	  Printer.Print "The OnMessageCreated Event Has Fired!"
	  Printer.EndDoc
	
	  End Sub
	
	7. Save the project. From the File menu, click Make PrintMsgProj.dll. You are
	  now finished creating your ActiveX DLL project, but you still need to test
	  it.
	
	8. Create a Microsoft Transaction Server (MTS) package. For additional
	  information, see the following article in the Microsoft Knowledge Base:
	
	  Q223406 HOWTO: Create an Empty MTS Package to Add Components for ASP
	
	9. Test the script. If nothing prints, check the script log for error
	  information.
	
	REFERENCES
	==========
	
	  Q301237 HOWTO: Create a Visual Basic Project Template for Creating IIS
	  Components
	
	  Q180121 XCLN: Agents Tab Is Missing from Folder Properties
	
	  The "Microsoft Exchange Event Scripting Agent" topic in the Microsoft
	  Developer Network (MSDN).
	
	Additional query words: events
	
	======================================================================
	Keywords          : kbExchange550 kbMsg kbEvent 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
