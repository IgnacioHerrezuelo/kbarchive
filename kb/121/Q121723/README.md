---
layout: page
title: "Q121723: How to Display Any Column of an Array in a List or Popup"
permalink: /kb/121/Q121723/
---

## Q121723: How to Display Any Column of an Array in a List or Popup

{% raw %}

	Article: Q121723
	Product(s): Microsoft FoxPro
	Version(s): 2.5x 2.6x 3.00 | 2.00 2.5x 2.6x
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6x 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5x, 2.6x 
	- Microsoft FoxPro for Macintosh, versions 2.5x, 2.6 
	- Microsoft FoxPro for UNIX, version 2.6 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, a list or popup shows the information from the first column of a
	multiple-column array. The methods below describe how to display information
	from any of the columns.
	
	MORE INFORMATION
	================
	
	Visual FoxPro
	-------------
	
	1. Create a form with a ListBox in it.
	
	2. Add the following code to the Init event of the ListBox:
	
	        PUBLIC ARRAY test(1,2)
	        * Define the two column array
	        SELECT cust_id, company FROM customer INTO ARRAY test
	        THIS.RowSource='test' && Ties the ListBox to the array
	        THIS.RowSourceType=5 && Tells the ListBox what type of data its using
	        THIS.ColumnCount=2   && In order to get other columns to show, you
	                             &&  must have a column count greater than 1
	        THIS.BoundColumn=2
	        THIS.ColumnWidths= '0,' +STR(THIS.Width) && Setting the ColumnWidth
	                           && property to 0, <some value> is the key to
	                           && displaying the second column.
	
	FoxPro 2.x
	----------
	
	NOTE: This example assumes that the CUSTOMER.DBF table has been installed in
	FoxPro's TUTORIAL subdirectory.
	
	To display any column of an array in a list or popup, use the Screen Builder to
	perform the following:
	
	1. In the Setup Code snippet of a test screen, type the following:
	
	       SET DEFAULT to <FoxPro_directory>\tutorial
	       SELECT company, city, state FROM customer INTO ARRAY a3colmns
	
	2. Create a list or popup object. For a list, select the From Array radio
	  button. For a popup, select the Array Popup radio option button.
	
	3. Type A3COLMNS in the Array Popup text box.
	
	4. In the Variable text box, type "M.COL" (without the quotation marks).
	
	5. Choose 1st Element.
	
	6. Verify that the Expression radio button is selected. Then type the number 1,
	  2, or 3 in the text editing region. The number you type designates which of
	  the three array columns will be displayed.
	
	7. Generate and run the screen.
	
	NOTE: The first column of the array contains COMPANY field data, the second
	contains CITY field data, and the third contains STATE field data from the
	CUSTOMER.DBF table.
	
	Additional query words: FoxUnix FoxMac FoxDos FoxWin VFoxWin 2.50 2.50a 2.50b 2.50c 2.60a different other many specific only multicolumn multi-column multi-dimension multiple-dimension dimension genscrn.prg power tool
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro260UNIX kbVFP300
	Version           : 2.5x 2.6x 3.00 | 2.00 2.5x 2.6x
	
	=============================================================================
	

{% endraw %}
