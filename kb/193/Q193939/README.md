---
layout: page
title: "Q193939: HOWTO: Use a Project and File Object's SCC PEMs"
permalink: /kb/193/Q193939/
---

## Q193939: HOWTO: Use a Project and File Object's SCC PEMs

{% raw %}

	Article: Q193939
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbSSafe600 kbvfp600
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, version 6.0 
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article illustrates how you can use the various source code control related
	properties and methods of the project and the file object.
	
	MORE INFORMATION
	================
	
	All of the source code control properties and methods are associated with the
	file object and only one property, read only, is associated with the project
	object. You can get access to all the source control functionality through the
	file object.
	
	Presently, using the current set of project object properties, events, and
	methods (PEM's), a project cannot be added to SCC programmatically. This
	operation has to be done visually using the "Add project to source control"
	option from the project menu.
	
	The source control property associated with the project object is SCCProvider,
	which contains an empty string if the project is not under source control.
	Otherwise, the source control property contains the name of the source control
	provider associated with the project. This property is read only at run and
	design time and is automatically updated by Visual FoxPro whenever a project is
	added to or removed from source control. The following is an example of using
	the SCCProvider property to find out whether or not a project is under source
	control:
	
	  curProj = _VFP.ActiveProject
	     IF EMPTY(curProj.SCCProvider)
	        MESSAGEBOX("Project is not under SourceCode Control"+;
	                 chr(13)+space(18)+"Unable to proceed")
	
	     ELSE
	        MESSAGEBOX("Project is under SourceCode Control")
	
	     ENDIF
	     RETURN
	
	Following are examples of how to use the file object SCC properties and methods.
	
	Properties
	----------
	
	SCCSTATUS:
	
	This property is read only at design and run time. It contains a numeric
	representation of the source control status of a file as follows:
	
	  No.   Source Control Status
	  --------------------------------------------------------------------
	
	  0     File is not Source Controlled (SCCFILE_NOTCONTROLLED)
	  1     File is Source Controlled and Checked In (SCCFILE_NOTCHECKEDOUT)
	  2     File Checked Out to Current User (SCCFILE_CHECKEDOUTCU)
	  3     File Checked Out to Other than Current User (SCCFILE_CHECKEDOUTOU)
	  4     File has Merge Conflict (SCCFILE_MERGECONFLICT)
	  5     File Merged without conflict (SCCFILE_MERGE)
	  6     File Checked Out to Multiple Users (SCCFILE_CHECKEDOUTMU)
	
	You can use the status property to make sure that a source control operation can
	or should be performed on a specific file. To check the contents of the property
	for a file, you can use the following sample code:
	
	     FUNCTION gSCCStat
	     PARAMETERS fName
	     CurProj = _VFP.ActiveProject
	     FOR i = 1 to CurProj.Files.Count
	        IF UPPER(fname) $ UPPER(CurProj.Files(i).Name)
	           IF CurProj.Files(i).SCCStatus = 0
	              MESSAGEBOX("File "+fname+" Is not Source Controlled")
	              fSCCStatus=0
	           ELSE
	              fSCCStatus = CurProj.Files(i).SCCStatus
	           ENDIF
	        ENDIF
	     ENDFOR
	     RETURN fSCCStatus
	
	Methods:
	
	When you invoke any of the following methods, the source control dialog box for
	the specific source control function comes up. The dialog box enables you to
	perform the function on a single or multiple files. The source control methods
	do not work if the project is not under source control.
	
	  Function: Description
	  ---------------------------------------------------------
	
	  AddToSCC: Adds file(s) to Source Control
	     Example: _VFP.ActiveProject.Files(1).AddToSCC
	
	  RemoveFromSCC: Removes file(s) from Source Control
	     Example: _VFP.ActiveProject.Files(1).RemoveFromSCC
	
	  CheckIn: Allows CheckIn of file(s)
	     Example: _VFP.ActiveProject.Files(1).CheckIn
	
	  CheckOut: Allows CheckOut of file(s)
	     Example: _VFP.ActiveProject.Files(1).CheckOut
	
	  UndoCheckOut: Allows Undo CheckOut for file(s)
	     Example: _VFP.ActiveProject.Files(1).UndoCheckOut
	
	  GetLatestVersion: Gets the Latest version of file(s)
	     Example: _VFP.ActiveProject.Files(1).GetLatestVersion
	
	In the examples above, the file represented by FILES(1) is selected in the source
	control dialog file list if the function can be performed on the file.
	Otherwise, the very first file in the list will be selected. In the dialog box,
	you can select to perform the function on one or multiple files.
	
	REFERENCES
	==========
	
	Visual FoxPro Help: Project Object/File Object
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe600 kbvfp600 
	Technology        : kbVFPsearch kbSSafeSearch kbAudDeveloper kbVFP600 kbSSafe600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
