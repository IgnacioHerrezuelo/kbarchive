---
layout: page
title: "Q129311: Visual FoxPro Has 3 New SYS Functions Related to Memory"
permalink: /kb/129/Q129311/
---

## Q129311: Visual FoxPro Has 3 New SYS Functions Related to Memory

{% raw %}

	Article: Q129311
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS: 3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There are three new SYS functions in Visual FoxPro related to memory.
	
	The new functions are:
	
	- SYS(3050), which sets buffer memory size.
	
	- SYS(3051), which sets lock retry interval.
	
	- SYS(3052), which overrides SET REPROCESS locking.
	
	MORE INFORMATION
	================
	
	SYS(3050) - Set Buffer Memory Size
	----------------------------------
	
	SYS(3050, nType, nBuffMemSize)
	
	- nType specifies foreground (1) or background (2)
	
	- nBuffMemSize specifies a suggested, maximum amount of buffer memory you want
	  Visual FoxPro to commit in foreground or background mode.
	
	The foreground memory buffer is the amount of memory available to Visual FoxPro
	when it is the currently active application. The background memory buffer is the
	amount of memory for use when Visual FoxPro is in the background with another
	application running in the foreground. Visual FoxPro never sets the target to
	more than the amount of physical RAM on the computer and never sets it to less
	than 256K bytes. Passing a zero for nBuffMemSize will cause Visual FoxPro to
	reset to its startup value, which is 262144 for both background and foreground.
	
	This function should be used in place of the MEMLIMIT command that was placed in
	the Config.fpw file in previous versions of FoxPro. The MEMLIMIT command is
	ignored in Visual FoxPro.
	
	To set the foreground or background buffer memory size to 6 and 4 million
	respectively, create a program and call it from the Config.fpw file. For
	example, add the following line to call Myprogram.prg from the Config.fpw file.
	Remember, only one Command= line is allowed in the Config.fpw file.
	
	     COMMAND = DO Myprogram.prg
	
	Create a program file called Myprogram.prg in the root folder of Visual FoxPro
	and type the following code:
	
	     =SYS(3050,1,6000000)
	     =SYS(3050,2,4000000)
	
	For these changes to take effect, restart Visual FoxPro. To check the validity of
	these settings, type the following in the Command window:
	
	     ? SYS(3050,1)
	     ? SYS(3050,2)
	
	SYS(3051) - Set Lock Retry Interval
	-----------------------------------
	
	SYS(3051, nWaitMilliseconds)
	
	- nWaitMilliseconds specifies the suggested interval of time for Visual FoxPro
	  to wait between retries while attempting to lock a record, file, memo, or
	  index. The valid range is from 100 to 1000 milliseconds. Passing a zero for
	  nWaitMilliseconds will cause Visual FoxPro to reset to its startup value
	  which is 333.
	
	SYS(3052) - Honor REPROCESS for Index or Memo Lock Attempts
	-----------------------------------------------------------
	
	SYS(3052, nFileType, lHonorReprocess)
	
	- nFileType specifies index (1) or memo (2).
	
	- lHonorReprocess, when equal to .T., specifies that Visual FoxPro should honor
	  the SET REPROCESS setting when Visual FoxPro attempts to lock files. When
	  lHonorReprocess is off (.F.), the locking behavior is to wait indefinitely
	  for locks on the specified files. Honoring SET REPROCESS is recommended if
	  your program is using transactions because reduces the risk of deadlocks.
	  Turning it on for indexes may adversely impact concurrency control because
	  index locks may be held for a longer period of time.
	
	Using SYS(1001) and SYS(1016)
	-----------------------------
	
	SYS(1001) returns the virtual memory pool size. SYS(1016) returns the amount of
	memory used by defined objects. However, in order to get accurate memory
	statistics, you should use Window API functions.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS: 3.0,5.0,6.0
	
	=============================================================================
	

{% endraw %}
