---
layout: page
title: "Q141349: Error Message: MMSYSTEM281 This File Could Not Be Played"
permalink: /kb/141/Q141349/
---

## Q141349: Error Message: MMSYSTEM281 This File Could Not Be Played

{% raw %}

	Article: Q141349
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to play a MIDI (.mid) file, .avi file, or .wav file, you may
	receive the following error message:
	
	  MMSYSTEM281 This file could not be played. Check the filename or install a
	  driver that supports this type of file.
	
	CAUSE
	=====
	
	This behavior can occur for either of the following reasons:
	
	- The proper entry is not present in the [mci extensions] section of the
	  Win.ini file for the type of file you are trying to play.
	
	- There is an incorrect Media Control Device association for the file type you
	  are trying to play.
	
	RESOLUTION
	==========
	
	Proper Entry Not Present in the Win.ini File
	--------------------------------------------
	
	Make sure that the [mci extensions] section exists in the Win.ini file, and that
	the proper entries are present. For example, .avi files are played using the
	AVIVideo MCI device.
	
	The following is a sample [mci extensions] section:
	
	  [mci extensions]
	  mid=Sequencer
	  rmi=Sequencer
	  wav=waveaudio
	  avi=AVIVideo
	
	
	Incorrect Media Control Device Association
	------------------------------------------
	
	To correct this error, remove and then reinstall any devices that are not working
	correctly. To do so, follow these steps:
	
	1. In Control Panel, double-click Multimedia.
	
	2. On the Advanced tab, double-click the Media Control Devices branch to expand
	  it.
	
	3. Click the device that is not working properly, click Properties, and then
	  click Remove.
	
	4. When you are prompted to verify that you want to remove the device, click
	  Yes. Click OK when you are notified that the device has been removed and when
	  you are notified that the changes will take effect when you restart Windows
	  95.
	
	5. Repeat steps 3-4 to remove any other devices that are not working correctly.
	  When you are done removing devices, click OK to close the Multimedia
	  Properties dialog box.
	
	6. In Control Panel, double-click Add New Hardware.
	
	7. Click Next, click No, and then click Next.
	
	8. In the Hardware Types box, click Sound, Video, And Game Controllers, and then
	  click Next.
	
	9. In the Manufacturers box, click Microsoft MCI.
	
	10. In the Models box, click one of the drivers you removed in step 3, and then
	  click Next.
	
	11. Click Finish.
	
	12. If you need to install another device, click No when you are prompted to
	  restart your computer, and then repeat steps 6-11.
	
	13. When you are done installing devices, click Yes when you are prompted to
	  restart your computer.
	
	MORE INFORMATION
	================
	
	This behavior usually occurs with files associated with Media Player. Because
	several file types are associated with Media Player, the [mci extensions]
	section of the Win.ini file is used to determine which MCI device Media Player
	should be used.
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
