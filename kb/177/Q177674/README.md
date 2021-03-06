---
layout: page
title: "Q177674: HOWTO: Toggle the NUM LOCK, CAPS LOCK, and SCROLL LOCK Keys"
permalink: /kb/177/Q177674/
---

## Q177674: HOWTO: Toggle the NUM LOCK, CAPS LOCK, and SCROLL LOCK Keys

{% raw %}

	Article: Q177674
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kb
	Last Modified: 27-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to toggle the NUM LOCK, CAPS LOCK, AND SCROLL LOCK
	keys under Windows 95, Windows 98, Windows Me, Windows NT, or Windows 2000.
	
	MORE INFORMATION
	================
	
	To toggle the NUM LOCK, CAPS LOCK, or SCROLL LOCK keys, you can use the
	following logic:
	
	- Use the GetKeyboardState function to determine the state of the key.
	
	- Determine which operating system is being used with the GetVersionEx API.
	  (Windows 95/98/Me and Windows NT/2000 require different methods for toggling
	  these keys.)
	
	- Under Windows 95, Windows 98, or Windows Me, use the SetKeyboardState API
	  function to set the state of the key. Under Windows NT or Windows 2000, use
	  the keybd_event function to simulate a key press.
	
	This example shows how to toggle these three keys to "on" if they are "off." This
	sample may be easily modified to toggle them off or just to check their state.
	
	Sample Project
	--------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a CommandButton to Form1.
	
	3. Add the following code to the General Declarations section of Form1:
	
	        ' Declare Type for API call:
	        Private Type OSVERSIONINFO
	          dwOSVersionInfoSize As Long
	          dwMajorVersion As Long
	          dwMinorVersion As Long
	          dwBuildNumber As Long
	          dwPlatformId As Long
	          szCSDVersion As String * 128   '  Maintenance string for PSS usage
	        End Type
	
	        ' API declarations:
	
	        Private Declare Function GetVersionEx Lib "kernel32" _
	           Alias "GetVersionExA" _
	           (lpVersionInformation As OSVERSIONINFO) As Long
	
	        Private Declare Sub keybd_event Lib "user32" _
	           (ByVal bVk As Byte, _
	            ByVal bScan As Byte, _
	            ByVal dwFlags As Long, ByVal dwExtraInfo As Long)
	
	        Private Declare Function GetKeyboardState Lib "user32" _
	           (pbKeyState As Byte) As Long
	
	        Private Declare Function SetKeyboardState Lib "user32" _
	           (lppbKeyState As Byte) As Long
	
	        ' Constant declarations:
	        Const VK_NUMLOCK = &H90
	        Const VK_SCROLL = &H91
	        Const VK_CAPITAL = &H14
	        Const KEYEVENTF_EXTENDEDKEY = &H1
	        Const KEYEVENTF_KEYUP = &H2
	        Const VER_PLATFORM_WIN32_NT = 2
	        Const VER_PLATFORM_WIN32_WINDOWS = 1
	
	4. Add the following code to the Click event of the CommandButton:
	
	      Private Sub Command1_Click()
	        Dim o As OSVERSIONINFO
	        Dim NumLockState As Boolean
	        Dim ScrollLockState As Boolean
	        Dim CapsLockState As Boolean
	
	        o.dwOSVersionInfoSize = Len(o)
	        GetVersionEx o
	        Dim keys(0 To 255) As Byte
	        GetKeyboardState keys(0)
	
	        ' NumLock handling:
	        NumLockState = keys(VK_NUMLOCK)
	        If NumLockState <> True Then    'Turn numlock on
	          If o.dwPlatformId = VER_PLATFORM_WIN32_WINDOWS Then  '=== Win95/98
	
	            keys(VK_NUMLOCK) = 1
	            SetKeyboardState keys(0)
	          ElseIf o.dwPlatformId = VER_PLATFORM_WIN32_NT Then   '=== WinNT
	          'Simulate Key Press
	            keybd_event VK_NUMLOCK, &H45, KEYEVENTF_EXTENDEDKEY Or 0, 0
	          'Simulate Key Release
	            keybd_event VK_NUMLOCK, &H45, KEYEVENTF_EXTENDEDKEY _
	               Or KEYEVENTF_KEYUP, 0
	          End If
	        End If
	
	        ' CapsLock handling:
	        CapsLockState = keys(VK_CAPITAL)
	        If CapsLockState <> True Then    'Turn capslock on
	          If o.dwPlatformId = VER_PLATFORM_WIN32_WINDOWS Then  '=== Win95/98
	            keys(VK_CAPITAL) = 1
	            SetKeyboardState keys(0)
	          ElseIf o.dwPlatformId = VER_PLATFORM_WIN32_NT Then   '=== WinNT
	          'Simulate Key Press
	            keybd_event VK_CAPITAL, &H45, KEYEVENTF_EXTENDEDKEY Or 0, 0
	          'Simulate Key Release
	            keybd_event VK_CAPITAL, &H45, KEYEVENTF_EXTENDEDKEY _
	               Or KEYEVENTF_KEYUP, 0
	          End If
	        End If
	
	        ' ScrollLock handling:
	        ScrollLockState = keys(VK_SCROLL)
	        If ScrollLockState <> True Then    'Turn Scroll lock on
	          If o.dwPlatformId = VER_PLATFORM_WIN32_WINDOWS Then  '=== Win95/98
	            keys(VK_SCROLL) = 1
	            SetKeyboardState keys(0)
	          ElseIf o.dwPlatformId = VER_PLATFORM_WIN32_NT Then   '=== WinNT
	          'Simulate Key Press
	            keybd_event VK_SCROLL, &H45, KEYEVENTF_EXTENDEDKEY Or 0, 0
	          'Simulate Key Release
	            keybd_event VK_SCROLL, &H45, KEYEVENTF_EXTENDEDKEY _
	              Or KEYEVENTF_KEYUP, 0
	          End If
	        End If
	      End Sub
	
	5. Press the F5 key to run the program. Click the CommandButton. The state of
	  the CAPS LOCK, the NUM LOCK, and the SCROLL LOCK keys should all be "on."
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q127190 : HOWTO: Toggle the NUM LOCK, CAPS LOCK, and SCROLL LOCK Keys
	
	
	Additional query words: numlock capslock scrolllock key state kbKeyboard
	
	======================================================================
	Keywords          : kbSDKWin32 kbVBp kbVBp400 kbVBp500 kbVBp600 kbOSWin95 kbOSWin98 kbGrpDSVB kbDSupport kbOSWinME 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
