---
layout: page
title: "Q141677: FIX: Insufficient Memory Errors Using OLE Controls"
permalink: /kb/141/Q141677/
---

## Q141677: FIX: Insufficient Memory Errors Using OLE Controls

{% raw %}

	Article: Q141677
	Product(s): Microsoft FoxPro
	Version(s): 3.00
	Operating System(s): 
	Keyword(s): kbbuglist kbfixlist
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Under some circumstances, using OLE controls and then repeatedly running the
	form that contains the OLE controls may result in a loss of system resources.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in FoxPro 3.0b for
	Windows.
	
	MORE INFORMATION
	================
	
	The following steps will replicate the resource leak in Windows 3.1 or in
	Windows NT. Before trying this example, you should save any information you have
	open in Visual FoxPro.
	
	Steps to Reproduce Problem
	--------------------------
	
	The following steps require that two conditions be satisfied:
	
	- Microsoft Word 6.0 or later must be installed.
	
	- On the Tools under the Controls option, you have both the Outline and
	  Microsoft Word Document controls installed.
	
	1. Create a new program file that holds the following code:
	
	     FOR i = 1 TO 50000
	       Formstr = "TESTFRM"
	       Loopstr = "#" + STR(i,3) + ":  "
	
	       WAIT loopstr + "Modifying form" WINDOW NOWAIT
	       MODIFY FORM (formstr) NOWAIT
	       WAIT loopstr + "Modifying form" WINDOW TIMEOUT 2
	       RELEASE (formstr)
	       CLEAR WINDOW
	       CLOSE ALL
	       *
	       WAIT loopstr + "Running form" WINDOW NOWAIT
	       DO FORM (formstr)
	       WAIT loopstr + "Running form" WINDOW TIMEOUT 2
	       RELEASE (formstr)
	       CLEAR WINDOW
	       CLOSE ALL
	       *
	       WAIT loopstr + "Delaying 2 seconds..." WINDOW TIMEOUT 2
	       WAIT loopstr + ;
	          "Memory handles in use = " + STR(VAL(SYS(1011)),4) WINDOW
	
	       TIMEOUT 2
	     ENDFOR
	
	2. In the Command window, type:
	
	     CREATE FORM TESTFRM
	
	3. In the Init event of the form, place the following code:
	
	     Public rval
	
	     rval=getobject("","word.basic")
	     Thisform.olecontrol2.doverb(0)
	     rval.insert("Hello")
	     rval.insert("Hello1")
	     rval.insert("Hello2")
	     rval.insert("Hello3")
	     rval.insert("Hello4")
	
	     Thisform.olecontrol1.additem("Line1")
	     Thisform.olecontrol1.additem("Line2")
	     Thisform.olecontrol1.additem("Line3")
	     Thisform.olecontrol1.additem("Line4")
	     Thisform.olecontrol1.additem("Line5")
	
	4. Place an Outline control on the form. Do not change any default settings.
	
	5. Place a Word Document control on the form, and type some text in it.
	
	6. Run the code. On some versions of Win32s (Prior to version 1.25) Visual
	  FoxPro will quit at around 870 iterations; on Windows NT it will quit at
	  around 2,700 iterations.
	
	Additional query words: VFoxWin buglist3.00 fixlist3.00b crash OLE control OLECONTROL
	
	======================================================================
	Keywords          :  kbbuglist kbfixlist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : 3.00
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
