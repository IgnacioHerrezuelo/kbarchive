---
layout: page
title: "Q110772: PRB: Window Sizes in .EXE Change w/ MODIFY WINDOW SCREEN FONT"
permalink: /kb/110/Q110772/
---

## Q110772: PRB: Window Sizes in .EXE Change w/ MODIFY WINDOW SCREEN FONT

{% raw %}

	Article: Q110772
	Product(s): Microsoft FoxPro
	Version(s): 2.00 2.50 2.50a 2.50b 3.00
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are creating an executable file in FoxPro for Windows, you notice that
	the distributed application's appearance is quite different from what it was
	during development.
	
	CAUSE
	=====
	
	This difference occurs because the default font in the Windows environment is
	usually different than the font that FoxPro uses to dimension the main desktop.
	
	The default font you have specified in the Screen Layout dialog box in the Screen
	Builder must match your current screen font.
	
	RESOLUTION
	==========
	
	To avoid this problem during development, issue MODIFY WINDOW SCREEN FONT
	"foxfont" as the first line of executable code in the executable's main program.
	Although this is enough to correct the problem on the development machine, it
	still is not enough to solve the problem on the systems the executable will
	eventually be run on.
	
	To completely resolve this issue, do the following:
	
	1. Make MODIFY WINDOW SCREEN FONT <font name> the first line of executable
	  code in the main program of the application.
	
	  NOTE: <Font name> should be the name of the default font in FoxPro. To
	  determine the default font, hold down the SHIFT key and choose Screen Font
	  from the Text menu in FoxPro. By default, the font will be FoxFont, but this
	  setting can be changed by the user. Any font can be used as the default font,
	  but it is recommended that you use FoxFont because it can be distributed
	  freely, unlike other TrueType fonts. If you use another font, all machines
	  that run the application will have to have that font installed.
	
	2. Install FOXFONT.FON using the Fonts icon in the Windows Control Panel.
	
	  NOTE: This step must be performed on any machine that will run the executable
	  application.
	
	3. Include FOXFONT.FON in the set of files to be distributed with the executable
	  file.
	
	Additional query words: VFoxWin FoxWin 2.00 2.50 position off screen
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : 2.00 2.50 2.50a 2.50b 3.00
	
	=============================================================================
	

{% endraw %}
