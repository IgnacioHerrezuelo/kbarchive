---
layout: page
title: "Q139542: Infrared Data Association Relnotes.doc File (Part 1 of 2)"
permalink: /kb/139/Q139542/
---

## Q139542: Infrared Data Association Relnotes.doc File (Part 1 of 2)

{% raw %}

	Article: Q139542
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): Win2000:95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This information is a copy of the information in the Relnotes.doc file included
	with the Microsoft Windows 95 Infrared Communications Driver version 1.0.
	
	MORE INFORMATION
	================
	
	         ---------------------------------------------------
	         Microsoft Windows 95 Infrared Communications Driver
	                                                 Version 1.0
	                                               Release Notes
	         ---------------------------------------------------
	
	TABLE OF CONTENTS
	=================
	
	Quick Start
	Installing the IR Communications Driver
	Using the IR Communications Driver
	Troubleshooting
	Product Support
	
	QUICK START
	===========
	
	Congratulations! You are the proud owner of the Microsoft(r)
	Windows(r) 95 Infrared (IR) communications driver. After you install
	the IR communications driver you can start replacing your serial and
	parallel cable connections with wireless IR links.
	
	Wireless communications between computers is a new thing. And you're
	part of it! Have fun experimenting with wireless IR links between
	your computers and printers.
	
	The Version 1.0 IR communications driver is a set of software
	components that you can add to a Windows 95 computer to enable that
	computer to send and receive data over IR communications links.
	Installing the IR communications driver is as simple as running the
	Setup program that is one of the driver components.
	
	The IR communications driver supports IR communications links running
	up to 115.2 kilobytes per second (Kbps). The infrared hardware can be
	built into your Windows 95 computer or added by attaching an infrared
	adapter to a serial or parallel port. A future release of the IR
	communications driver will add support for high-speed IR devices
	which run at 1.152 and 4.0 megabytes per second (Mbps).
	
	Installing the IR Communications Driver
	---------------------------------------
	
	NOTE: You must always remove any previously installed version of the IR
	     communications driver every time you install the driver. For
	     example, if you have an earlier (Beta) version of the IR
	     communications driver already installed you must remove it before
	     you install Version 1.0. You may also need to remove an installation
	     of the Version 1.0 driver. For example, if you change the IR adapter
	     model that is connected to your computer, you must remove the
	     installed IR communications driver and reinstall it, specifying the
	     new IR adapter type. Instructions for removing the IR communications
	     driver are in "An Optional Step: Removing the IR Communications
	     Driver."
	
	A Quick Start overview of the IR Communications driver installation
	procedure is:
	
	- If you are using an IR adapter (rather than a built-in IR device), make
	  sure the adapter is physically attached to a COM port and note which
	  COM port it is (COM1, COM2, and so on). If you are using a computer
	  with a built-in IR device, note which COM port that device is assigned
	  to.
	
	- Start the setup program SETUP.EXE, which is one of the IR
	  communications components, to invoke the Windows 95 Add Infrared Device
	  Wizard. Respond to the wizard's prompts for physical COM port
	  information, IR device manufacturer and model information, and so on.
	
	- If the wizard announces New Hardware Found events for the IR serial and
	  parallel ports, you can enable the IR device immediately after the
	  wizard is finished. Enable the IR device by double-clicking on the
	  Infrared device icon in the Control Panel. If the wizard does not
	  announce New Hardware Found events before it is finished, you must
	  restart the computer before you use the Control Panel icon to activate
	  the IR device.
	
	For a detailed description of each of these steps, see "Roadmap for
	Installing and Using the IR Communications Driver" later in this
	document.
	
	Using the IR Communications Driver
	----------------------------------
	
	End-users can install the IR communications device driver on their
	Windows 95 computer and run applications using wireless infrared
	communications instead of serial or parallel cables. The driver has
	been successfully tested on the following Windows 95 notebook
	computers, which have built-in IR ports:
	
	  Digital(r) HiNote Ultra CT475
	  Gateway(r) 2000 Liberty
	  Gateway Solo
	  HP(r) Omnibook(tm) 600CT
	  HP Omnibook 4000C
	  IBM(r) ThinkPad(r) 701C (Butterfly)
	  IBM ThinkPad 755 (most configurations)
	  Midwest Micro Elite
	  Midwest Micro Elite p90
	  Sharp(r) PC 3050
	  TI(r) TravelMate(tm) 5000
	  Toshiba(r) Satellite Pro 400 CDT
	
	In addition, the driver has been successfully tested on Windows 95
	platforms with the following IR adapters connected to serial ports:
	
	  ACTiSYS ACT-200L Infrared Wireless Interface
	  ACTiSYS ACT-220L Infrared Wireless Interface
	  Adaptec(tm) AIRport APA-9320 External Infrared Adapter (this adapter is
	     also called the Adaptec AIRport 2000)
	  Adaptec AIRport 1000
	  AMP PhasIR Serial Adapter
	  Extended Systems JetEye PC Infrared PC Interface (ESI-9680)
	  Parallax IR Adapter LiteLink PRA9500A
	
	To obtain any of the IR adapters listed above, contact the adapter
	manufacturer. The addresses of  these manufacturers are listed in "IR
	Adapter Manufacturer Names and Addresses" at the end of this
	document.
	
	The following applications have been run successfully over an IR
	communications link, using the IR communications driver and the
	hardware listed above:
	
	  Windows 95 Direct Cable Connection (DCC)
	  Various Windows communications applications, including HyperTerminal,
	     DynaComm, and Carbon Copy.
	
	Because the IR link is simulating a serial communications link, some
	communications applications may not perform as expected after they
	connect over the IR link. See the "Troubleshooting" topic for more
	information.
	
	For instructions on running DCC over an IR link, see "Notes on
	Running the Direct Cable Connection Application Over an IR Link"
	later in this document.
	
	Numerous Windows 95 applications have successfully printed over an IR
	link to an HP(r) LaserJet(r) 5P or 5MP printer, which have built-in
	IR ports.
	
	Troubleshooting
	---------------
	
	Some general troubleshooting tips are:
	
	- To get two IR devices to discover each other, you may have to realign
	  the IR devices so they point right at each other, move them closer
	  together, and/or change the batteries in an IR adapter or plug the AC
	  power into an IR adapter. The devices must be three feet apart, or
	  less, and the angle of the cone of IR transmission is 30 degrees. Some
	  devices work best if kept at least six inches apart.
	
	- You must always remove any previously installed version of the IR
	  communications driver every time you install the driver. For example,
	  if you have an earlier (Beta) version of the IR communications driver
	  already installed you must remove it before you install Version 1.0.
	  You may also need to remove an installation of the Version 1.0 driver.
	  For example, if you change the IR adapter model that is connected to
	  your computer, you must remove the installed IR communications driver
	  and reinstall it, specifying the new IR adapter type. Instructions for
	  removing the IR communications driver are in "An Optional Step:
	  Removing the IR Communications Driver."
	
	Some troubleshooting tips related to using particular applications
	over IR links are:
	
	- If you use the Windows 95 application HyperTerminal to transfer files,
	  you will not be able to transfer files successfully over an IR link
	  using the Zmodem protocol as it is implemented by HyperTerminal.
	
	- When you run the Windows 95 application Direct Cable Connection (DCC)
	  and establish the connection between the host and guest computers, the
	  guest computer may display the message "Direct Cable Connection was
	  unable to display shared folders of the host computer" and prompt you
	  to enter the computer name of the host computer. A convenient way to
	  find the computer name of the host computer is on the Status tab of the
	  Infrared Monitor interface screen.
	
	Troubleshooting tips related to specific infrared hardware are:
	
	- The Adaptec AIRport 2000 infrared adapter can be powered by either the
	  serial port, installed AA batteries, or an external power supply. In
	  some cases, the serial port may not provide sufficient power for the
	  operation of the adapter. This can cause reduced operating range and/or
	  a failure to find another IR device which is nearby and aligned
	  correctly. If you suspect such a problem, connect an AC adapter or add
	  four AA batteries to the battery compartment in the infrared adapter.
	  This will assure sufficient power. In some instances, you may need to
	  separate the adapter by at least six inches the other IR device.
	
	- If you have an ACTiSYS 220L IR adapter attached to your computer and
	  print to a printer that is using an Extended Systems ESI-9580 printer
	  IR adapter, or you are printing to the HP DeskJet 340, you must use the
	  Options tab in the Infrared Monitor to limit the connection speed to
	  19.2 Kbps to print successfully. If you allow the IR devices to
	  automatically negotiate the connection speed without setting this
	  limit, they will negotiate a higher connection speed and your
	  application will not be able to print.
	
	- The TI TravelMate 5000 may communicate over an IR link only at very low
	  speeds (9600 baud).
	
	- The Sharp PC 3050 may communicate over an IR link only at speeds
	  between 9600 baud and 19.2 Kbps.
	
	- If you have an HP Omnibook 4000C or an HP Omnibook 600CT, you must
	  install a special echo-canceling serial driver in addition to the
	  components that make up the IR communications driver. The echo-
	  canceling driver, along with instructions on how to install it, are
	  available from Hewlett-Packard.
	
	Product Support
	---------------
	
	For a complete list of Microsoft Product Support Services phone numbers and
	information on support costs, please go to the following address on the World
	Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	Be prepared to give the following information:
	
	- The version number of the Microsoft product that you are using.
	
	- The type of hardware that you are using.
	
	- The exact wording of any messages that appeared on your screen.
	
	- A description of what happened and what you were doing when the problem
	  occurred.
	
	- A description of how you tried to solve the problem.
	
	Additional query words: irda
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : Win2000:95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
