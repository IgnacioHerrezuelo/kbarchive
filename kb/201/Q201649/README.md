---
layout: page
title: "Q201649: FAQ: Visual SourceSafe Integration with Visual Basic 6.0"
permalink: /kb/201/Q201649/
---

## Q201649: FAQ: Visual SourceSafe Integration with Visual Basic 6.0

{% raw %}

	Article: Q201649
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:4.0a,5.0,6.0
	Operating System(s): 
	Keyword(s): kbinterop kbSSafe400 kbSSafe500 kbSSafe600 kbVBp600kbfaq
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 4.0a, 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article covers some of the most frequently asked questions (FAQ) about
	Visual Basic and Visual SourceSafe integration.
	
	MORE INFORMATION
	================
	
	1. Q. Where is the main copy of the Visual Basic project stored?
	
	  A. The main copy of the project is located in the Visual SourceSafe database.
	  After modifying their local copies, all users should check the files into
	  Visual SourceSafe. This will cause the latest version of the user's work to
	  be stored in Visual SourceSafe. Every time you open the Visual Basic project,
	  Visual Basic will use the information in the local Mssccprj.scc file to
	  retrieve the latest version of the files from Visual SourceSafe and replace
	  the local copies of the user's Visual Basic files.
	
	2. Q. If the Allow Multiple Checkouts option is enabled, what type of files can
	  I allow multiple users to check out simultaneously?
	
	  A. Binary files cannot be checked out by multiple users simultaneously. Forms,
	  User Controls, and Property pages are added to Visual SourceSafe as binary
	  files. However, Project files, Modules, Class Modules, and User Connections
	  can be checked out by multiple users at the same time.
	
	3. Q. How do I know that a file has been Checked Out by some other user?
	
	  A. From Visual Basic, select the file in the project window for which you want
	  to know the status, then click on Tools->SourceSafe->SourceSafe
	  Properties->Check Out Status tab. You will get the following information:
	  Which users have the file checked out, Check Out Date and time, Computer name
	  that the file was Checked Out to and the Visual SourceSafe project that
	  contains this file.
	
	4. Q. If two users check out a project file, how does Visual SourceSafe avoid
	  overwriting changes made by one user when the other user checks in their copy
	  of the file?
	
	  A. Let us assume that UserA and UserB checked out the same project file,
	  Proj1.vbp. UserA changes the file and checks it in. This will update the file
	  stored in the Visual SourceSafe database. UserB changes their local copy of
	  the file and checks it in. Before updating the server copy, Visual SourceSafe
	  will compare the files in UserB's working folder and the file stored in the
	  Visual SourceSafe database. If UserA and UserB have made different changes to
	  the same parts of the vbp file, Visual SourceSafe will display the Visual
	  Merge window and give UserB the opportunity to specify which changes he or
	  she wants to keep.
	
	5. Q. If new users want to modify the project, what are the steps they need to
	  follow?
	
	  A. Follow the steps given in the "Creating local copy of the Project from
	  SourceSafe" section. This will create a local copy of the project from Visual
	  SourceSafe database.
	
	6. Q. While trying to modify a user control after doing a checkout, it gives an
	  error "Can't edit module." How can I fix this error?
	
	  A. You will get this error if do not have the form that contains the user
	  control checked out. You can avoid this error by checking out the form prior
	  to editing the user control.
	
	7. Q. Is it necessary to check out the project file when I only want to edit one
	  of the forms contained in the project file?
	  A. If you have a ActiveX control embedded in your form, you have to check out
	  the project file also.
	
	8. Q. I've checked out and modified my files. At what point do the copies stored
	  in the Visual SourceSafe database get updated?
	
	  A. The copies of the files stored in the Visual SourceSafe database only get
	  updated when you check your files back in. This causes the changes you've
	  made to your local copy of the file transferred to the file stored in Visual
	  SourceSafe.
	
	9. Q. When I open a project in Visual Basic that is under Source Code control,
	  does Visual SourceSafe get the latest version of the project?
	
	  A. In order to get the latest version of your project from Visual SourceSafe,
	  you need to set the Tools->SourceSafe->Options->'Get the latest
	  checked-in version while opening the Visual Basic project' option to Yes.
	
	REFERENCES
	==========
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q135995 FAQ: Visual SourceSafe Integration with Visual Basic 4.0 and 5.0
	
	Additional query words:
	
	======================================================================
	Keywords          : kbinterop kbSSafe400 kbSSafe500 kbSSafe600 kbVBp600 kbfaq
	Technology        : kbVBSearch kbSSafeSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbSSafe600 kbSSafe400a kbSSafe500
	Version           : WINDOWS:4.0a,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
