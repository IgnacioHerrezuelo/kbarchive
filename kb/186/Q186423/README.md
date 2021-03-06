---
layout: page
title: "Q186423: HOWTO: Return and Assign Arrays with Visual Basic 6.0"
permalink: /kb/186/Q186423/
---

## Q186423: HOWTO: Return and Assign Arrays with Visual Basic 6.0

{% raw %}

	Article: Q186423
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	New to Visual Basic 6.0 is the ability to assign an array or return an array
	from a function. This article demonstrates these new features.
	
	MORE INFORMATION
	================
	
	One of the benefits of assigning arrays is that the compiler will type- check
	the assignments the same way it does for other variable assignments. Also you
	can trap for a Type Mismatch error if you are returning an array from a
	late-bound object.
	
	When making array assignments, the array on the left side of the argument must me
	a dynamic array. Otherwise, you will receive the following compiler error:
	
	  "Can't assign to array"
	
	This is the same compiler error you will get if you try to assign arrays of
	different types. For example, you will receive this error if you attempt to
	assign an Integer array to a String array:
	
	     StringArray = IntegerArray
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Standard EXE project. Form1 is created by default.
	
	2. Add a Class Module to the project.
	
	3. Place the following code in the Class Module:
	
	        Option Explicit
	
	        Public Function ArrayFromClass() As String()
	           Dim aStr(1 To 10) As String
	           Dim i As Integer
	           For i = 1 To 10
	              aStr(i) = "Class array element " & Str(i)
	           Next i
	           ArrayFromClass = aStr()
	        End Function
	
	4. Place three CommandButtons on form1.
	
	5. Add the following code to form1:
	
	        Option Explicit
	
	        Private aiLeftSide() As Integer
	        Private asLeftSide() As String
	        Private aiRightSide(1 To 10) As Integer
	        Private asRightSide(1 To 10) As String
	        Private obj As Object
	
	        Private Sub Command1_Click()
	           Dim i As Integer
	           aiLeftSide = aiRightSide
	           'try assigning arrays of different types by changing the next line
	           ' to aiLeftSide = asRightSide
	           asLeftSide = asRightSide
	           For i = 1 To UBound(aiLeftSide)
	              Debug.Print aiLeftSide(i)
	           Next i
	           For i = 1 To UBound(asLeftSide)
	              Debug.Print asLeftSide(i)
	           Next i
	        End Sub
	
	        Private Sub Command2_Click()
	           Dim i As Integer
	           Dim aInt() As Integer
	           Dim astr() As String
	           aInt = ReturnIntArray
	           'try assigning arrays of different types by changing the next line
	           ' to aInt = ReturnStringArray
	           astr = ReturnStringArray
	           For i = 1 To UBound(aInt)
	              Debug.Print aInt(i)
	           Next i
	           For i = 1 To UBound(astr)
	              Debug.Print astr(i)
	           Next i
	        End Sub
	
	        Private Sub Command3_Click()
	           'To see what kind of error you get when a late-bound object
	           'returns an array that is of a different type than the receiving
	           'array, change the next line of code to be Dim astr() as Integer
	           Dim astr() As String
	           Dim i As Integer
	           astr = obj.ArrayFromClass
	           For i = 1 To UBound(astr)
	              Debug.Print astr(i)
	           Next i
	        End Sub
	
	        Private Sub Form_Load()
	           Dim i As Integer
	           Command1.Caption = "Assign Array"
	           Command2.Caption = "Call Function that returns Array"
	           Command3.Caption = "Call Object method that returns Array"
	           For i = 1 To 10
	              aiRightSide(i) = i
	              asRightSide(i) = "This is element " & Str(i)
	           Next i
	           Set obj = New Class1
	        End Sub
	
	        Private Function ReturnStringArray() As String()
	           Dim aString(1 To 10) As String
	           Dim i As Integer
	           For i = 1 To UBound(aString)
	              aString(i) = "Element " & Str(i)
	           Next i
	           ReturnStringArray = aString()
	        End Sub
	
	        Private Function ReturnIntArray() As Integer()
	           Dim aInt(1 To 10) As Integer
	           Dim i As Integer
	           For i = 1 To 10 'UBound(aInt)
	              aInt(i) = i
	           Next i
	           ReturnIntArray = aInt()
	        End Sub
	
	6. Run the form and click on the different command buttons. You will see the
	  results in the Immediate Window.
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Brian
	Combs, Microsoft Corporation
	
	
	Additional query words: kbDSupport kbDSD kbVBA kbVB600 kbDSupport
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
