---
layout: page
title: "Q256117: ATLComp.exe: Add Many ATL Simple Objects from ATL Object Wizard"
permalink: /kb/256/Q256117/
---

## Q256117: ATLComp.exe: Add Many ATL Simple Objects from ATL Object Wizard

{% raw %}

	Article: Q256117
	Product(s): Microsoft C Compiler
	Version(s): 2.0,3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbSample kbATL kbide kbVC500 kbVC600 kbDevStudio kbDSupport kbGrpDSTools
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- The Microsoft Active Template Library (ATL), versions 2.0, 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The ATLComp.exe add-in sample enables you to insert many ATL-based COM classes
	from the ATL Object wizard. This sample in particular inserts the "Simple
	Object" from the ATL Object Wizard. Moreover, the ATLComp.exe add-in is based on
	the Developer Studio Object Model and Microsoft Foundation Classes (MFC). This
	sample is unsupported.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  ATLComp.exe
	  (http://download.microsoft.com/download/vc60ent/30/1.0/WIN98/EN-US/ATLComp.exe)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	The self extracting ATLComp.exe file contains the following files:
	
	+---------------------------------+
	| File name                | Size | 
	+---------------------------------+
	| Commands.cpp             | 2KB  | 
	+---------------------------------+
	| Commands.h               | 2KB  | 
	+---------------------------------+
	| DSAddIn.cpp              | 4KB  | 
	+---------------------------------+
	| DSAddIn.h                | 2KB  | 
	+---------------------------------+
	| InsertManyATLComp.cpp    | 5KB  | 
	+---------------------------------+
	| InsertManyATLComp.h      | 1KB  | 
	+---------------------------------+
	| InsertManyATLComp.dsw    | 1KB  | 
	+---------------------------------+
	| InsertManyATLComp.dsp    | 6KB  | 
	+---------------------------------+
	| InsertManyATLComp.def    | 1KB  | 
	+---------------------------------+
	| InsertManyATLComp.odl    | 2KB  | 
	+---------------------------------+
	| InsertManyATLComp.rc     | 7KB  | 
	+---------------------------------+
	| InsertManyATLComp.clw    | 2KB  | 
	+---------------------------------+
	| InsertManyATLComp.i_c    | 2KB  | 
	+---------------------------------+
	| InsertManyATLComp.rc2    | 1KB  | 
	+---------------------------------+
	| TBarLrge.bmp             | 2KB  | 
	+---------------------------------+
	| TBarMedm.bmp             | 1KB  | 
	+---------------------------------+
	| ATLObjWizDlg.cpp         | 2KB  | 
	+---------------------------------+
	| ATLObjWizDlg.h           | 2KB  | 
	+---------------------------------+
	| InsertManyATLCompTypes.h | 6KB  | 
	+---------------------------------+
	| Resource.h               | 2KB  | 
	+---------------------------------+
	| StdAfx.cpp               | 1KB  | 
	+---------------------------------+
	| StdAfx.h                 | 3KB  | 
	+---------------------------------+
	| InsertATLClass.cpp       | 5KB  | 
	+---------------------------------+
	| InsertATLClass.h         | 2KB  | 
	+---------------------------------+
	| ClassEditorDlg.cpp       | 2KB  | 
	+---------------------------------+
	| ClassEditorDlg.h         | 2KB  | 
	+---------------------------------+
	
	Steps to Install the Add-In
	---------------------------
	
	1. Run ATLComp.exe to extract the Visual C++ project.
	
	2. Build the project in Visual C++ in Release or Debug configuration.
	
	3. In Visual C++, click Customize from the Tools menu.
	
	4. In the Customize dialog box, click Add-Ins and Macro Files.
	
	5. Click Browse and locate the InsertManyATLComp.dll file that was built in step
	  2.
	
	6. Click OK to save the settings.
	
	A toolbar with the InsertManyATLComp command appears.
	
	Using the ATLComp.exe Add-In
	----------------------------
	
	Click InsertManyATLComp to launch the "Insert Many ATL Object Wizard Components"
	dialog. In this dialog you can either choose to create a series of ATL classes
	or specify a custom list of classes to create. You can select one of them by
	choosing the appropriate radio button.
	
	If you choose the first radio button then you should specify the short name for
	the "Simple Object", the start and end values. For example if you enter
	"MyObject" as the short name, 1 and 10 for the start and end values
	respectively, then clicking OK adds classes CMyObject1 through CMyObject10 to
	your project.
	
	When the add-in is performing the task of adding classes you should avoid using
	the keyboard and avoid switching to another program. Also, do not add duplicate
	ATL classes.
	
	If you find that the add-in fails to add a class or you get a build error then
	open the InsertATLClass.cpp file; go to line 173; change the delay amount passed
	to the Sleep function; rebuild the project and try adding the classes again.
	Sometimes problems arise due to synchronization. The default value passed to
	Sleep is 2000 milliseconds.
	
	REFERENCES
	==========
	
	See the following topics in the MSDN Library for Visual C++ 6.0 for
	documentation on Visual C++ Automation:
	
	MSDN Library; Visual Studio Documentation; Visual C++ Documentation; Using Visual
	C++; Visual C++ User's Guide; Automating Tasks in Visual C++
	
	Additional query words: ATLComp
	
	======================================================================
	Keywords          : kbfile kbSample kbATL kbide kbVC500 kbVC600 kbDevStudio kbDSupport kbGrpDSTools 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch kbATL200 kbATL300 kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : :2.0,3.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
