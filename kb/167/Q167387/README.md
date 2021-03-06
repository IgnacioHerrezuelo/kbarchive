---
layout: page
title: "Q167387: WD97: WordBasic.Files&#36;() Command Adds Quotation Marks to Result"
permalink: /kb/167/Q167387/
---

## Q167387: WD97: WordBasic.Files&#36;() Command Adds Quotation Marks to Result

{% raw %}

	Article: Q167387
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbmacro kbProgramming kbdta kbdtacode word8 kbwordvba word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Visual Basic for Applications WordBasic object in combination
	with the WordBasic Files$() command and a path that includes spaces, the return
	value will contain quotation marks. If you attempt to use this return value with
	another command, you will receive the following error message:
	
	  Run-time error '76': "Path not found."
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Use one of the following methods to work around this problem:
	
	Method 1: Remove the extra quotation marks
	------------------------------------------
	
	The following Visual Basic for Applications subroutine, "GetWordBasicPath,"
	retrieves the current path using the WordBasic File$() command. It then calls
	the function, "RemoveQuotes," that checks to see if the path begins with a
	quotation mark. If it does, the function strips the beginning and ending
	quotation marks from the path and returns the value to the calling subroutine.
	If the path does not contain quotation marks, the original value is returned.
	
	     Sub GetWordBasicPath()
	        Dim sPath As String
	        sPath = RemoveQuotes(WordBasic.Files$("."))
	        MsgBox sPath
	     End Sub
	
	     Function RemoveQuotes(sPath As String)
	     ' ***********************************************
	     ' This function strips extra quotation marks from
	     ' the return value when using the WordBasic
	     ' Files$() command.
	     ' ***********************************************
	        ' If the value starts with a quotation mark...
	        If Left$(sPath, Length:=1) = Chr$(34) Then
	           ' ...remove opening and closing quotation marks.
	           RemoveQuotes = Mid$(sPath, Start:=2, Length:=Len(sPath) - 2)
	        Else
	           ' ...otherwise, return the value as is.
	           RemoveQuotes = sPath
	        End If
	     End Function
	
	Method 2. Use Visual Basic for Applications equivalent commands
	---------------------------------------------------------------
	
	In Visual Basic for Applications, use the CurDir and/or the Dir functions instead
	of the WordBasic object. When you use either of these functions, the value
	returned does not contain quotation marks. The following example code does not
	enclose the current path in quotation marks when it stores it in the variable,
	MyPath:
	
	     Dim MyPath As String
	     MyPath = CurDir
	
	For more information about the Dir Function, from the Visual Basic Editor, click
	the Office Assistant, type "Dir Function" (without the quotation marks), click
	Search, and then click to view "Dir Function."
	
	For more information about the CurDir Function, from the Visual Basic Editor,
	click the Office Assistant, type "CurDir Function" (without the quotation
	marks), click Search, and then click to view "CurDir Function."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If the Assistant is not able to answer your query, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q176476 OFF: Office Assistant Not Answering Visual Basic Questions
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kbmacro kbProgramming kbdta kbdtacode word8 kbwordvba word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Hardware          : x86
	
	=============================================================================
	

{% endraw %}
