---
layout: page
title: "Q205053: PRB: &quot;Overflow&quot; with Integer Division and MOD Operator"
permalink: /kb/205/Q205053/
---

## Q205053: PRB: &quot;Overflow&quot; with Integer Division and MOD Operator

{% raw %}

	Article: Q205053
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kberrmsg kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using a number larger than 2,147,483,647 (or smaller than -2,147,483,648)
	with the Mod operator or the integer division operator (\), you receive the
	following error message:
	
	  Run Time Error '6':
	  Overflow
	
	CAUSE
	=====
	
	The Visual Basic Help topic for the Mod operator and the integer division
	operator (\) explains that if floating point numbers are used in the expression,
	they are converted to Longs first. Thus, if the floating point number is greater
	than the maximum value of a Long (2,147,483,647), or less than the minimum value
	for a long (-2,147,483,648), an overflow error will occur.
	
	RESOLUTION
	==========
	
	The following code demonstrates how to perform integer division and modulo
	arithmetic when the size of an operand is sufficiently large to cause overflow:
	
	  Dim dblX as Double
	  Dim dblY as Double
	  dblX = 2147483648                ' numerator
	  dblY = 123                       ' denominator
	
	  ' round off the numerator and denominator (ensure number is .0)
	  dblX = INT(dblX + .5)         
	  dblY = INT(dblY + .5)      
	
	  ' Emulate integer division
	  MsgBox FIX(dblX / dblY)             
	  ' Emulate modulo arithmetic
	  MsgBox dblX - ( dblY * FIX(dblX / dblY) )
	
	STATUS
	======
	
	This behavior is by design.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
