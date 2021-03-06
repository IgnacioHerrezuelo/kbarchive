---
layout: page
title: "Q85431: MultFont.exe Modifies the Font Common Dialog Box"
permalink: /kb/085/Q85431/
---

## Q85431: MultFont.exe Modifies the Font Common Dialog Box

{% raw %}

	Article: Q85431
	Product(s): Microsoft Windows Software Development Kit
	Version(s): 3.1
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbCmnDlg kbCmnDlgFont kbGrpDSUser kbOSWin310 kbOSWin300
	Last Modified: 23-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MultFont.exe is a file in the Microsoft Download Center that demonstrates how an
	application can modify the ChooseFont() common dialog box to allow the user to
	select more than one font simultaneously. The standard Font dialog box only
	facilitates selecting one font; to choose more than one font, the user must
	interact with the dialog box multiple times.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  MultFont.exe
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	This article discusses techniques that are useful in applications that allow the
	user to specify different fonts for different areas of the application. MULTFONT
	displays information about an individual: name, occupation, and social security
	number. For each line of information, the user can use the Font dialog box to
	specify a different font for each line.
	
	MULTFONT uses a custom dialog box template and a hook function in conjunction
	with the Font dialog box. The template extends the Font dialog box with a list
	box. The entries in the list box list the name of each data element (name,
	occupation, and social security number). When the user selects a font and
	chooses the Apply button, MULTFONT stores the font face name, style, and point
	size in the list box. The text is stored outside the list box's visible area.
	
	For example, suppose the user selects the Name entry in the list box, selects the
	Arial font, Bold style, size 10 points, and then chooses the Apply button. The
	contents of the Name entry in the list box is updated as follows:
	
	      Select font for:
	    -------------------
	    |Name             | :Arial,Bold,10,
	    |Occupation       | :Script,Normal,12,
	    |SS_Number        | :Terminal,Normal,10,
	    |                 |
	    -------------------
	
	An advantage of storing this information in the list box is that the application
	can update the currently displayed font when the selection changes. In the
	example above, if the user selects Occupation, the fields of the Font dialog box
	should display the Script font. To obtain this behavior, MULTFONT installs a
	hook function to process the LBN_SELCHANGE message. When it receives an
	LBN_SELCHANGE message, MULTFONT performs the following processing:
	
	1. Parses the font information in the list box.
	
	2. Simulates the corresponding selections of the Font, Font Style, and Size.
	
	This processing updates the Font dialog box to display the font associated with
	the currently selected field. For more information, see the MAINWND.C file in
	the MULTFONT sample.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbCmnDlg kbCmnDlgFont kbGrpDSUser kbOSWin310 kbOSWin300 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : :3.1
	
	=============================================================================
	

{% endraw %}
