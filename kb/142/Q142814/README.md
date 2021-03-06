---
layout: page
title: "Q142814: INFO: Diagnosing &quot;Error in loading DLL&quot; with LoadLibrary"
permalink: /kb/142/Q142814/
---

## Q142814: INFO: Diagnosing &quot;Error in loading DLL&quot; with LoadLibrary

{% raw %}

	Article: Q142814
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0
	Operating System(s): 
	Keyword(s): kb16bitonly kbVBp400
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The error "Error in loading DLL" (code 48) occurs when you call a dynamic-link
	library (DLL) procedure and the file specified in the procedure's Declare
	statement cannot be loaded. You can use the Microsoft Windows API function
	LoadLibrary to find out more specific information about why a DLL fails to load.
	
	MORE INFORMATION
	================
	
	The API function LoadLibrary loads a DLL and returns either a handle or an error
	code. If the return value is less than 32, it indicates one of the errors listed
	below. A return value greater than or equal to 32 indicates success and you
	should call the FreeLibrary function to unload the library.
	
	LoadLibrary Error Codes
	-----------------------
	
	0  System was out of memory, executable file was corrupt, or
	   relocations were invalid.
	
	2  File was not found.
	
	3  Path was not found.
	
	5  Attempt was made to dynamically link to a task, or there was a
	   sharing or network-protection error.
	
	6  Library required separate data segments for each task.
	
	8  There was insufficient memory to start the application.
	
	10 Windows version was incorrect.
	
	11 Executable file was invalid. Either it was not a Windows
	   application or there was an error in the .EXE image.
	
	12 Application was designed for a different operating system.
	
	13 Application was designed for MS-DOS 4.0.
	
	14 Type of executable file was unknown.
	
	15 Attempt was made to load a real-mode application (developed for
	   an earlier version of Windows).
	
	16 Attempt was made to load a second instance of an executable file
	   containing multiple data segments that were not marked read-only.
	
	19 Attempt was made to load a compressed executable file. The file
	   must be decompressed before it can be loaded.
	
	20 Dynamic-link library (DLL) file was invalid. One of the DLLs
	   required to run this application was corrupt.
	
	21 Application requires Microsoft Windows 32-bit extensions.
	
	Steps to Create Example Program
	-------------------------------
	
	The following program demonstrates how to call LoadLibrary to load a library and
	display a resulting error code.
	
	1. Create a new Standard EXE Project in Visual Basic, Form1 is created by
	  default.
	
	2. Enter the following code into the general declarations section of Form1:
	
	     #If Win32 Then
	        Private Declare Function LoadLibraryEx Lib "Kernel32" Alias "LoadLibraryExA" _
	           (ByVal lpLibFileName As String, _
	           ByVal hFile As Long, _
	           ByVal dwFlags As Long) As Integer
	        Private Declare Sub FreeLibrary Lib "Kernel32" (ByVal hLibModule As Integer)
	     #Else
	        Private Declare Function LoadLibrary Lib "kernel" (ByVal f$) As Integer
	        Private Declare Sub FreeLibrary Lib "Kernel" (ByVal h As Integer)
	     #End If
	
	3. Enter the following code into the Form Click event handler:
	
	        Private Sub Form_Click ()
	           Dim hInst As Integer
	           ' Enter the name of your DLL file inside the quotes below.
	           ' The file WIN.COM is not a valid DLL and demonstrates an error.
	           #If Win32 Then
	              hInst = LoadLibraryEx("win.com", 0, 2)
	              If hInst > 32 Then
	                 MsgBox "LoadLibrary success"
	                 FreeLibrary (hInst)
	              Else
	                 MsgBox "LoadLibrary error " + Format$(hInst)
	              End If
	           #Else
	              hInst = LoadLibrary("win.com")
	              If hInst > 32 Then
	                 MsgBox "LoadLibrary success"
	                 FreeLibrary (hInst)
	              Else
	                 MsgBox "LoadLibrary error " + Format$(hInst)
	              End If
	           #End If
	        End Sub
	
	4. Press the F5 key to run the program. Then click Form1. The program displays
	  the error code returned from LoadLibrary. Look up this error code in the list
	  of errors above to find an explanation.
	
	Additional query words:
	
	======================================================================
	Keywords          : kb16bitonly kbVBp400 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500 kbVB500 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
