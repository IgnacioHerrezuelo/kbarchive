---
layout: page
title: "Q192951: HOWTO: Install an ActiveX Control for Design-Time Use"
permalink: /kb/192/Q192951/
---

## Q192951: HOWTO: Install an ActiveX Control for Design-Time Use

{% raw %}

	Article: Q192951
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to use the Microsoft Visual Basic Application Setup
	Wizard to install the design-time license information for a custom ActiveX
	control developed in Visual Basic.
	
	MORE INFORMATION
	================
	
	In order for the Setup Wizard to install the license information a .VBL file
	must be created. This is accomplished by specifying that the control require
	license information. The following steps will demonstrate how to create a new
	control and require a license file for the control.
	
	Step-by-Step Example
	--------------------
	
	1. Start Microsoft Visual Basic and create a new ActiveX Control project.
	  UserControl1 is created by default.
	
	2. On the Project menu, click Project1 Properties, and then click the General
	  Tab.
	
	3. Select "Require License Key" and click Ok.
	
	  At this point, the custom ActiveX control will require a license to be used in
	  the design environment. When the control is compiled, a .VBL file will be
	  created that contains the necessary license information. If using the Setup
	  Wizard to generate an application distribution set, the Setup wizard will
	  include the license information in the [Licenses] section of the Setup.lst
	  file.
	
	Additional query words: kbVBp500 kbCtrl kbCtrlCreate kbWizard kbAppSetup kbdss kbDSupport kbVBp kbActiveX
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500
	Version           : WINDOWS:5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
