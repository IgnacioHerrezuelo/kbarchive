---
layout: page
title: "Q214617: Changing the Page Orientation to Landscape"
permalink: /kb/214/Q214617/
---

## Q214617: Changing the Page Orientation to Landscape

{% raw %}

	Article: Q214617
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbfile kbprint kbSample kbCmnDlgPrint kbMFC kbPrinting kbVC500 kbVC600 kbGrpDSMFCATL
	Last Modified: 14-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Default printing in MFC supports changing the page orientation (Portrait or
	Landscape) by interacting with the common Print dialog box. Sometimes, it may be
	necessary to change the page orientation at run time without interacting with
	the Print dialog box; for example, when changing the orientation to Landscape
	for printing a large report.
	
	Mfcdvmd.exe is a sample that shows how the page orientation can be changed
	without interacting with the common Print dialog box. This is a self extracting
	.exe file.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	Visual C++ 6.0:
	
	  Mfcdvmd.exe
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	Visual C++ .NET:
	
	  DownloadDownload Mfcdvmdvcnet.exe now
	  (http://download.microsoft.com/download/visualstudionet/other/1.33/win98mexp/en-us/Mfcdvmdvcnet.exe)
	
	Release Date: August 14, 2002
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	Sample Functionality
	--------------------
	
	First, the sample queries for the available printers, in the OnPrepareDC function
	of CMyPrintView. Then, the sample allocates memory using the queried
	PrinterInfo. This is done to query the name of the printer.
	
	A member function ChangeDevMode() is added to CMyPrintView. The ChangeDevMode()
	function follows these three steps for obtaining and changing the DEVMODE
	buffer. The function takes a named printer and configures a DEVMODE to print in
	Landscape if it supports these features. The resulting DEVMODE is returned to
	the caller, that is the OnPrepareDC function. When OnPrepareDC is done with the
	DEVMODE buffer, it is responsible for freeing the memory.
	
	The change in the page orientation can be verified either by printing on paper or
	by print-previewing. Even if the Print Setup dialog box is set to Portrait, the
	page will print with a Landscape orientation.
	
	NOTE: To use the Print APIs, Winspool.h needs to be included.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q132239 TITLE : SAMPLE: Calling ExtDeviceMode/DeviceCapabilities in Win32s
	  App
	
	  Q167345 HOWTO: Modify Printer Settings with DocumentProperties()
	
	Additional query words: DEVMODE OnPrepareDC PrinterInfo orientation
	
	======================================================================
	Keywords          : kbfile kbprint kbSample kbCmnDlgPrint kbMFC kbPrinting kbVC500 kbVC600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : :5.0,6.0
	
	=============================================================================
	

{% endraw %}
