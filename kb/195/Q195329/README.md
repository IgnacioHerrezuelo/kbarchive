---
layout: page
title: "Q195329: WD97: Text Converted to One-Row Table (Paragraph Marks Ignored)"
permalink: /kb/195/Q195329/
---

## Q195329: WD97: Text Converted to One-Row Table (Paragraph Marks Ignored)

{% raw %}

	Article: Q195329
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): winword word97 kbtable kbdta
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you try to convert text to a table, Microsoft Word puts all the text in a
	single row. In the Convert Table To Text dialog box, Word shows only one row
	even though there should be multiple rows.
	
	This behavior occurs even when each line of text is separated by a paragraph
	mark.
	
	CAUSE
	=====
	
	This problem occurs if the paragraph marks have been inserted using the ASCII
	equivalent number 13 (denoted as ^13) rather than (^p). The Convert Text To
	Table feature does not recognize ^13 as a valid paragraph mark.
	
	RESOLUTION
	==========
	
	Before you convert the text to a table, replace the ASCII 13 characters (^13)
	with the appropriate paragraph marks (^p). To do this, follow these steps:
	
	1. Select all the text that you want to convert to a table.
	
	2. On the Edit menu, click Replace.
	
	3. In the Find What box, type "^13" (without the quotation marks).
	
	4. In the Replace With box, type "^p" (without the quotation marks).
	
	5. In the Search box, click to select Down, and then click Replace All.
	
	6. When Word asks if you want to continue to search the rest of the document,
	  click No.
	
	7. Click Close.
	
	8. With the lines of text still selected, click Convert Text To Table on the
	  Table menu. The correct options should appear. Click OK.
	
	Additional query words: linefeed line feed carriage return 8.0 8.00
	
	======================================================================
	Keywords          : winword word97 kbtable kbdta 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
