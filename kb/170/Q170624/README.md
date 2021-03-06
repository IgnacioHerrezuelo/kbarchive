---
layout: page
title: "Q170624: FP97: Data Loss After Using &quot;View or Edit HTML&quot; Dialog Box"
permalink: /kb/170/Q170624/
---

## Q170624: FP97: Data Loss After Using &quot;View or Edit HTML&quot; Dialog Box

{% raw %}

	Article: Q170624
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbusage kbdta
	Last Modified: 26-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In FrontPage Editor, when you use the HTML command on the View menu to edit a
	very large file, you may experience any of the following symptoms:
	
	- The scroll bar does not function as expected in the Web browser.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q160616 FP: Unable to Use Scroll Bar/Page Displayed Incorrectly
	
	- You cannot enter new text in the "View or Edit HTML" dialog box.
	
	- When you click OK to close the "View or Edit HTML" dialog box, some of your
	  text is deleted.
	
	- The Show Color Coding check box in the "View or Edit HTML" dialog box is
	  selected, but some of the HTML markup is not color coded.
	
	CAUSE
	=====
	
	FrontPage 97 Editor does not have internal data structures large enough to
	accurately handle very large documents.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Microsoft FrontPage
	98 for Windows.
	
	MORE INFORMATION
	================
	
	As a general rule, if you cannot enter any additional text, without first
	deleting text in the "View or Edit HTML" dialog box, do not click OK or you will
	lose some of your text. If you experience any of the problems described in the
	"Symptoms" section, you should avoid using the HTML command on the View menu.
	
	
	WORKAROUND
	==========
	
	To work around this problem, break up the large document into smaller documents
	before you use the HTML command on the View menu.
	
	Additional query words: truncate denude pave trash
	
	======================================================================
	Keywords          : kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage97 kbZNotKeyword2 kbFrontPage97Search
	Version           : :
	Hardware          : x86
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
