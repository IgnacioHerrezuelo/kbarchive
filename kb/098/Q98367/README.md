---
layout: page
title: "Q98367: How to Update Scrollable Lists in FoxBASE+/Mac"
permalink: /kb/098/Q98367/
---

## Q98367: How to Update Scrollable Lists in FoxBASE+/Mac

{% raw %}

	Article: Q98367
	Product(s): Microsoft Fox Miscellaneous Products
	Version(s): MACINTOSH:2.01
	Operating System(s): 
	Keyword(s): 
	Last Modified: 23-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxBASE+ for Macintosh, version 2.01 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The code example below shows one method of updating a scrollable list after an
	array element has been modified.
	
	MORE INFORMATION
	================
	
	WARNING: ANY USE BY YOU OF THE CODE PROVIDED IN THIS ARTICLE IS AT YOUR OWN
	RISK. Microsoft provides this code "as is" without warranty of any kind, either
	expressed or implied, including but not limited to the implied warranties of
	merchantability and/or fitness for a particular purpose.
	
	This code example uses the following procedures to update the scrollable list:
	
	  GETIT       "Grabs" the element out of the array.
	  SHOWIT      Shows the element on the screen for editing.
	  PUTITBACK   Puts the modified element in the scrollable list.
	  UPDATESCRN  Updates the screen.
	
	NOTE: Because FoxBASE+/Mac does not allow for nested READs, the READ must be
	terminated before the DO SHOWIT and DO UPDATESCRN commands can be issued.
	
	     *Start with a clean environment.
	     CLEAR
	     CLEAR ALL
	     SET TALK OFF
	     SET BELL OFF
	     *The name of this file is FARM.PRG.
	     SET PROCEDURE TO farm
	
	     *Set up memory variables for the GETs.
	     DIMENSION farm_var(4)
	     STORE "cow" TO farm_var(1)
	     STORE "pig" TO farm_var(2)
	     STORE "chicken" TO farm_var(3)
	     STORE "horse" TO farm_var(4)
	     STORE 0 to whichanimal,complete
	     STORE space(15) TO editanimal,mvar
	     STORE .F. TO done,flag1,flag2
	
	     ON KEY=13 DO dostopit
	     DO WHILE ! done
	     SCREEN 1 TOP
	     @ PIXELS 80,80 GET whichanimal FROM farm_var SIZE 80,80;
	       VALID getit(whichanimal)
	     @ PIXELS 160,200 GET mvar
	     @ PIXELS 200,140 GET complete PICTURE "@*H Done";
	       VALID stopit(complete)
	     READ
	     IF flag1           && When flag1 is true,
	        DO showit       && do procedure(s) to show and edit choice.
	     ENDIF
	     IF flag2           && When flag2 is true,
	        DO updatescrn   && do procedure to update the screen.
	     ENDIF
	     ENDDO
	
	     *Procedure to grab the element out of the array
	     PROCEDURE getit
	     PARAMETER theanimal
	     STORE farm_var(theanimal) TO editanimal
	     STORE .T. TO flag1  && Set flag1 to true to do showit.
	     KEYBOARD CHR(23)    && Terminate the READ.
	     RETURN .T.
	
	     *Procedure to show the element on the screen for editing
	     PROCEDURE showit
	     @ PIXELS 200,140 CLEAR   && Hide the Done text button.
	     @ PIXELS 160,200 CLEAR   && Hide mvar.
	     *Keep the GETs the same length.
	     x=15 - LEN(editanimal)
	     editanimal = editanimal + space(x)
	     @ PIXELS 120,200 GET editanimal VALID putitback(editanimal)
	     READ
	     RETURN
	
	     *Procedure to replace the element in the scrollable field
	     PROCEDURE putitback
	     PARAMETER manimal
	     STORE TRIM(LOWER(manimal)) TO farm_var(whichanimal)
	     STORE .F. TO flag1   && Do not go through PROCEDURE showit again.
	     STORE .T. TO flag2   && Set flag2 true to do updatescrn.
	     KEYBOARD CHR(23)     && Terminate READ.
	     RETURN .T.
	
	     *Procedure to the update the screen
	     PROCEDURE updatescrn
	     CLEAR
	     KEYBOARD CHR(9)     && TAB to next field.
	     STORE .F. TO flag2  && Do not go through PROCEDURE updatescrn again.
	     RETURN
	
	     *Procedure to stop the program with a RETURN
	     PROCEDURE dostopit
	     STORE 1 TO complete
	     DO stopit WITH complete
	
	     *Procedure to stop the program
	     PROCEDURE stopit
	     PARAMETER mcomplete
	     IF mcomplete=1
	        *Restore the environment.
	        ON KEY
	        CLEAR ALL
	        SCREEN 2 TOP OFF
	        SCREEN 1 DELETE
	        SCREEN 1 TOP
	        CANCEL
	     ENDIF
	     *End program.
	
	Additional query words: 2.01 scroll list
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbAudDeveloper kbFoxproSearch kbFoxBASE201Mac kbFoxBASESearch
	Version           : MACINTOSH:2.01
	
	=============================================================================
	

{% endraw %}
