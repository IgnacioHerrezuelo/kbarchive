---
layout: page
title: "Q318706: FIX: Cannot Implement Office Add-in IDTExtensibility2 Interface"
permalink: /kb/318/Q318706/
---

## Q318706: FIX: Cannot Implement Office Add-in IDTExtensibility2 Interface

{% raw %}

	Article: Q318706
	Product(s): Microsoft FoxPro
	Version(s): 7.0
	Operating System(s): 
	Keyword(s): kbCOMt kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix
	Last Modified: 03-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 7.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to create a single-threaded dynamic-link library (DLL) or
	multi-threaded DLL that implements the Office Add-in IDTExtensibility2
	Interface, the resulting .dll file or .exe file does not contain the
	IDTExtensibility2 interface.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Visual FoxPro for
	Windows 7.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q316964 How to Obtain the Latest Visual FoxPro for Windows 7.0 Service Pack
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Visual FoxPro for
	Windows 7.0.
	
	This problem was first corrected in Visual FoxPro for Windows 7.0 Service Pack 1.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	On a computer with Visual FoxPro 7.0 and Microsoft Office 2000 or later
	installed, follow these steps:
	
	1. On the Tools menu, click Object Browser.
	
	2. In the Object Browser, click Options, and then click to select all of the
	  options under Display Options.
	
	3. Close the Object Browser.
	
	4. Paste the following code in a program (.prg) file named Test, and then run
	  the program from the Command window:
	
	  NOTE: Change the path to include Msaddndr.dll file if necessary.
	
	  RELEASE ALL
	  CLEAR ALL
	  DELETE FILE testxx.*
	
	  CREATE PROJECT testxx NOWAIT
	  TEXT TO lcText NOSHOW
	  x = NEWOBJECT("myclass")
	
	  DEFINE CLASS myclass AS session OLEPUBLIC
	
	  	IMPLEMENTS IDTExtensibility2 IN "C:\program files\common files\designer\msaddndr.dll"
	
	  	PROCEDURE IDTExtensibility2_OnConnection(_Application AS VARIANT, ConnectMode AS VARIANT, AddInInst AS VARIANT, custom AS VARIANT) AS VOID
	  	* Add user code here.
	  	ENDPROC
	
	  	PROCEDURE IDTExtensibility2_OnDisconnection(RemoveMode AS VARIANT, custom AS VARIANT) AS VOID
	  	* Add user code here.
	  	ENDPROC
	
	  	PROCEDURE IDTExtensibility2_OnAddInsUpdate(custom AS VARIANT) AS VOID
	  	* Add user code here.
	  	ENDPROC
	
	  	PROCEDURE IDTExtensibility2_OnStartupComplete(custom AS VARIANT) AS VOID
	  	* Add user code here.
	  	ENDPROC
	
	  	PROCEDURE IDTExtensibility2_OnBeginShutdown(custom AS VARIANT) AS VOID
	  	* Add user code here.
	  	ENDPROC
	  ENDDEFINE
	  ENDTEXT
	
	  STRTOFILE(lcText,'testxx.prg',0)
	  _VFP.ACTIVEPROJECT.FILES.ADD('testxx.prg')
	  _VFP.ACTIVEPROJECT.BUILD('testxx.dll',4)
	  _VFP.ACTIVEPROJECT.CLOSE
	
	  DO (_OBJECTBROWSER)
	  _oobjectbrowser.loadtypelib(SET("Default")+CURDIR()+'testxx.dll')
	
	  RETURN 
	
	If you run the example code in Visual FoxPro 7.0, you receive the following error
	message:
	
	  An error occured loading the requested type library!
	  The selected file is either invalid or not a type library.
	
	If you try to manually build the project by using the Project Manager or by using
	the BUILD command, you receive the following error message:
	
	  Unknown error <error number>
	
	If you run the code in Visual FoxPro 7.0 Service Pack 1, no error occurs.
	
	To view the IDTExtensibility2 interface in Visual FoxPro 7.0 Service Pack 1,
	follow these steps:
	
	1. Expand the Classes node in the left pane of the Object Browser.
	
	2. Select myclass, and observe that the IDTExtensibility2 interface appears in
	  the right pane under Interfaces.
	
	To clean up the registry entries for the .dll that is created in this
	reproduction, follow these steps:
	
	1. From Visual FoxPro, use the change directory (CD) command to change to the
	  directory that contains Testxx.dll.
	
	2. Paste the following code in a .prg file, and then run the program from the
	  Command window:
	
	  DECLARE INTEGER DllUnregisterServer IN TESTXX.DLL
	  ? DLLUnregisterServer()
	  CLEAR DLLS
	
	A 0 appears, indicating that the registry entries for the DLL have been removed.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCOMt kbGrpDSFox kbDSupport kbCodeSnippet kbvfp700 _IK283 kbVFP700sp1fix 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP700
	Version           : :7.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
