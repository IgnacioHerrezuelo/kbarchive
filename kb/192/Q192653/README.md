---
layout: page
title: "Q192653: FIX: Eight or More ActiveX DLLs in Compiled Project Cause Error"
permalink: /kb/192/Q192653/
---

## Q192653: FIX: Eight or More ActiveX DLLs in Compiled Project Cause Error

{% raw %}

	Article: Q192653
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbservicepack kbActiveX kbDLL kbide kbVBp kbVBp600bug kbGrpDSVB kbVS600sp2 kbVS600sp2fi
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A Visual Basic project group contains at least eight ActiveX DLL projects and
	one standard EXE project. The Standard EXE project creates and releases the
	ActiveX DLL files. The project group is compiled into DLL and EXE files. The EXE
	file is run.
	
	The first time you create and release the ActiveX DLL files, the program runs
	successfully. However, the second time you create and release the ActiveX DLL
	files, an application error occurs and displays the following message:
	
	  The instruction at "0x6602c2c5 referenced memory at "0x010b008c". The Memory
	  could not be "written".
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3. For more information
	about Visual Studio service packs, please see the following articles in the
	Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	The bug occurs only when the compiled projects are run outside the Visual Basic
	IDE. The bug does not occur when you run the project through the Visual Basic
	IDE.
	
	This section shows you how to create a sample project that demonstrates the bug
	behavior. The section assumes you are familiar with creating ActiveX DLL
	projects, standard EXE projects, project groups, and compiling these files into
	a executable file.
	
	Steps to Reproduce Behavior
	---------------------------
	
	The sample project contains eight ActiveX DLL projects that will be used in a
	Standard EXE project. The Standard EXE project is then compiled into an
	executable file. The executable file is then run to demonstrate the bug
	behavior.
	
	To create the eight ActiveX DLL projects:
	
	1. Start a new ActiveX DLL project in Visual Basic. Class1 is created by
	  default.
	
	2. Copy the following code to the Code window of the Class1:
	
	  Option Explicit
	        Public Sub DoNothing()
	
	        End Sub
	
	3. Save this Class module as Class1.cls and this project as Project1.vbp.
	
	4. Add another ActiveX DLL project to the project group. Class1 is created by
	  default. Remove the Class1 class module from this project and add the Class1
	  class module you created for Project1.vbp to the new ActiveX DLL project.
	
	5. Save this project as Project2.vbp.
	
	6. Repeat steps 4 and 5 to add six other ActiveX DLL projects with the same
	  Class1 class module to the project group. Save these projects as Project3.vbp
	  through Project8.vbp.
	
	  You have just created a project group with eight ActiveX DLL projects saved as
	  Project1.vbp to Project8.vbp. Each ActiveX DLL project references the same
	  Class1 class module created in Project1.vbp.
	
	  The next step is to create a Standard EXE project that uses the eight ActiveX
	  DLL projects.
	
	To create the Standard EXE project:
	
	1. Add a new Standard EXE project to the same project group containing the eight
	  ActiveX DLL projects. Form1 is created by default.
	
	2. Add a CommandButton to Form1.
	
	3. Copy the following code to the Code window of the Form1 form:
	
	        Option Explicit
	
	        Private Sub Command1_Click()
	           Dim o(8) As Object
	           Dim i As Integer
	           Dim strProgID As String
	
	           For i = 1 To 8
	              strProgID = "Project" & i & ".Class1"
	              Set o(i) = CreateObject(strProgID)
	              o(i).donothing
	              Set o(i) = Nothing
	           Next
	           MsgBox "Done"
	        End Sub
	
	4. Save the project as Project9.vbp.
	
	5. Set Project9.vbp as the Start up project. In the Project Explorer,
	  right-click Project9.vbp and then click Set as Start Up. Project9.vbp appears
	  in bold in the Project Explorer.
	
	6. Press the F5 key to start to run the project in IDE. Click the Command1
	  button in Form1 several times and it note that it works correctly.
	
	7. Compile the Project Group.
	
	8. Run Project9.exe outside the IDE. The Form1 form appears. Click Command1. A
	  message box appears. Click OK to close the message box. Click Command1 again.
	  Note that an application error occurs and displays the following message box:
	
	  The instruction at "0x6602c2c5 referenced memory at "0x010b008c". The Memory
	  could not be "written".
	
	Additional query words: COM ActiveX InProc
	
	======================================================================
	Keywords          : kbservicepack kbActiveX kbDLL kbide kbVBp kbVBp600bug kbGrpDSVB kbVS600sp2 kbVS600sp2fix kbVS600SP1 kbVS600sp3fix kbVS600SP1fix 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
