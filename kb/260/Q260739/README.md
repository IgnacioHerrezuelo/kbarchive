---
layout: page
title: "Q260739: SerialKeys Advanced Usage and Troubleshooting"
permalink: /kb/260/Q260739/
---

## Q260739: SerialKeys Advanced Usage and Troubleshooting

{% raw %}

	Article: Q260739
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 2000,4.0,95
	Operating System(s): 
	Keyword(s): kbenable kbEnableMove
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 98 
	- Microsoft Windows 98 Second Edition 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows 2000 Professional 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes common troubleshooting tips for SerialKeys and how to use
	more sophisticated methods of access. SerialKeys enables you to control the
	computer by using an alternate input devices.
	
	For additional information about setting up SerialKeys or programming an
	assistive aid, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q260517 How to Set Up and Use SerialKeys in Windows
	
	MORE INFORMATION
	================
	
	SerialKeys is usually used by accessibility aids to provide input in place of
	that provided by the computer's keyboard or mouse. The Microsoft implementation
	of SerialKeys follows the connection and communication protocol outlined in the
	General Input Device Emulating Interface (GIDEI) protocol defined by the Trace
	Research and Development Center at the University of Wisconsin. Details of the
	GIDEI protocol are available from Trace at the following Trace Research and
	Development Center Web site:
	
	  http://trace.wisc.edu/docs/gidei/gidei.htm
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	Troubleshooting SerialKeys
	--------------------------
	
	If you are using SerialKeys and the aid stops sending keys successfully, try the
	following items:
	
	- Check to make sure you included any necessary periods in your key names.
	
	- Send three null characters. (The null character is different from a zero;
	  usually you can generate it on the aid by pressing CTRL+@.
	
	- Reset both the aid and SerialKeys to 300 baud. (If there is a communication
	  difficulty, SerialKeys may automatically reset itself to 300 baud, making it
	  unable to communicate with the aid if the aid is sending at a different
	  rate.)
	
	Note the following items:
	
	- SerialKeys uses hardware handshaking (DTR/RTS) and software (XON/OFF)
	  handshaking to control the flow of characters from the aid. Characters may be
	  lost if the aid ignores these handshaking signals.
	
	- Microsoft Windows NT 4.0 manages the COM ports, including the hardware
	  interrupt lines. Windows NT does not allow another device to use or share the
	  interrupt line that SerialKeys is using. This means that if, for example, you
	  have SerialKeys turned on using COM port 1, you cannot use the Windows
	  Terminal program on COM port 1. Also, if you have SerialKeys on COM 1, and
	  another program is experiencing problems while using COM 3, you must move the
	  program or SerialKeys to COM 2 or COM 4. See your computer documentation for
	  details on how COM 1 and 3 and COM 2 and 4 should be set, and whether the
	  computer supports COM ports 3 and 4.
	
	Microsoft recommends programming the aid to use the IBM Enhanced Keyboard (101
	keys). Even if the computer does not have this keyboard, SerialKeys functions as
	the 101-key keyboard. This can be to your advantage, because some programs
	recognize the additional keys, enabling you to use additional features. If you
	choose to program the 83-key or 84-key keyboard, there are a few exceptions you
	should be aware of:
	
	- To use the Break function, you would ordinarily press and hold down the CTRL
	  key and press the SCROLL key. For SerialKeys, press and hold down the CTRL
	  key and press the PAUSE key.
	
	- To use the Pause function, you would ordinarily press and hold down the CTRL
	  key and press the NUM LOCK key. For SerialKeys, just press the PAUSE key.
	
	Advanced Mouse Movements
	------------------------
	
	It is a good idea to program at least a square or selection on the aid to move
	the mouse in the four directions by 1, 10, and 100 units. This lets you make
	small, fine movements and large, fast movements. For example:
	
	  [esc],move,+1,0.         Moves mouse pointer 1 unit right
	  [esc],move,-1,0.         Moves mouse pointer 1 unit left
	  [esc],move,0,+1.         Moves mouse pointer 1 unit down
	  [esc],move,0,-1.         Moves mouse pointer 1 unit up
	  [esc],move,+10,0.        Moves mouse pointer 10 units right
	  [esc],move,-10,0.        Moves mouse pointer 10 units left
	  [esc],move,0,+10.        Moves mouse pointer 10 units down
	  [esc],move,0,-10.        Moves mouse pointer 10 units up
	  [esc],move,+100,0.       Moves mouse pointer 100 units right
	  [esc],move,-100,0.       Moves mouse pointer 100 units left
	  [esc],move,0,+100.       Moves mouse pointer 100 units down
	  [esc],move,0,-100.       Moves mouse pointer 100 units up
	
	Resetting SerialKeys
	--------------------
	
	If you are using SerialKeys in a multiple-user environment, the first command you
	send to SerialKeys should be the reset command. This ensures that SerialKeys
	operates at 300 baud and is ready to accept your keyboard and mouse actions. The
	reset command consists of sending three null (ASCII 0) characters with the aid
	configured to 300 baud. You can usually generate a null character on the aid by
	pressing CTRL+@.
	
	Using Lock and Release
	----------------------
	
	You can use this command to hold a key down and lift it back up again as separate
	actions. Its primary use is in using SerialKeys in combination with MouseKeys.
	
	1. Turn on MouseKeys by pressing left ALT+left SHIFT+NUM LOCK.
	
	2. Decide which direction you want to move the mouse. Find out which numeric
	  keypad key moves the mouse in that direction in MouseKeys.
	
	3. Send a lock command with that key name. For example, to move the mouse
	  pointer to the right:
	
	  [esc],lock,kpright.
	
	4. When the mouse pointer has moved as far as you want in that direction, send
	  the release command:
	
	  [esc],rel.
	
	You can program the lock part and the release part of this sequence under a
	different selection on the aid so that you do not have to type them each time
	you use them. Make sure to include the commas and periods.
	
	NOTE: MouseKeys also enables you to hold down and release a mouse button or click
	a mouse button.
	
	Using the Keyboard Combine Command 
	----------------------------------
	
	If you want to program a modifier key and another key under a single selection on
	the aid, use the combine command to place several keystrokes under one selection
	on the aid. This can be useful for common multiple-key command combinations that
	are required by software. There must be commas between the keys and a period at
	the end. No more than five keys can be combined. For example:
	
	  [esc],combine,shift,ctrl,enter.
	
	Using the Mouse Goto Command
	----------------------------
	
	This moves the mouse to a specified location. You should send the moureset
	command first. Both the horizontal and vertical direction numbers require only a
	plus (+) sign. (See the example for moving the mouse earlier in the "Advanced
	Mouse Movements" section.) For example:
	
	  [esc],goto,+20,+25.
	
	Using the Mouse Anchor Command
	------------------------------
	
	You can use this command to anchor the mouse pointer to a position within a
	Windows-based program. If you change the active window between setting the mouse
	anchor and returning to that anchor, the mouse anchor command does not work. The
	following example shows how to use the mouanchor (mouse anchor) command to mark
	a current window position, go to a new location and click the mouse to select a
	new tool, go to another new location and click the mouse to select another
	color, and then return to the location you left to use that tool:
	
	  [esc],mouanchor.    Sets the position or anchors the pointer
	  [esc],goto,+10,+10. Goes to a new location
	  [esc],click.        Click selects a new tool in this
	                      program at location 10,10
	  [esc],goto,+50,+10. Goes to a new location
	  [esc],click.        Click selects a new color in this
	                      program at location 50,10
	  [esc],mouanchor.    Returns to where you left from,
	                      anchor released
	
	Using the Baudrate Command
	--------------------------
	
	This command enables you to change the SerialKeys baud rate from the aid. The
	possible baud rates are 300; 600; 1,200; 2,400; 4,800; and 9,600. This command
	is never absolutely necessary because you can also set the baud rate in
	SerialKeys. For example:
	
	  [esc],baudrate,300.
	
	If you decide to run SerialKeys at a baud rate faster than 300, be aware of the
	special automatic reset feature in SerialKeys. When SerialKeys receives three
	consecutive characters with a transmission error, it automatically resets to 300
	baud. This enables people in a multiple-user environment to place SerialKeys in
	a known state (300 baud). SerialKeys signals any transmission problem with a
	short beep. If SerialKeys resets to 300 baud, it generates a long beep.
	SerialKeys also signals a baud rate change with a long beep.
	
	The information in this article is excerpted from the Customizing Windows for
	Individuals with Disabilities series of documents. For additional information
	about customizing different versions of Windows for people with disabilities,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q165486 Customizing Windows for Individuals with Disabilities
	
	Additional query words: serialkey
	
	======================================================================
	Keywords          : kbenable kbEnableMove 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbWin95search kbWin98search kbWin98SEsearch kbZNotKeyword3 kbWin98 kbWin98SE
	Version           : :2000,4.0,95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
