---
layout: page
title: "Q253588: PRB: OLE Error with Empty or NULL ControlSource with DT Picker"
permalink: /kb/253/Q253588/
---

## Q253588: PRB: OLE Error with Empty or NULL ControlSource with DT Picker

{% raw %}

	Article: Q253588
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbContainer kbCtrl kbvfp600 kbGrpDSFox kbDSupport
	Last Modified: 22-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Date and Time Picker ActiveX control is added to a form, its
	ControlSource set to a date field, and the record pointer moved to a record that
	contains a blank value in the date field, the following error message appears:
	
	  OLE IDispatch exception code 0 from DTPicker: A date was specified that does
	  not fall within the MinDate and MaxDate Properties...
	
	When the record pointer is moved to a record that contains a NULL value in the
	date field, the following error message appears:
	
	  OLE IDispatch exception code 0 from DTPicker: Invalid Property Value.
	
	CAUSE
	=====
	
	The DateTimePicker control's Calendar interface handles adjusting the Day,
	Month, and Year properties to create a valid date. If a value is assigned that
	creates an invalid date, one of the error messages above appears. This behavior
	occurs because the DateTimePicker control does not recognize {" / / "} as a
	valid date. Likewise, the DateTimePicker control does not recognize a NULL as a
	valid date.
	
	RESOLUTION
	==========
	
	Use the EMPTY() or ISNULL() functions to determine whether the date field that
	is the ControlSource for the DateTimePicker control is blank or NULL. If the
	field contains a blank or NULL value, set the ControlSource property of the
	DateTimePicker control to a NULL string. If the field is not blank, set the
	ControlSource of the DateTimePicker control to the datefield.
	
	  IF !EMPTY(TESTDTP.DTP_DATEA)
	      THISFORM.DTPicker1.CONTROLSOURCE="TESTDTP.DTP_Datea"
	   ELSE
	       THISFORM.DTPicker1.CONTROLSOURCE=""
	   ENDIF
	   IF !ISNULL(TESTDTP.DTP_DATEB)
	      THISFORM.DTPicker2.CONTROLSOURCE="TESTDTP.DTP_Dateb"
	   ELSE
	      THISFORM.DTPicker2.CONTROLSOURCE=""
	  ENDIF
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a program file named "DTP_DEMO" (without the quotation marks) using
	  the following code:
	
	  PUBLIC OX
	  OX=CREATEOBJECT('MYFORM')
	  OX.SHOW
	  READ EVENTS
	
	  DEFINE CLASS myform AS FORM
	     CAPTION = "DateTimePicker Form"
	     HEIGHT = 125
	     LEFT = 0
	     TOP = 0
	     WIDTH = 230
	     NAME = "myform"
	
	     ADD OBJECT DTPicker1 AS OLECONTROL WITH ;
	        OLECLASS="MSComCtl2.DTPicker.2",;
	        TOP = 5, ;
	        LEFT = 5, ;
	        HEIGHT = 25, ;
	        WIDTH = 100, ;
	        NAME = "DTPicker1"
	
	     ADD OBJECT DTPicker2 AS OLECONTROL WITH ;
	        OLECLASS="MSComCtl2.DTPicker.2",;
	        TOP = 35, ;
	        LEFT = 5, ;
	        HEIGHT = 25, ;
	        WIDTH = 100, ;
	        NAME = "DTPicker2"
	
	     ADD OBJECT commandbutton1 AS COMMANDBUTTON WITH ;
	        TOP=75, ;
	        LEFT=125, ;
	        HEIGHT=25, ;
	        CAPTION="\<Close"
	     NAME="commandbutton1"
	
	     PROCEDURE INIT
	  *!*      IF !EMPTY(TESTDTP.DTP_DATEA)
	           THISFORM.DTPicker1.CONTROLSOURCE="TESTDTP.DTP_Datea"
	  *!*      ELSE
	  *!*         THISFORM.DTPicker1.CONTROLSOURCE=""
	  *!*      ENDIF
	  *!*      IF !ISNULL(TESTDTP.DTP_DATEB)
	           THISFORM.DTPicker2.CONTROLSOURCE="TESTDTP.DTP_Dateb"
	  *!*      ELSE
	  *!*         THISFORM.DTPicker2.CONTROLSOURCE=""
	  *!*      ENDIF
	           
	     ENDPROC
	
	     PROCEDURE commandbutton1.CLICK
	        RELEASE THISFORM
	     ENDPROC
	
	     PROCEDURE LOAD
	        IF !FILE('TESTDTP.DBF')
	           CREATE TABLE TESTDTP (DTP_DATEA D, DTP_DATEB D NULL)
	           INSERT INTO TESTDTP VALUES (CTOD('  /  /  '),(.NULL.))
	        ENDIF
	        IF !USED("TESTDTP")
	           USE TESTDTP IN 0
	        ENDIF
	        SELECT TESTDTP
	     ENDPROC
	
	     PROCEDURE UNLOAD
	        USE IN TESTDTP
	        ERASE TESTDTP.DBF
	        CLEAR EVENTS
	     ENDPROC
	
	  ENDDEFINE
	
	2. Save and run DTP_DEMO. Note the error message that appears when the
	  DTPicker.ControlSource is set to a date field that contains an empty value.
	
	3. Note the error message that appears when the DTPicker.ControlSource is set to
	  a date field that contains a NULL value.
	
	4. Uncomment the commented lines of code in the Init method.
	
	  NOTE: This example uses the Init method. If you populate the ControlSource by
	  moving through the records of a table, you need to check for empty and NULL
	  fields in another event.
	
	5. Save and run DTP_DEMO. Note that the error message does not appear.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by John Desch,
	Microsoft Corporation.
	
	
	REFERENCES
	==========
	
	For additional information DTPicker ActiveX Control, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q189991 PRB: Error Setting DateTimePicker's Month Programmatically
	
	Additional query words:
	
	======================================================================
	Keywords          : kbActiveX kbContainer kbCtrl kbvfp600 kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP600
	Version           : WINDOWS:6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
