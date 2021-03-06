---
layout: page
title: "Q154664: PRB: Dispatch Interface for Automation Object Must Be Registered"
permalink: /kb/154/Q154664/
---

## Q154664: PRB: Dispatch Interface for Automation Object Must Be Registered

{% raw %}

	Article: Q154664
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbole kbActiveX kbAutomation kbCOMt kbCtrlCreate kbMFC kbGrpDSMFCATL
	Last Modified: 09-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 4.0, 4.1 
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 4.2 
	- Microsoft Visual C++, 32-bit Professional Edition, version 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Visual Basic 4.0 can do typesafe binding to automation objects. In this
	scenario, the Visual Basic program will QueryInterface the automation object for
	its dispatch interface. If the interface is not registered on the machine, the
	Visual Basic program will fail to create the object. In this case, Visual Basic
	will report the following error:
	
	  Error 430: Class Does not Support OLE Automation.
	
	MORE INFORMATION
	================
	
	Visual Basic does typesafe binding to an automation object when a variable is
	dimensioned as a specific type. For instance:
	
	  Dim x As New TestVB.Document
	
	When developing this code, establish a reference to the TestVB module (in the
	Visual Basic development environment, select Tools, References, and Browse for
	the TestVB type library). Select the type library to register the type library
	and the dispatch interface for the Document object.
	
	The problem occurs when the Visual Basic program and the automation server are
	loaded on a machine other than the development machine. Even if the automation
	server is initially run to perform self-registration, the dispatch interface for
	the automation object will not be registered and the "New" syntax will fail to
	create the automation object.
	
	To eliminate this problem, it is necessary to register the dispatch interface for
	the automation object on the non-development machine. This can be done
	programmatically or with a .reg file during setup.
	
	In the case of the TestVB module, the Document object's dispatch interface is the
	ITestVB interface, which is defined as follows in the .cpp file for the Document
	object:
	
	     // Note: We add support for IID_ITestVB to support typesafe binding
	     // from VBA. This IID must match the GUID that is attached to the
	     // dispinterface in the .ODL file.
	
	     // {1249A4D2-D469-11CF-A68F-00AA00A70FC2}
	     static const IID IID_ITestVB =
	     { 0x1249a4d2, 0xd469, 0x11cf,
	             { 0xa6, 0x8f, 0x0, 0xaa, 0x0, 0xa7, 0xf, 0xc2 } };
	
	     BEGIN_INTERFACE_MAP(CTestVBDoc, CDocument)
	         INTERFACE_PART(CTestVBDoc, IID_ITestVB, Dispatch)
	     END_INTERFACE_MAP()
	
	The following .reg file will register the ITestVB interface and enable marshaling
	of the interface via the standard IDispatch proxy and stub.
	
	     REGEDIT
	     
	     HKEY_CLASSES_ROOT\Interface\{1249A4D2-D469-11CF-A68F-00AA00A70FC2}
	             = ITestVB
	     HKEY_CLASSES_ROOT\Interface\{1249A4D2-D469-11CF-A68F-00AA00A70FC2}
	             ProxyStubClsid = {00020420-0000-0000-C000-000000000046}
	     HKEY_CLASSES_ROOT\Interface\{1249A4D2-D469-11CF-A68F-00AA00A70FC2}
	             ProxyStubClsid32 = {00020420-0000-0000-C000-000000000046}
	
	To programmatically register the interface, #include <winreg.h>, and insert
	the following code (with the proper dispatch ID) in the InitInstance of the
	automation server:
	
	     HKEY key;
	
	     // Open HKEY_CLASSES_ROOT
	     RegOpenKey(HKEY_CLASSES_ROOT, _T("Interface"), &key);
	
	     // Set up the key
	     RegSetValue( key,
	         _T("{1249A4D2-D469-11CF-A68F-00AA00A70FC2}"), REG_SZ,
	         _T("ITestVB"), 0);
	     RegSetValue( key,
	         _T("{1249A4D2-D469-11CF-A68F-00AA00A70FC2}\\ProxyStubClsid"),
	         REG_SZ, _T("{00020420-0000-0000-C000-000000000046}"), 0);
	     RegSetValue( key,
	         _T("{1249A4D2-D469-11CF-A68F-00AA00A70FC2}\\ProxyStubClsid32"),
	         REG_SZ, _T("{00020420-0000-0000-C000-000000000046}"), 0);
	
	     RegCloseKey(key);
	
	
	Additional query words: Automation 430
	
	======================================================================
	Keywords          : kbole kbActiveX kbAutomation kbCOMt kbCtrlCreate kbMFC kbGrpDSMFCATL 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbVC410 kbVC420 kbVC32bitSearch
	Version           : winnt:4.0,4.1,4.2
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
