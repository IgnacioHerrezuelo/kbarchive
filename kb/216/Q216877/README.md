---
layout: page
title: "Q216877: CFS: Cannot Hear Radio Communications When You Fly a Mission"
permalink: /kb/216/Q216877/
---

## Q216877: CFS: Cannot Hear Radio Communications When You Fly a Mission

{% raw %}

	Article: Q216877
	Product(s): Microsoft Home Games
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbenv kbsound fsim kbimu msgamekbfaq
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Combat Flight Simulator: WWII Europe Series, version 1.0 
	- Microsoft Combat Flight Simulator 2: WWII Pacific Theater, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you fly a mission in Combat Flight Simulator, you may not hear any radio
	communications.
	
	CAUSE
	=====
	
	This issue can occur if the Microsoft Adaptive Delta Pulse Code Modulation
	(ADPCM) audio codec is not properly installed on your computer.
	
	The radio communications files in Combat Flight Simulator are compressed using
	the ADPCM codec.
	
	RESOLUTION
	==========
	
	To resolve this issue, check the radio communication volume setting in the game.
	If the issue continues to occur, remove and reinstall the default audio codecs.
	To do this, follow these steps:
	
	NOTE: You need to have your Microsoft Windows 95/98 CD-ROM to reinstall the audio
	codecs.
	
	1. Check the radio communication volume setting in Combat Flight Simulator. To
	  do this, follow these steps:
	
	  a. Start Combat Flight Simulator.
	
	  b. On the Combat Flight Simulator startup screen, click Settings.
	
	  c. Under Sound Volume, drag the Communications slider bar to the right.
	
	  d. Click OK.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. Double-click Add/Remove Programs.
	
	4. Click the Windows Setup tab.
	
	5. In the Components box, click Multimedia, and then click Details.
	
	6. Click to clear the Audio Compression check box, click OK, and then click
	  Apply.
	
	7. In the Components box, click Multimedia, and then click Details.
	
	8. Click to select the Audio Compression check box, and then click OK.
	
	9. Click OK.
	
	If the issue continues to occur, follow these steps to remove and reinstall only
	the ADPCM audio codec:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click MultiMedia.
	
	3. Click the Devices or Advanced tab.
	
	4. Click the PLUS SIGN (+) next to Audio Compression Codecs to expand the
	  branch.
	
	5. Click Microsoft ADPCM CODEC, and then click Properties.
	
	6. Click Remove. When you are prompted to remove the codec, click Yes.
	
	7. Follow the instructions on the screen to remove the codec.
	
	8. Restart your computer.
	
	9. Click Start, point to Settings, and then click Control Panel.
	
	10. Double-click Add New Hardware.
	
	11. Click Next, and then click Next again.
	
	12. Click "No, the device is not on the list," and then click Next.
	
	13. Click "No, I want to select the hardware from a list," and then click Next.
	
	14. Click Sound, Video And Game Controllers, and then click Next.
	
	15. In the Manufacturers box, click Microsoft Audio Codecs.
	
	16. In the Models box, click ADPCM CODEC, and then click Next.
	
	17. Click Finish. When you are prompted to restart the computer, do so.
	
	Additional query words: 1.00 msgame voices instructions fltsim sound winme
	
	======================================================================
	Keywords          : kbenv kbsound fsim kbimu msgame kbfaq
	Technology        : _IKkbbogus kbGamesSearch kbCombatFlightSim2 kbCombatFlightSim kbCombatFlightSimSearch kbSimSearch
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
